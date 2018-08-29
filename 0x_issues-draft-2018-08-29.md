# 0x exchange findings to date: 2018-08-29

The following is an excerpt from a Draft of ConsenSys' Diligence audit report of the 0x v2 protocol.

It includes all of our findings to date, but does not include discussion of proposed remediation changes to address some of these findings. 


## Issue Overview  

The following table contains all the issues discovered during the audit. The issues are ordered based on their severity. More detailed description on the  levels of severity can be found in Appendix 2. The table also contains the Github status of any discovered issue.

| Chapter | Issue Title  | Issue Status | Severity |
| ------------- | ------------- | ------------- | ------------- |
 | 3.1 | [A malicious maker can empty a taker’s account of all tokens.](#31-a-malicious-maker-can-empty-a-taker’s-account-of-all-tokens-) | open| critical | 
 | 3.2 | [MixinSignatureValidator: Insecure signature validator SignatureType.Caller](#32-mixinsignaturevalidator-insecure-signature-validator-signaturetype-caller) | open| critical | 
 | 3.3 | [AssetProxyOwner: timelocked transactions affected by changing wallet parameters](#33-assetproxyowner-timelocked-transactions-affected-by-changing-wallet-parameters) | open| medium | 
 | 3.4 | [AssetProxyOwner: removeAuthorizedAddressAtIndex requires multiple confirmations](#34-assetproxyowner-removeauthorizedaddressatindex-requires-multiple-confirmations) | open| medium | 
 | 3.5 | [LibBytes: Insufficient Testing](#35-libbytes-insufficient-testing) | open| medium | 
 | 3.6 | [LibBytes: readBytes4 does not adhere to spec](#36-libbytes-readbytes4-does-not-adhere-to-spec) | open| medium | 
 | 3.7 | [AssetProxyOwner: readBytes4 does not adhere to spec](#37-assetproxyowner-readbytes4-does-not-adhere-to-spec) | open| medium | 
 | 3.8 | [MixinAuthorizable: Insufficient Testing](#38-mixinauthorizable-insufficient-testing) | open| medium | 
 | 3.9 | [ERC721Proxy: Insufficient Testing](#39-erc721proxy-insufficient-testing) | open| medium | 
 | 3.10 | [ERC721Proxy: fallback function silently fails](#310-erc721proxy-fallback-function-silently-fails) | open| medium | 
 | 3.11 | [ERC20Proxy: fallback function silently fails](#311-erc20proxy-fallback-function-silently-fails) | open| medium | 
 | 3.12 | [ERC20Proxy: Insufficient testing](#312-erc20proxy-insufficient-testing) | open| medium | 
 | 3.13 | [ERC721Token: inaccurate isContract function](#313-erc721token-inaccurate-iscontract-function) | open| medium | 
 | 3.14 | [AssetProxyOwner duplicates code for readBytes4 function](#314-assetproxyowner-duplicates-code-for-readbytes4-function) | open| minor | 
 | 3.15 | [Outdated compiler version](#315-outdated-compiler-version) | open| minor | 
 | 3.16 | [Use of this.balance in WETH9.sol](#316-use-of-this-balance-in-weth9-sol) | open| minor | 
 | 3.17 | [ERC20Proxy: Reconsider use of inline assembly](#317-erc20proxy-reconsider-use-of-inline-assembly) | open| minor | 
 | 3.18 | [ERC20Proxy: Unclear comments](#318-erc20proxy-unclear-comments) | open| minor | 
 | 3.19 | [ERC20Proxy/ERC721Proxy: LibBytes imported but not used](#319-erc20proxyerc721proxy-libbytes-imported-but-not-used) | open| minor | 
 | 3.20 | [LibBytes is imported but never used](#320-libbytes-is-imported-but-never-used) | open| minor | 
 | 3.21 | [Optimization: refine function visibilities in the Exchange for gas efficiency](#321-optimization-refine-function-visibilities-in-the-exchange-for-gas-efficiency) | open| minor | 
 | 3.22 | [LibConstants: dynamic constructor initialisation](#322-libconstants-dynamic-constructor-initialisation) | open| minor | 




## 3 Issue Detail  


### 3.1 A malicious maker can empty a taker’s account of all tokens. 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| critical |  open | <>| The issue is currently under review |


#### Description

A malicious maker can empty a taker’s account of all tokens. The order does not need to involve a malicious token.

The attack uses reentry via `executeTransaction()`.  

 1. The attacker creates a maker order and signs it with `SignatureType.Wallet` signature type.
 2. The taker signs a transaction, to take that order.
 3. Some `sender` (or another account of the attacker) submits that transaction using `executeTransaction()`. This will write the taker’s address to `currentContextAddress`.
 4. The attacker’s wallet contract re-enters to `setSignatureValidatorApproval()`, and sets a contract which always returns `true`.
 5. The attacker can then submit any order for the victim with `SignatureType.Validator`.

The attack can be modified to execute any order filling function on the Exchange on behalf of the taker. 

Note that, despite the comment, this check doesn’t prevent calls to other functions in `Exchange.sol`.

[packages/contracts/src/2.0.0/protocol/Exchange/MixinTransactions.sol:L60](https://github.com/0xProject/0x-monorepo/blob/dilligence-audit-7-23/packages/contracts/src/2.0.0/protocol/Exchange/MixinTransactions.sol#L61)

```Solidity
    // Prevent reentrancy
    require(
        currentContextAddress == address(0),
        "REENTRANCY_ILLEGAL"
        );
```

#### Remediation

The developers have indicated plans for these mitigations, which we are evaluating: 

1. use `pragma experimental 0.5.0`. This change would make all of the `view` functions use static calls, which automatically limits this specific attack vector to malicious tokens
2. Add a mutex to all variations of `fillOrder`. This will add 10k gas to each fill, but this will be significantly reduced after EIP1087/1283

### 3.2 MixinSignatureValidator: Insecure signature validator SignatureType.Caller 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| critical |  open | <>| The issue is currently under review |


#### Description 

MixinSignatureValidator has a signature validator called `SignatureType.Caller` that allows an order to be valid if `order.makerAddress == msg.sender`. If the `SignatureType.Caller` is set, no actual signature verification is performed for the order. An attacker could attack contracts that have:

1. ERC20/ERC721 tokens.
2. approved the Exchange proxy contracts to make transfers on their behalf.
3. a function that allows users to make calls to the exchange trading functions. 

A contract that has the above listed properties is the Forwarder contract. It requires a ZRX token balance to function properly and it also approves the Exchange proxy contracts to make transfers on its behalf. An attacker can create an order to obtain ZRX (in exchange for, e.g., 1 wei), using SignatureType.Caller with the Forwarder contract as the maker. If such an order is used in a call to `Forwarder::marketSellOrderWithEthAsync`, the Forwarder address will be `msg.sender` when calling `fillOrder`, the signature will be seen as valid and the order will be filled. 

The following order is a POC for the attack (full details in [forwarder_malicious.ts.txt](https://github.com/0xProject/0x-monorepo/files/2322170/forwarder_malicious.ts.txt)). The Forwarder will process the order and trade with itself as it is both the taker and the maker. The Forwarder will end up with exactly the balance after the Exchange contract has settled the order and Forwarder will transfer the takerAmount to itself and makerAmount to the attacker. 

```Solidity
Order {
  makerAssetData: ZRX_ASSET_DATA 
  takerAssetData: WETH_ASSET_DATA
  makerAddress: address of Forwarder contract
  takerAddress: 0x0 
  makerAmount: as many ZRX tokens as the Forwarder contract owns
  takerAmount: 1 (WETH)
  ...
}
Signature: SignatureType.Caller
```

#### Remediation 

Removing `SignatureType.Caller` is the most important counter measure. Assuming that msg.sender has created the order because `order.makerAddress == msg.sender` is unsafe not just for the Forwarder but any contract that calls into the Exchange contract and that has a token balance. Proper signature recovery and validation needs to be performed by all variations of `SignatureType`. 

Forwarder should check every order that `order.makerAddress` is not the Forwarder address itself. 

Exchange check that the `order.makerAddress` id not `order.takerAddress` before processing an order.  

### 3.3 AssetProxyOwner: timelocked transactions affected by changing wallet parameters 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

Increasing the `required` parameter of AssetProxyOwner by invoking the `changeRequirement` function prevents the execution of a transaction that was previously fully confirmed and is currently under timelock. Even if the transaction eventually receives the additional confirmations needed for the new `required` value, its timelock will be reset by `confirmTransaction` and it will need to wait another 2 weeks to get executed.

Similarly, increasing the `secondsTimeLocked` parameter by invoking `changeTimeLock` increases the timelock of unexecuted, fully confirmed transactions that have been scheduled to be executable at the 2 week mark after their last confirmation.

Evaluate whether this is the intended behavior, and if so, document it so the wallet members understand the consequences of changing these parameters on unexecuted, fully confirmed transactions.

### 3.4 AssetProxyOwner: removeAuthorizedAddressAtIndex requires multiple confirmations 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <> | The issue is currently under review |


#### Description

AssetProxyOwner allows the `removeAuthorizedAddressAtIndex` function to be executed without being subject to the time lock. However, it is still subject to `required` number of confirmations, which may be too slow in the situation where a security bug is discovered. Consider adding an immediate, temporary pause functionality that requires fewer (or even a single) confirmation to remove an insecure authorized address.

### 3.5 LibBytes: Insufficient Testing 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

LibBytes is not thoroughly tested which is concerning especially due to its extensive use of inline assembly. Specifically, the following test cases are missing, among others not listed here:

1. `readBytes4` when index > 0 and b.length >= index + 4
2. `readBytes4` when index > 0 and b.length < index + 4





### 3.6 LibBytes: readBytes4 does not adhere to spec 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

The specification of the `readBytes4` function in LibBytes.sol is to "read an unpadded bytes4 value from a position in a byte array". However, the implementation ignores the `index` parameter and instead only ever returns the bytes4 at index 0, regardless of the value of the `index` parameter.

### 3.7 AssetProxyOwner: readBytes4 does not adhere to spec 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

The specification of the `readBytes4` function in AssetProxyOwner.sol is to "read an unpadded bytes4 value from a position in a byte array". However, the implementation ignores the `index` parameter and instead only ever returns the bytes4 at index 0, regardless of the value of the `index` parameter.

### 3.8 MixinAuthorizable: Insufficient Testing 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

The `authorizable.ts` file tests the MixinAuthorizable contract. The file uses the `address` variable as the parameter for the unit test cases of the contract functions. However, this `address` variable is always set to `owner` because of line 21. Thus the test file only covers scenarios where the owner is authorizing himself, and does not test the more common scenario where he is authorizing another, different address.

#### Remediation

Set the `address` variable to a fresh account, different from `owner`.

### 3.9 ERC721Proxy: Insufficient Testing 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

ERC721Proxy is not thoroughly tested which is concerning especially due to its extensive use of inline assembly. Specifically, the following test cases are missing, among others not listed here:

1. The `should throw if transferring 0 amount of a token` test case and the `should throw if transferring > 1 amount of a token` test case and the `should throw if allowances are too low` test case  do not check that the NFT ownership is unchanged.
2. Fallback function should revert if a function selector is used besides the one for "transferFrom(bytes,address,address,uint256)".
3. No test case for when assetData has extra data (beyond the minimum 68 bytes), which, according to the [specification](https://github.com/0xProject/0x-protocol-specification/blob/master/v2/v2-specification.md#erc721proxy), is possible: "The ERC721Proxy does not enforce strict length checks for assetData, which means that extra data may be appended to this field with any arbitrary encoding. Any extra data will be ignored by the ERC721Proxy but may be used in external contracts interacting with the Exchange contract. Relayers that do not desire this behavior should validate the length of all assetData fields contained in orders before acceptance."

### 3.10 ERC721Proxy: fallback function silently fails 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description 

The ERC721Proxy fallback does not revert if an incorrect function selector is used. Instead, it silently fails, which is inconsistent with the rest of the fallback's behavior which is to revert on error,  and also inconsistent with the IAssetProxy interface specification "Either succeeds or throws". 

Based on the spec, a client of IAssetProxy would assume that, because a (malformed) transaction sent to the IAssetProxy did not throw, that the token transfer succeeded (when it didn't) and may incorrectly notify the user that his order was fulfilled.

#### Remediation

If the sender calls a function besides "transferFrom(bytes,address,address,uint256)", the fallback function should revert.

### 3.11 ERC20Proxy: fallback function silently fails 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description 

The ERC20Proxy fallback does not revert if an incorrect function selector is used. Instead, it silently fails, which is inconsistent with the rest of the fallback's behavior which is to revert on error, and also inconsistent with the IAssetProxy interface specification "Either succeeds or throws".

Based on the spec, a client of IAssetProxy would assume that, because a (malformed) transaction sent to the IAssetProxy did not throw, that the token transfer succeeded (when it didn't) and may incorrectly notify the user that his order was fulfilled.

#### Remediation

If the sender calls a function besides "transferFrom(bytes,address,address,uint256)", the fallback function should revert.


### 3.12 ERC20Proxy: Insufficient testing 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description

ERC20Proxy is not thoroughly tested which is concerning especially due to its extensive use of inline assembly. Specifically, the following test cases are missing, among others not listed here:

1. The `should throw if requesting address is not authorized` test case and the `should throw if allowances are too low` test case  do not check that the balances are unchanged.
2. The `should successfully transfer tokens` test case and the `should do nothing if transferring 0 amount of a token` test case does not check that all addresses (besides maker and taker) have not changed.
3. The only token implementation tested is `DummyERC20Token` whose `transferFrom` method returns false on failure. The tests need to use other token implementations such as ones that revert on failure or ones that have the missing return type issue described in https://medium.com/coinmonks/missing-return-value-bug-at-least-130-tokens-affected-d67bf08521ca.
4. No test case for "unlimited allowance".
5. No test case for when `iszero(returndatasize)` is true after the `token.transferFrom` call.
6. No test case for when `eq(returndatasize, 32)` is false after the `token.transferFrom` call.
7. Fallback function should revert if a function selector is used besides the one for "transferFrom(bytes,address,address,uint256)".
8. No test case for when assetData has extra data (beyond the minimum 36 bytes), which, according to the [specification](https://github.com/0xProject/0x-protocol-specification/blob/master/v2/v2-specification.md#erc20proxy), is possible: "The ERC20Proxy does not enforce strict length checks for assetData, which means that extra data may be appended to this field with any arbitrary encoding. Any extra data will be ignored by the ERC20Proxy but may be used in external contracts interacting with the Exchange contract. Relayers that do not desire this behavior should validate the length of all assetData fields contained in orders before acceptance."

### 3.13 ERC721Token: inaccurate isContract function 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| medium |  open | <>| The issue is currently under review |


#### Description 
The function `isContract` verifies if a calling address is a contract or a human actor. The current implementation if used as a security control could be compromised by a contract that calls the `checkAndCallSafeTransfer` from the constructor at initialisation. 



[packages/contracts/src/2.0.0/tokens/ERC721Token/ERC721Token.sol:L376-L406](https://github.com/0xProject/0x-monorepo/blob/a05b14e4d9659be1cc495ee33fd8962ce773f87f/packages/contracts/src/2.0.0/tokens/ERC721Token/ERC721Token.sol#L377-L407)

```Solidity
    function checkAndCallSafeTransfer(
        address _from,
        address _to,
        uint256 _tokenId,
        bytes _data)
        internal
        returns (bool)
    {
        if (!isContract(_to)) {
            return true;
        }
        bytes4 retval = IERC721Receiver(_to).onERC721Received(_from, _tokenId, _data);
        return (retval == ERC721_RECEIVED);
    }

    function isContract(address addr)
        internal
        view
        returns (bool)
    {
        uint256 size;
        // XXX Currently there is no better way to check if there is a contract in an address
        // than to check the size of the code at that address.
        // See https://ethereum.stackexchange.com/a/14016/36603
        // for more details about how this works.
        // TODO Check this again before the Serenity release, because all addresses will be
        // contracts then.
        assembly { size := extcodesize(addr) }  // solium-disable-line security/no-inline-assembly
        return size > 0;
    }
}
```



#### Remediation 

### 3.14 AssetProxyOwner duplicates code for readBytes4 function 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description

The AssetProxyOwner contract has a `readBytes4` function implementation which already exists in LibBytes. Avoid unnecessary code duplication to minimize errors.

#### Remediation

Remove the `readBytes4` function from AssetProxyOwner and instead import LibBytes.


### 3.15 Outdated compiler version 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description 

Using an outdated compiler version can be problematic especially if there are publicly disclosed bugs and issues (see also https://github.com/ethereum/solidity/releases) that affect the current compiler version. 



[packages/contracts/src/2.0.0/protocol/AssetProxyOwner/AssetProxyOwner.sol:L18](https://github.com/0xProject/0x-monorepo/blob/a05b14e4d9659be1cc495ee33fd8962ce773f87f/packages/contracts/src/2.0.0/protocol/AssetProxyOwner/AssetProxyOwner.sol#L19)

```Solidity
pragma solidity 0.4.10;
```



#### Remediation 

It is recommended to use at least version 0.4.23 of the Solidity compiler.

### 3.16 Use of this.balance in WETH9.sol 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description

The WETH9 contract, which is used as the system's EtherToken uses the contract's ether balance to track the totalSupply of the token. 



[packages/contracts/src/2.0.0/tokens/EtherToken/WETH9.sol:L46](https://github.com/0xProject/0x-monorepo/blob/a05b14e4d9659be1cc495ee33fd8962ce773f87f/packages/contracts/src/2.0.0/tokens/EtherToken/WETH9.sol#L47L49)

```Solidity
   function totalSupply() public view returns (uint) {
        return this.balance;
    }
```

#### Remediation

This saves gas by not having to track a `totalSupply` storage value with each deposit and withdrawal. However this `totalSupply` value need not be equal to the sum of all account balances in the contract. This may lead to unforeseen issues with other contracts calling on the `totalSupply()` function. We leave it to the developer to consider if this is an acceptable trade off. 

### 3.17 ERC20Proxy: Reconsider use of inline assembly 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description

The ERC20Proxy fallback function is written entirely in inline assembly. The rationale given was to optimize gas costs caused by unnecessary ABI encoding/decoding. In general, inline assembly is concerning from a security perspective because it bypasses compiler checks and inhibits human code reasoning.

#### Remediation 

Consider minimizing the amount of inline assembly used. For example, the function selector check and the `authorized` map check on lines 37-61 likely do not need to be written in assembly from a gas savings standpoint.

### 3.18 ERC20Proxy: Unclear comments 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description 

The following comment in ERC20Proxy is confusing to follow and can be written more clearly. For example, what does "It" refer to and what does "Params" refer to?
```Solidity
            // The token address is found as follows:
            // * It is stored at offset 4 in `assetData` contents.
            // * This is stored at offset 32 from `assetData`.
            // * The offset to `assetData` from Params is stored at offset
            //   4 in calldata.
            // * The offset of Params in calldata is 4.
            // So we read location 4 and add 32 + 4 + 4 to it.
```

### 3.19 ERC20Proxy/ERC721Proxy: LibBytes imported but not used 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description 

LibBytes is imported by ERC20Proxy.sol but never used.

#### Remediation

Remove the import.

### 3.20 LibBytes is imported but never used 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description

This line appears to be unnecessary. The contract compiles without it, and I cannot see where it would be used. 



[packages/contracts/src/2.0.0/protocol/Exchange/MixinAssetProxyDispatcher.sol:L30](https://github.com/0xProject/0x-monorepo/blob/a05b14e4d9659be1cc495ee33fd8962ce773f87f/packages/contracts/src/2.0.0/protocol/Exchange/MixinAssetProxyDispatcher.sol#L31)

```Solidity
    using LibBytes for bytes;
```



#### Remediation

Remove it. 

### 3.21 Optimization: refine function visibilities in the Exchange for gas efficiency 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description

The `fillOrder()` function is labelled `public` because it is intended to be called either by external accounts, or from other 'wrapper' functions such as `fillOrKillOrder()`, and `batchFillOrders()`.

Relative to `external` and `internal` functions, the `public` keyword is gas inefficient, because it can be run either by a `JUMP` from a function within the same contract or by a `CALL` from another contract. If called by a `JUMP` the arguments will be passed in memory. If called by a `CALL`, the arguments are in the call data. 

Functions labelled `public` require extra code to handle both cases. 

#### Remediation

Given the sensitivity to gas costs in this system, it would be more efficient to move the code of `fillOrder()` to an internal function (ie. `internalFillOrder()` which is called by the wrapper functions as well as `fillOrder()`.

Additionally, it would be more efficient to change visibility of wrapper functions from `public` to `external`, unfortunately there is a [compiler issue](https://github.com/ethereum/solidity/issues/3293) preventing this with the v2 encoder.

I have confirmed small gas savings in principle with very simple code samples, but have not yet tested in the Exchange itself. Given the number and size of arguments required to complete an order I expect they would be non-trivial.

### 3.22 LibConstants: dynamic constructor initialisation 

| Severity  | Status | Link | Remediation Comment |
| ------------- | ------------- | ------------- | ------------- |
| minor |  open | <>| The issue is currently under review |


#### Description 
According to the specs the dynamic constructor should be removed before deploying the contracts to the mainnet. Manually removing the code is not a good coding practice, it is recommended to build in a fail safe to ensure the code changes will not be missed. 



[packages/contracts/src/2.0.0/protocol/Exchange/libs/LibConstants.sol:L41-L49](https://github.com/0xProject/0x-monorepo/blob/a05b14e4d9659be1cc495ee33fd8962ce773f87f/packages/contracts/src/2.0.0/protocol/Exchange/libs/LibConstants.sol#L42-L50)

```Solidity
    // @TODO: Remove when we deploy.
    constructor (bytes memory zrxAssetData)
        public
    {
        ZRX_ASSET_DATA = zrxAssetData;
    }
}
// solhint-enable max-line-length
```



#### Remediation 
Build in a fail safe that throws if the contracts are deployed on the mainnet without changing them beforehand. This could be achieved by checking the `block.number` to identify on which network the contracts are deployed. The mainnet is ahead of all the test networks and the following code could be used to prevent a successful launch on the mainnet without the code changes. 

```Solidity 
require(block.number <  6019600)
````




## Appendix 2 - Severity 


### A.2.1 - Minor

Minor issues are generally subjective in nature, or potentially deal with topics like "best practices" or "readability".  Minor issues in general will not indicate an actual problem or bug in code.

The maintainers should use their own judgment as to whether addressing these issues improves the codebase.

### A.2.2 - Medium

Medium issues are generally objective in nature but do not represent actual bugs or security problems.

These issues should be addressed unless there is a clear reason not to.

### A.2.3 - Major

Major issues will be things like bugs or security vulnerabilities.  These issues may not be directly exploitable, or may require a certain condition to arise in order to be exploited.

Left unaddressed these issues are highly likely to cause problems with the operation of the contract or lead to a situation which allows the system to be exploited in some way.

### A.2.4 - Critical

Critical issues are directly exploitable bugs or security vulnerabilities.

Left unaddressed these issues are highly likely or guaranteed to cause major problems or potentially a full failure in the operations of the contract.

## Appendix 3 - Disclosure

ConsenSys Diligence (“CD”) typically receives compensation from one or more clients (the “Clients”) for performing the analysis contained in these reports (the “Reports”). The Reports may be distributed through other means, including via ConsenSys publications and other distributions.

The Reports are not an endorsement or indictment of any particular project or team, and the Reports do not guarantee the security of any particular project. This Report does not consider, and should not be interpreted as considering or having any bearing on, the potential economics of a token, token sale or any other product, service or other asset. Cryptographic tokens are emergent technologies and carry with them high levels of technical risk and uncertainty. No Report provides any warranty or representation to any Third-Party in any respect, including regarding the bugfree nature of code, the business model or proprietors of any such business model, and the legal compliance of any such business. No third party should rely on the Reports in any way, including for the purpose of making any decisions to buy or sell any token, product, service or other asset. Specifically, for the avoidance of doubt, this Report does not constitute investment advice, is not intended to be relied upon as investment advice, is not an endorsement of this project or team, and it is not a guarantee as to the absolute security of the project. CD owes no duty to any Third-Party by virtue of publishing these Reports.

PURPOSE OF REPORTS The Reports and the analysis described therein are created solely for Clients and published with their consent. The scope of our review is limited to a review of Solidity code and only the Solidity code we note as being within the scope of our review within this report. The Solidity language itself remains under development and is subject to unknown risks and flaws. The review does not extend to the compiler layer, or any other areas beyond Solidity that could present security risks. Cryptographic tokens are emergent technologies and carry with them high levels of technical risk and uncertainty.

CD makes the Reports available to parties other than the Clients (i.e., “third parties”) -- on its Github account (https://github.com/ConsenSys). CD hopes that by making these analyses publicly available, it can help the blockchain ecosystem develop technical best practices in this rapidly evolving area of innovation.

LINKS TO OTHER WEB SITES FROM THIS WEB SITE You may, through hypertext or other computer links, gain access to web sites operated by persons other than ConsenSys and CD. Such hyperlinks are provided for your reference and convenience only, and are the exclusive responsibility of such web sites' owners. You agree that ConsenSys and CD are not responsible for the content or operation of such Web sites, and that ConsenSys and CD shall have no liability to you or any other person or entity for the use of third party Web sites. Except as described below, a hyperlink from this web Site to another web site does not imply or mean that ConsenSys and CD endorses the content on that Web site or the operator or operations of that site. You are solely responsible for determining the extent to which you may use any content at any other web sites to which you link from the Reports. ConsenSys and CD assumes no responsibility for the use of third party software on the Web Site and shall have no liability whatsoever to any person or entity for the accuracy or completeness of any outcome generated by such software.

TIMELINESS OF CONTENT The content contained in the Reports is current as of the date appearing on the Report and is subject to change without notice. Unless indicated otherwise, by ConsenSys and CD. 


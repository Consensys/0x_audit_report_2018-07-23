``
SUB-ROOT DIRECTORY
├── examples
│   ├── ExchangeWrapper
│   │   └── ExchangeWrapper.sol [The analysis was completed successfully. No issues were detected.]
│   ├── Validator
│   │   └── Validator.sol [The analysis was completed successfully. No issues were detected.]
│   ├── Wallet
│   │   └── Wallet.sol [The analysis was completed successfully. No issues were detected.]
│   └── Whitelist
│       └── Whitelist.sol [The analysis was completed successfully. No issues were detected.]
├── forwarder
│   ├── Forwarder.sol [The analysis was completed successfully. No issues were detected.]
│   ├── interfaces
│   │   ├── IAssets.sol [Input files do not contain any valid contracts.]
│   │   ├── IForwarderCore.sol [Input files do not contain any valid contracts.]
│   │   └── IForwarder.sol [Input files do not contain any valid contracts.]
│   ├── libs
│   │   ├── LibConstants.sol [The analysis was completed successfully. No issues were detected.]
│   │   └── LibForwarderErrors.sol [The analysis was completed successfully. No issues were detected.]
│   ├── MixinAssets.sol [Input files do not contain any valid contracts.]
│   ├── MixinExchangeWrapper.sol [Input files do not contain any valid contracts.]
│   ├── MixinForwarderCore.sol [Input files do not contain any valid contracts.]
│   ├── mixins
│   │   ├── MAssets.sol [Input files do not contain any valid contracts.]
│   │   ├── MExchangeWrapper.sol [Input files do not contain any valid contracts.]
│   │   ├── MForwarderCore.sol [Input files do not contain any valid contracts.]
│   │   └── MWeth.sol [Input files do not contain any valid contracts.]
│   └── MixinWeth.sol [Input files do not contain any valid contracts.]
├── multisig
│   ├── MultiSigWallet.sol [15]
│   └── MultiSigWalletWithTimeLock.sol [16]
├── protocol
│   ├── AssetProxy
│   │   ├── ERC20Proxy.sol [14]
│   │   ├── ERC721Proxy.sol [13]
│   │   ├── interfaces
│   │   │   ├── IAssetData.sol [Input files do not contain any valid contracts.]
│   │   │   ├── IAssetProxy.sol [Input files do not contain any valid contracts.]
│   │   │   └── IAuthorizable.sol [Input files do not contain any valid contracts.]
│   │   ├── libs
│   │   │   └── LibAssetProxyErrors.sol [The analysis was completed successfully. No issues were detected.]
│   │   ├── MixinAuthorizable.sol [12]
│   │   └── mixins
│   │       └── MAuthorizable.sol [Input files do not contain any valid contracts.]
│   ├── AssetProxyOwner
│   │   └── AssetProxyOwner.sol [11]
│   └── Exchange
│       ├── Exchange.sol [The analysis was completed successfully. No issues were detected.]
│       ├── interfaces
│       │   ├── IAssetProxyDispatcher.sol [Input files do not contain any valid contracts.]
│       │   ├── IExchangeCore.sol [Input files do not contain any valid contracts.]
│       │   ├── IExchange.sol [Input files do not contain any valid contracts.]
│       │   ├── IMatchOrders.sol [Input files do not contain any valid contracts.]
│       │   ├── ISignatureValidator.sol [Input files do not contain any valid contracts.]
│       │   ├── ITransactions.sol [Input files do not contain any valid contracts.]
│       │   ├── IValidator.sol [Input files do not contain any valid contracts.]
│       │   ├── IWallet.sol [Input files do not contain any valid contracts.]
│       │   └── IWrapperFunctions.sol [Input files do not contain any valid contracts.]
│       ├── libs
│       │   ├── LibAbiEncoder.sol [The analysis was completed successfully. No issues were detected.]
│       │   ├── LibConstants.sol [The analysis was completed successfully. No issues were detected.]
│       │   ├── LibEIP712.sol [The analysis was completed successfully. No issues were detected.]
│       │   ├── LibExchangeErrors.sol [The analysis was completed successfully. No issues were detected.]
│       │   ├── LibFillResults.sol [The analysis was completed successfully. No issues were detected.]
│       │   ├── LibMath.sol [The analysis was completed successfully. No issues were detected.]
│       │   └── LibOrder.sol [The analysis was completed successfully. No issues were detected.]
│       ├── MixinAssetProxyDispatcher.sol [10]
│       ├── MixinExchangeCore.sol [Input files do not contain any valid contracts.]
│       ├── MixinMatchOrders.sol [Input files do not contain any valid contracts.]
│       ├── mixins
│       │   ├── MAssetProxyDispatcher.sol [Input files do not contain any valid contracts.]
│       │   ├── MExchangeCore.sol [Input files do not contain any valid contracts.]
│       │   ├── MMatchOrders.sol [Input files do not contain any valid contracts.]
│       │   ├── MSignatureValidator.sol [Input files do not contain any valid contracts.]
│       │   └── MTransactions.sol [Input files do not contain any valid contracts.]
│       ├── MixinSignatureValidator.sol [Input files do not contain any valid contracts]
│       ├── MixinTransactions.sol [Input files do not contain any valid contracts.]
│       └── MixinWrapperFunctions.sol [Input files do not contain any valid contracts.]
├── test
│   ├── DummyERC20Token
│   │   └── DummyERC20Token.sol [The analysis was completed successfully. No issues were detected.]
│   ├── DummyERC721Receiver
│   │   └── DummyERC721Receiver.sol [The analysis was completed successfully. No issues were detected.]
│   ├── DummyERC721Token
│   │   └── DummyERC721Token.sol [The analysis was completed successfully. No issues were detected.]
│   ├── Mintable
│   │   └── Mintable.sol [The analysis was completed successfully. No issues were detected.]
│   ├── TestAssetProxyDispatcher
│   │   └── TestAssetProxyDispatcher.sol [8]
│   ├── TestAssetProxyOwner
│   │   └── TestAssetProxyOwner.sol [9]
│   ├── TestConstants
│   │   └── TestConstants.sol [The analysis was completed successfully. No issues were detected.]
│   ├── TestLibBytes
│   │   └── TestLibBytes.sol [7]
│   ├── TestLibs
│   │   └── TestLibs.sol [The analysis was completed successfully. No issues were detected.]
│   └── TestSignatureValidator
│       └── TestSignatureValidator.sol [6]
├── tokens
│   ├── ERC20Token
│   │   ├── ERC20Token.sol [The analysis was completed successfully. No issues were detected.]
│   │   └── IERC20Token.sol [input files do not contain any valid contracts]
│   ├── ERC721Token
│   │   ├── ERC721Token.sol [5]
│   │   ├── IERC721Receiver.sol [input files do not contain any valid contracts]
│   │   └── IERC721Token.sol [input files do not contain any valid contracts]
│   ├── EtherToken
│   │   ├── IEtherToken.sol [3]
│   │   └── WETH9.sol [4]
│   ├── UnlimitedAllowanceToken
│   │   └── UnlimitedAllowanceToken.sol [2]
│   └── ZRXToken
│       └── ZRXToken.sol [1]
└── utils
    ├── LibBytes
    │   └── LibBytes.sol [The analysis was completed successfully. No issues were detected.]
    ├── Ownable
    │   ├── IOwnable.sol [input files do not contain any valid contracts]
    │   ├── Ownable.sol [The analysis was completed successfully. No issues were detected.]
    └── SafeMath
        └── SafeMath.sol [The analysis was completed successfully. No issues were detected.]
```

# Footnotes
## [1] 
```
$myth -x ZRXToken.sol 
Solc experienced a fatal error (code 1).

ZRXToken.sol:22:1: Error: Source "1.0.0/UnlimitedAllowanceToken/UnlimitedAllowanceToken_v1.sol" not found: File not found.
import { UnlimitedAllowanceToken_v1 as UnlimitedAllowanceToken } from "../../../1.0.0/UnlimitedAllowanceToken/UnlimitedAllowanceToken_v1.sol";
^-----------------------------------------------------------------------------------------------------------------------------^
```
File **does** exist in the specified local path. Error occurs on multiple Ubuntu machines.

---
## [2]
```
$ myth -x UnlimitedAllowanceToken.sol 
Solc experienced a fatal error (code 1).

UnlimitedAllowanceToken.sol:21:1: Error: Source "ERC20Token/ERC20Token.sol" not found: File not found.
import "../ERC20Token/ERC20Token.sol";
^------------------------------------^
```
File **does** exist in the specified local path. Error occurs on multiple Ubuntu machines.

---
## [3]
```
$ myth -x IEtherToken.sol 
Solc experienced a fatal error (code 1).

IEtherToken.sol:21:1: Error: Source "ERC20Token/IERC20Token.sol" not found: File not found.
import "../ERC20Token/IERC20Token.sol";
^-------------------------------------^
```
File **does** exist in the specified local path. Error occurs on multiple Ubuntu machines.

---
## [4]
```
$ myth -x WETH9.sol 
==== Integer Overflow ====
Type: Warning
Contract: WETH9
Function name: deposit()
PC address: 1231
A possible integer overflow exists in the function `deposit()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: WETH9.sol:37

balanceOf[msg.sender] += msg.value

--------------------

==== Integer Underflow ====
Type: Warning
Contract: WETH9
Function name: transferFrom(address,address,uint256)
PC address: 2398
A possible integer underflow exists in the function `transferFrom(address,address,uint256)`.
The subtraction may result in a value < 0.
--------------------
In file: WETH9.sol:72

balanceOf[src] -= wad

--------------------

==== Integer Overflow ====
Type: Warning
Contract: WETH9
Function name: transferFrom(address,address,uint256)
PC address: 2475
A possible integer overflow exists in the function `transferFrom(address,address,uint256)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: WETH9.sol:73

balanceOf[dst] += wad

--------------------
```

---
## [5]
```
Solc experienced a fatal error (code 1).

ERC721Token.sol:30:1: Error: Source "utils/SafeMath/SafeMath.sol" not found: File not found.
import "../../utils/SafeMath/SafeMath.sol";
^-----------------------------------------^
```
---

## [6]
```
myth TestSignatureValidator.sol  -x
Solc experienced a fatal error (code 1).

TestSignatureValidator.sol:21:1: Error: Source "protocol/Exchange/MixinSignatureValidator.sol" not found: File not found.
import "../../protocol/Exchange/MixinSignatureValidator.sol";
^-----------------------------------------------------------^
TestSignatureValidator.sol:22:1: Error: Source "protocol/Exchange/MixinTransactions.sol" not found: File not found.
import "../../protocol/Exchange/MixinTransactions.sol";
^-----------------------------------------------------^

```
---
## [7]
```
==== Integer Overflow ====
Type: Warning
Contract: TestLibBytes
Function name: publicDeepCopyBytes(bytes,bytes)
PC address: 5441
A possible integer overflow exists in the function `publicDeepCopyBytes(bytes,bytes)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: utils/LibBytes/LibBytes.sol:106

add(source, length)

--------------------

==== Integer Overflow ====
Type: Warning
Contract: TestLibBytes
Function name: publicDeepCopyBytes(bytes,bytes)
PC address: 5499
A possible integer overflow exists in the function `publicDeepCopyBytes(bytes,bytes)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: utils/LibBytes/LibBytes.sol:134

add(dest, length)

--------------------
```

---
## [8]
```
$ myth -x test/TestAssetProxyDispatcher/TestAssetProxyDispatcher.sol 
==== Message call to external contract ====
Type: Warning
Contract: TestAssetProxyDispatcher
Function name: _function_0xc585bb93
PC address: 1341
This contract executes a message call to an address provided as a function argument. Generally, it is not recommended to call user-supplied addresses using Solidity's call() construct. Note that attackers might leverage reentrancy attacks to exploit race conditions or manipulate this contract's state.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:46

assetProxyContract.getProxyId()

--------------------

==== State change after external call ====
Type: Warning
Contract: TestAssetProxyDispatcher
Function name: _function_0xc585bb93
PC address: 1822
The contract account state is changed after an external call. Consider that the called contract could re-enter the function before this state change takes place. This can lead to business logic vulnerabilities.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:54

assetProxies[assetProxyId] = assetProxyContract

--------------------

==== Integer Overflow ====
Type: Warning
Contract: TestAssetProxyDispatcher
Function name: publicDispatchTransferFrom(bytes,address,address,uint256)
PC address: 2787
A possible integer overflow exists in the function `publicDispatchTransferFrom(bytes,address,address,uint256)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:131

add(mload(assetData), 63)

--------------------

==== Integer Overflow ====
Type: Warning
Contract: TestAssetProxyDispatcher
Function name: publicDispatchTransferFrom(bytes,address,address,uint256)
PC address: 2794
A possible integer overflow exists in the function `publicDispatchTransferFrom(bytes,address,address,uint256)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:133

add(cdStart, add(132, dataAreaLength))

--------------------

==== Integer Overflow ====
Type: Warning
Contract: TestAssetProxyDispatcher
Function name: publicDispatchTransferFrom(bytes,address,address,uint256)
PC address: 2902
A possible integer overflow exists in the function `publicDispatchTransferFrom(bytes,address,address,uint256)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:153

add(cdStart, 132)

--------------------

==== Message call to external contract ====
Type: Warning
Contract: TestAssetProxyDispatcher
Function name: publicDispatchTransferFrom(bytes,address,address,uint256)
PC address: 2945
This contract executes a message call to an address provided as a function argument. Generally, it is not recommended to call user-supplied addresses using Solidity's call() construct. Note that attackers might leverage reentrancy attacks to exploit race conditions or manipulate this contract's state.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:162

call(
                    gas,                    // forward all gas
                    assetProxy,             // call address of asset proxy
                    0,                      // don't send any ETH
                    cdStart,                // pointer to start of input
                    sub(cdEnd, cdStart),    // length of input  
                    cdStart,                // write output over input
                    512                     // reserve 512 bytes for output
                )

--------------------
```
---
## [9]
```
Solc experienced a fatal error (code 1).

multisig/MultiSigWallet.sol:37:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:43:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:49:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:55:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:61:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:67:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:73:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:79:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:88:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:106:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function MultiSigWallet(address[] _owners, uint _required)
    ^ (Relevant source part starts here and spans across multiple lines).
multisig/MultiSigWallet.sol:112:17: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
                throw;
                ^---^
multisig/MultiSigWalletWithTimeLock.sol:59:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function MultiSigWalletWithTimeLock(address[] _owners, uint _required, uint _secondsTimeLocked)
    ^ (Relevant source part starts here and spans across multiple lines).
protocol/AssetProxyOwner/AssetProxyOwner.sol:19:1: Error: Source file requires different compiler version (current compiler is 0.4.24+commit.e67f0147.Linux.g++ - note that nightly builds are considered to be strictly less than the released version
pragma solidity 0.4.10;
^---------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:51:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function AssetProxyOwner(
    ^ (Relevant source part starts here and spans across multiple lines).
test/TestAssetProxyOwner/TestAssetProxyOwner.sol:19:1: Error: Source file requires different compiler version (current compiler is 0.4.24+commit.e67f0147.Linux.g++ - note that nightly builds are considered to be strictly less than the released version
pragma solidity 0.4.10;
^---------------------^
test/TestAssetProxyOwner/TestAssetProxyOwner.sol:29:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function TestAssetProxyOwner(
    ^ (Relevant source part starts here and spans across multiple lines).
multisig/MultiSigWallet.sol:228:13: Warning: This declaration shadows a builtin symbol.
            Transaction tx = transactions[transactionId];
            ^------------^
multisig/MultiSigWalletWithTimeLock.sol:113:9: Warning: This declaration shadows a builtin symbol.
        Transaction storage tx = transactions[transactionId];
        ^--------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:39:9: Warning: This declaration shadows a builtin symbol.
        Transaction storage tx = transactions[transactionId];
        ^--------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:88:9: Warning: This declaration shadows a builtin symbol.
        Transaction storage tx = transactions[transactionId];
        ^--------------------^
multisig/MultiSigWallet.sol:228:13: Warning: Variable is declared as a storage pointer. Use an explicit "storage" keyword to silence this warning.
            Transaction tx = transactions[transactionId];
            ^------------^
multisig/MultiSigWallet.sol:97:13: Warning: Invoking events without "emit" prefix is deprecated.
            Deposit(msg.sender, msg.value);
            ^----------------------------^
multisig/MultiSigWallet.sol:130:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerAddition(owner);
        ^------------------^
multisig/MultiSigWallet.sol:149:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerRemoval(owner);
        ^-----------------^
multisig/MultiSigWallet.sol:168:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerRemoval(owner);
        ^-----------------^
multisig/MultiSigWallet.sol:169:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerAddition(newOwner);
        ^---------------------^
multisig/MultiSigWallet.sol:180:9: Warning: Invoking events without "emit" prefix is deprecated.
        RequirementChange(_required);
        ^--------------------------^
multisig/MultiSigWallet.sol:205:9: Warning: Invoking events without "emit" prefix is deprecated.
        Confirmation(msg.sender, transactionId);
        ^-------------------------------------^
multisig/MultiSigWallet.sol:218:9: Warning: Invoking events without "emit" prefix is deprecated.
        Revocation(msg.sender, transactionId);
        ^-----------------------------------^
multisig/MultiSigWallet.sol:231:17: Warning: Invoking events without "emit" prefix is deprecated.
                Execution(transactionId);
                ^----------------------^
multisig/MultiSigWallet.sol:233:17: Warning: Invoking events without "emit" prefix is deprecated.
                ExecutionFailure(transactionId);
                ^-----------------------------^
multisig/MultiSigWallet.sol:277:9: Warning: Invoking events without "emit" prefix is deprecated.
        Submission(transactionId);
        ^-----------------------^
multisig/MultiSigWalletWithTimeLock.sol:73:9: Warning: Invoking events without "emit" prefix is deprecated.
        TimeLockChange(_secondsTimeLocked);
        ^--------------------------------^
multisig/MultiSigWalletWithTimeLock.sol:86:9: Warning: Invoking events without "emit" prefix is deprecated.
        Confirmation(msg.sender, transactionId);
        ^-------------------------------------^
multisig/MultiSigWalletWithTimeLock.sol:102:9: Warning: Invoking events without "emit" prefix is deprecated.
        Revocation(msg.sender, transactionId);
        ^-----------------------------------^
multisig/MultiSigWalletWithTimeLock.sol:116:13: Warning: Invoking events without "emit" prefix is deprecated.
            Execution(transactionId);
            ^----------------------^
multisig/MultiSigWalletWithTimeLock.sol:118:13: Warning: Invoking events without "emit" prefix is deprecated.
            ExecutionFailure(transactionId);
            ^-----------------------------^
multisig/MultiSigWalletWithTimeLock.sol:132:9: Warning: Invoking events without "emit" prefix is deprecated.
        ConfirmationTimeSet(transactionId, confirmationTime);
        ^--------------------------------------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:77:9: Warning: Invoking events without "emit" prefix is deprecated.
        AssetProxyRegistration(assetProxyContract, isRegistered);
        ^------------------------------------------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:92:13: Warning: Invoking events without "emit" prefix is deprecated.
            Execution(transactionId);
            ^----------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:94:13: Warning: Invoking events without "emit" prefix is deprecated.
            ExecutionFailure(transactionId);
            ^-----------------------------^
```
---

## [10]
```
==== Message call to external contract ====
Type: Warning
Contract: MixinAssetProxyDispatcher
Function name: registerAssetProxy(address)
PC address: 1133
This contract executes a message call to an address provided as a function argument. Generally, it is not recommended to call user-supplied addresses using Solidity's call() construct. Note that attackers might leverage reentrancy attacks to exploit race conditions or manipulate this contract's state.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:46

assetProxyContract.getProxyId()

--------------------

==== State change after external call ====
Type: Warning
Contract: MixinAssetProxyDispatcher
Function name: registerAssetProxy(address)
PC address: 1614
The contract account state is changed after an external call. Consider that the called contract could re-enter the function before this state change takes place. This can lead to business logic vulnerabilities.
--------------------
In file: protocol/Exchange/MixinAssetProxyDispatcher.sol:54

assetProxies[assetProxyId] = assetProxyContract

--------------------
```
---
## [11]

```
Solc experienced a fatal error (code 1).

multisig/MultiSigWallet.sol:37:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:43:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:49:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:55:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:61:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:67:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:73:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:79:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:88:13: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
            throw;
            ^---^
multisig/MultiSigWallet.sol:106:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function MultiSigWallet(address[] _owners, uint _required)
    ^ (Relevant source part starts here and spans across multiple lines).
multisig/MultiSigWallet.sol:112:17: Warning: "throw" is deprecated in favour of "revert()", "require()" and "assert()".
                throw;
                ^---^
multisig/MultiSigWalletWithTimeLock.sol:59:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function MultiSigWalletWithTimeLock(address[] _owners, uint _required, uint _secondsTimeLocked)
    ^ (Relevant source part starts here and spans across multiple lines).
protocol/AssetProxyOwner/AssetProxyOwner.sol:19:1: Error: Source file requires different compiler version (current compiler is 0.4.24+commit.e67f0147.Linux.g++ - note that nightly builds are considered to be strictly less than the released version
pragma solidity 0.4.10;
^---------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:51:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function AssetProxyOwner(
    ^ (Relevant source part starts here and spans across multiple lines).
multisig/MultiSigWallet.sol:228:13: Warning: This declaration shadows a builtin symbol.
            Transaction tx = transactions[transactionId];
            ^------------^
multisig/MultiSigWalletWithTimeLock.sol:113:9: Warning: This declaration shadows a builtin symbol.
        Transaction storage tx = transactions[transactionId];
        ^--------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:39:9: Warning: This declaration shadows a builtin symbol.
        Transaction storage tx = transactions[transactionId];
        ^--------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:88:9: Warning: This declaration shadows a builtin symbol.
        Transaction storage tx = transactions[transactionId];
        ^--------------------^
multisig/MultiSigWallet.sol:228:13: Warning: Variable is declared as a storage pointer. Use an explicit "storage" keyword to silence this warning.
            Transaction tx = transactions[transactionId];
            ^------------^
multisig/MultiSigWallet.sol:97:13: Warning: Invoking events without "emit" prefix is deprecated.
            Deposit(msg.sender, msg.value);
            ^----------------------------^
multisig/MultiSigWallet.sol:130:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerAddition(owner);
        ^------------------^
multisig/MultiSigWallet.sol:149:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerRemoval(owner);
        ^-----------------^
multisig/MultiSigWallet.sol:168:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerRemoval(owner);
        ^-----------------^
multisig/MultiSigWallet.sol:169:9: Warning: Invoking events without "emit" prefix is deprecated.
        OwnerAddition(newOwner);
        ^---------------------^
multisig/MultiSigWallet.sol:180:9: Warning: Invoking events without "emit" prefix is deprecated.
        RequirementChange(_required);
        ^--------------------------^
multisig/MultiSigWallet.sol:205:9: Warning: Invoking events without "emit" prefix is deprecated.
        Confirmation(msg.sender, transactionId);
        ^-------------------------------------^
multisig/MultiSigWallet.sol:218:9: Warning: Invoking events without "emit" prefix is deprecated.
        Revocation(msg.sender, transactionId);
        ^-----------------------------------^
multisig/MultiSigWallet.sol:231:17: Warning: Invoking events without "emit" prefix is deprecated.
                Execution(transactionId);
                ^----------------------^
multisig/MultiSigWallet.sol:233:17: Warning: Invoking events without "emit" prefix is deprecated.
                ExecutionFailure(transactionId);
                ^-----------------------------^
multisig/MultiSigWallet.sol:277:9: Warning: Invoking events without "emit" prefix is deprecated.
        Submission(transactionId);
        ^-----------------------^
multisig/MultiSigWalletWithTimeLock.sol:73:9: Warning: Invoking events without "emit" prefix is deprecated.
        TimeLockChange(_secondsTimeLocked);
        ^--------------------------------^
multisig/MultiSigWalletWithTimeLock.sol:86:9: Warning: Invoking events without "emit" prefix is deprecated.
        Confirmation(msg.sender, transactionId);
        ^-------------------------------------^
multisig/MultiSigWalletWithTimeLock.sol:102:9: Warning: Invoking events without "emit" prefix is deprecated.
        Revocation(msg.sender, transactionId);
        ^-----------------------------------^
multisig/MultiSigWalletWithTimeLock.sol:116:13: Warning: Invoking events without "emit" prefix is deprecated.
            Execution(transactionId);
            ^----------------------^
multisig/MultiSigWalletWithTimeLock.sol:118:13: Warning: Invoking events without "emit" prefix is deprecated.
            ExecutionFailure(transactionId);
            ^-----------------------------^
multisig/MultiSigWalletWithTimeLock.sol:132:9: Warning: Invoking events without "emit" prefix is deprecated.
        ConfirmationTimeSet(transactionId, confirmationTime);
        ^--------------------------------------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:77:9: Warning: Invoking events without "emit" prefix is deprecated.
        AssetProxyRegistration(assetProxyContract, isRegistered);
        ^------------------------------------------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:92:13: Warning: Invoking events without "emit" prefix is deprecated.
            Execution(transactionId);
            ^----------------------^
protocol/AssetProxyOwner/AssetProxyOwner.sol:94:13: Warning: Invoking events without "emit" prefix is deprecated.
            ExecutionFailure(transactionId);
            ^-----------------------------^
```
---

## [12]
```
==== Integer Overflow ====
Type: Warning
Contract: MixinAuthorizable
Function name: getAuthorizedAddresses()
PC address: 700
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:111

function getAuthorizedAddresses()
        external
        view
        returns (address[] memory)
    {
        return authorities;
    }

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MixinAuthorizable
Function name: addAuthorizedAddress(address)
PC address: 1307
A possible integer overflow exists in the function `addAuthorizedAddress(address)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: utils/Ownable/Ownable.sol:1



/*
 * Ownable
 *

--------------------

==== Exception state ====
Type: Informational
Contract: MixinAuthorizable
Function name: _function_0x494503d4
PC address: 1506
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:40

address[] public authorities

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MixinAuthorizable
Function name: getAuthorizedAddresses()
PC address: 3638
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:116

return authorities

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MixinAuthorizable
Function name: getAuthorizedAddresses()
PC address: 3640
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:116

return authorities

--------------------
```
---

## [13]
```
==== Message call to external contract ====
Type: Warning
Contract: ERC721Proxy
Function name: 
PC address: 597
This contract executes a message call to an address provided as a function argument. Generally, it is not recommended to call user-supplied addresses using Solidity's call() construct. Note that attackers might leverage reentrancy attacks to exploit race conditions or manipulate this contract's state.
--------------------
In file: protocol/AssetProxy/ERC721Proxy.sol:135

call(
                    gas,            // forward all gas
                    token,          // call address of token contract
                    0,              // don't send any ETH
                    0,              // pointer to start of input
                    100,            // length of input
                    0,              // write output to null
                    0               // output size is 0 bytes
                )

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC721Proxy
Function name: getAuthorizedAddresses()
PC address: 1382
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:111

function getAuthorizedAddresses()
        external
        view
        returns (address[] memory)
    {
        return authorities;
    }

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC721Proxy
Function name: addAuthorizedAddress(address)
PC address: 1989
A possible integer overflow exists in the function `addAuthorizedAddress(address)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: utils/Ownable/Ownable.sol:1



/*
 * Ownable
 *

--------------------

==== Exception state ====
Type: Informational
Contract: ERC721Proxy
Function name: _function_0x494503d4
PC address: 2188
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:40

address[] public authorities

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC721Proxy
Function name: getAuthorizedAddresses()
PC address: 4381
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:116

return authorities

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC721Proxy
Function name: getAuthorizedAddresses()
PC address: 4383
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:116

return authorities

--------------------

```
---

## [14]
```
==== Message call to external contract ====
Type: Warning
Contract: ERC20Proxy
Function name: 
PC address: 464
This contract executes a message call to an address provided as a function argument. Generally, it is not recommended to call user-supplied addresses using Solidity's call() construct. Note that attackers might leverage reentrancy attacks to exploit race conditions or manipulate this contract's state.
--------------------
In file: protocol/AssetProxy/ERC20Proxy.sol:85

call(
                    gas,            // forward all gas
                    token,          // call address of token contract
                    0,              // don't send any ETH
                    0,              // pointer to start of input
                    100,            // length of input
                    0,              // write output over input
                    32              // output size should be 32 bytes
                )

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC20Proxy
Function name: getAuthorizedAddresses()
PC address: 1266
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:111

function getAuthorizedAddresses()
        external
        view
        returns (address[] memory)
    {
        return authorities;
    }

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC20Proxy
Function name: addAuthorizedAddress(address)
PC address: 1873
A possible integer overflow exists in the function `addAuthorizedAddress(address)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: utils/Ownable/Ownable.sol:1



/*
 * Ownable
 *

--------------------

==== Exception state ====
Type: Informational
Contract: ERC20Proxy
Function name: _function_0x494503d4
PC address: 2072
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:40

address[] public authorities

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC20Proxy
Function name: getAuthorizedAddresses()
PC address: 4265
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:116

return authorities

--------------------

==== Integer Overflow ====
Type: Warning
Contract: ERC20Proxy
Function name: getAuthorizedAddresses()
PC address: 4267
A possible integer overflow exists in the function `getAuthorizedAddresses()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: protocol/AssetProxy/MixinAuthorizable.sol:116

return authorities

--------------------
```
---

## [15]
```
==== Integer Overflow ====
Type: Warning
Contract: MultiSigWallet
Function name: getOwners()
PC address: 1358
A possible integer overflow exists in the function `getOwners()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:313

function getOwners()
        public
        constant
        returns (address[])
    {
        return owners;
    }

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWallet
Function name: getTransactionIds(uint256,uint256,bool,bool)
PC address: 1522
A possible integer overflow exists in the function `getTransactionIds(uint256,uint256,bool,bool)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:348

function getTransactionIds(uint from, uint to, bool pending, bool executed)
        public
        constant
        returns (uint[] _transactionIds)
    {
        uint[] memory transactionIdsTemp = new uint[](transactionCount);
        uint count = 0;
        uint i;
        for (i=0; i<transactionCount; i++)
            if (   pending && !transactions[i].executed
                || executed && transactions[i].executed)
            {
                transactionIdsTemp[count] = i;
                count += 1;
            }
        _transactionIds = new uint[](to - from);
        for (i=from; i<to; i++)
            _transactionIds[i - from] = transactionIdsTemp[i];
    }

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWallet
Function name: getConfirmations(uint256)
PC address: 1652
A possible integer overflow exists in the function `getConfirmations(uint256)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:324

function getConfirmations(uint transactionId)
        public
        constant
        returns (address[] _confirmations)
    {
        address[] memory confirmationsTemp = new address[](owners.length);
        uint count = 0;
        uint i;
        for (i=0; i<owners.length; i++)
            if (confirmations[transactionId][owners[i]]) {
                confirmationsTemp[count] = owners[i];
                count += 1;
            }
        _confirmations = new address[](count);
        for (i=0; i<count; i++)
            _confirmations[i] = confirmationsTemp[i];
    }

--------------------

==== Exception state ====
Type: Informational
Contract: MultiSigWallet
Function name: _function_0x025e7c27
PC address: 2249
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: multisig/MultiSigWallet.sol:24

address[] public owners

--------------------

==== Integer Underflow ====
Type: Warning
Contract: MultiSigWallet
Function name: removeOwner(address)
PC address: 2548
A possible integer underflow exists in the function `removeOwner(address)`.
The subtraction may result in a value < 0.
--------------------
In file: multisig/MultiSigWallet.sol:141

owners.length - 1

--------------------

==== Exception state ====
Type: Informational
Contract: MultiSigWallet
Function name: removeOwner(address)
PC address: 2592
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: multisig/MultiSigWallet.sol:142

owners[i]

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWallet
Function name: addOwner(address)
PC address: 3801
A possible integer overflow exists in the function `addOwner(address)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:126

owners.length + 1

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWallet
Function name: getOwners()
PC address: 4835
A possible integer overflow exists in the function `getOwners()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:318

return owners

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWallet
Function name: getOwners()
PC address: 4837
A possible integer overflow exists in the function `getOwners()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:318

return owners

--------------------

==== Integer Underflow ====
Type: Warning
Contract: MultiSigWallet
Function name: getTransactionIds(uint256,uint256,bool,bool)
PC address: 5163
A possible integer underflow exists in the function `getTransactionIds(uint256,uint256,bool,bool)`.
The subtraction may result in a value < 0.
--------------------
In file: multisig/MultiSigWallet.sol:363

to - from

--------------------

==== Exception state ====
Type: Informational
Contract: MultiSigWallet
Function name: getTransactionIds(uint256,uint256,bool,bool)
PC address: 5237
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: multisig/MultiSigWallet.sol:365

transactionIdsTemp[i]

--------------------
```
---

## [16]
```
==== Integer Overflow ====
Type: Warning
Contract: MultiSigWalletWithTimeLock
Function name: getOwners()
PC address: 1479
A possible integer overflow exists in the function `getOwners()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:313

function getOwners()
        public
        constant
        returns (address[])
    {
        return owners;
    }

--------------------

==== Exception state ====
Type: Informational
Contract: MultiSigWalletWithTimeLock
Function name: _function_0x025e7c27
PC address: 2435
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: multisig/MultiSigWallet.sol:24

address[] public owners

--------------------

==== Integer Underflow ====
Type: Warning
Contract: MultiSigWalletWithTimeLock
Function name: removeOwner(address)
PC address: 2734
A possible integer underflow exists in the function `removeOwner(address)`.
The subtraction may result in a value < 0.
--------------------
In file: multisig/MultiSigWallet.sol:141

owners.length - 1

--------------------

==== Exception state ====
Type: Informational
Contract: MultiSigWalletWithTimeLock
Function name: removeOwner(address)
PC address: 2778
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: multisig/MultiSigWallet.sol:142

owners[i]

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWalletWithTimeLock
Function name: addOwner(address)
PC address: 4016
A possible integer overflow exists in the function `addOwner(address)`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:126

owners.length + 1

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWalletWithTimeLock
Function name: getOwners()
PC address: 5173
A possible integer overflow exists in the function `getOwners()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:318

return owners

--------------------

==== Integer Overflow ====
Type: Warning
Contract: MultiSigWalletWithTimeLock
Function name: getOwners()
PC address: 5175
A possible integer overflow exists in the function `getOwners()`.
The addition or multiplication may result in a value higher than the maximum representable integer.
--------------------
In file: multisig/MultiSigWallet.sol:318

return owners

--------------------

==== Integer Underflow ====
Type: Warning
Contract: MultiSigWalletWithTimeLock
Function name: getTransactionIds(uint256,uint256,bool,bool)
PC address: 5501
A possible integer underflow exists in the function `getTransactionIds(uint256,uint256,bool,bool)`.
The subtraction may result in a value < 0.
--------------------
In file: multisig/MultiSigWallet.sol:363

to - from

--------------------

==== Exception state ====
Type: Informational
Contract: MultiSigWalletWithTimeLock
Function name: getTransactionIds(uint256,uint256,bool,bool)
PC address: 5575
A reachable exception (opcode 0xfe) has been detected. This can be caused by type errors, division by zero, out-of-bounds array access, or assert violations. This is acceptable in most situations. Note however that `assert()` should only be used to check invariants. Use `require()` for regular input checking. 
--------------------
In file: multisig/MultiSigWallet.sol:365

transactionIdsTemp[i]

--------------------
```

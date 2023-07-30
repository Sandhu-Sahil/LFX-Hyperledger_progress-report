# 🧠 `tx.origin` vs `msg.sender` in Ethereum Smart Contracts

## 👀 Overview

In Ethereum smart contract development, understanding the differences between `tx.origin` and `msg.sender` is crucial for security and preventing potential vulnerabilities. Both variables provide information about the sender of a transaction, but they serve different purposes and have distinct implications.

## 🕳️ `tx.origin`: The Original Sender

`tx.origin` is a global variable in Solidity that represents the original sender of a transaction. It is the external account that initiated the transaction and triggered the contract execution. Even if the contract invokes another contract, `tx.origin` remains constant, representing the external user who initiated the entire transaction.

## 🏡 `msg.sender`: The Immediate Sender

`msg.sender`, on the other hand, represents the immediate sender of the current message or transaction. In the context of contract-to-contract communication, it refers to the address of the contract that invokes the current contract's function. If a contract A calls a function in contract B, then `msg.sender` within contract B will be contract A's address.

## 🛡️ Security Implications

The key difference between `tx.origin` and `msg.sender` lies in their security implications. Relying on `tx.origin` for access control can lead to potential vulnerabilities, such as "Cross-Function Race Condition" attacks.

### 📉 Cross-Function Race Condition

Consider the following scenario:

1. A user initiates a transaction to a contract C, with contract B being the middleman.
2. Contract B calls contract C's function that checks the sender's address using `tx.origin` for access control.
3. Before contract C's function completes execution, contract B invokes another contract D, triggering another function that requires different access rights.
4. The attacker exploits the window of opportunity between contract B's function call to contract C and the completion of contract C's function, using a different contract to gain unauthorized access.

## 🏛️ Real-Life Example: The Parity Multisig Hack

One infamous example of the misuse of `tx.origin` is the Parity Multisig Wallet hack. In this attack, hackers exploited a vulnerability in a multisig contract that relied on `tx.origin` for access control. By creating a malicious contract and using it as a middleman, the attackers tricked the original multisig contract into granting them access to the funds.

## 👮 Prevention: Rely on `msg.sender` for Access Control

To prevent the Cross-Function Race Condition and other potential attacks, it is best practice to use `msg.sender` for access control in most cases. `msg.sender` represents the immediate sender of the current transaction and is not affected by any intermediate contract calls.

```solidity
contract MyContract {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    function sensitiveFunction() public {
        require(msg.sender == owner, "Only the contract owner can access this function");
        // Function logic accessible only to the contract owner
    }
}
```

In this example, the `sensitiveFunction` can only be accessed by the contract owner, as `msg.sender` is used for access control.

## 👋 Conclusion

`tx.origin` and `msg.sender` are both global variables in Solidity that provide information about the sender of a transaction. However, they serve different purposes and have distinct security implications. Developers should be aware of these differences and use `msg.sender` for access control in most cases.

# Resources

https://learnweb3.io/degrees/ethereum-developer-degree/senior/never-use-tx-origin-again/
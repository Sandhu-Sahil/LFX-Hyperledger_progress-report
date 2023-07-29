# Bug testing

https://github.com/Sandhu-Sahil/re-entrancy-BUG

# 🤯 The Bug That Cost $60 Million - Re-entrancy

In the world of smart contracts, security is paramount. One of the most infamous vulnerabilities that caused a loss of $60 million is known as "Re-entrancy." Today, we will delve into the concept of Re-entrancy, understand its implications, and explore preventive measures, including the use of OpenZeppelin's ReentrancyGuard library.

## 👀 What is Re-entrancy?

Re-entrancy is a critical security vulnerability that arises when a contract allows external calls to other contracts before finishing its own execution. This can lead to unexpected behaviors, where an attacker exploits the contract's re-entrant nature to manipulate its state or drain its funds.

Consider the following example of a vulnerable smart contract:

```solidity
contract VulnerableContract {
    mapping(address => uint256) balances;

    function withdraw(uint256 _amount) public {
        uint256 balance = balances[msg.sender];
        require(balance >= _amount, "Insufficient balance");
        balances[msg.sender] -= _amount;
        (bool success, ) = msg.sender.call{value: _amount}("");
        require(success, "Transfer failed");
    }
}
```

In this example, the `withdraw` function allows users to withdraw funds from their balance. However, the contract first transfers the funds and then updates the user's balance. This creates an opportunity for an attacker to recursively call the `withdraw` function before the balance update, effectively draining the contract of funds.

## 🤔 How Does Re-entrancy Work?

Let's take a closer look at the `withdraw` function to understand how re-entrancy works. The function first checks if the user has sufficient balance and then transfers the requested amount. However, the contract does not update the user's balance before transferring the funds. This creates a window of opportunity for an attacker to recursively call the `withdraw` function before the balance update.

Consider the following scenario:

1. Alice has a balance of 100 ETH in the contract.
2. Alice calls the `withdraw` function to withdraw 50 ETH.
3. The contract checks if Alice has sufficient balance and transfers 50 ETH to Alice.
4. The contract updates Alice's balance to 50 ETH.
5. Alice's transaction is complete.

Now, consider the following scenario:

1. Alice has a balance of 100 ETH in the contract.
2. Alice calls the `withdraw` function to withdraw 50 ETH.
3. The contract checks if Alice has sufficient balance and transfers 50 ETH to Alice.
4. Alice calls the `withdraw` function to withdraw 50 ETH.
5. The contract checks if Alice has sufficient balance and transfers 50 ETH to Alice.
6. Alice calls the `withdraw` function to withdraw 50 ETH.
7. The contract checks if Alice has sufficient balance and transfers 50 ETH to Alice.
8. Alice calls the `withdraw` function to withdraw 50 ETH.
9. The contract checks if Alice has sufficient balance and transfers 50 ETH to Alice.
10. Alice's transaction is complete.

In this scenario, Alice is able to withdraw 200 ETH from the contract, even though she only has 100 ETH in her balance. This is because the contract does not update Alice's balance before transferring the funds. This creates a window of opportunity for Alice to recursively call the `withdraw` function before the balance update.

## 🛡️ Preventing Re-entrancy

The best way to prevent re-entrancy is to follow the Checks-Effects-Interactions pattern. This pattern ensures that the contract first checks all conditions, then updates the contract state, and finally interacts with other contracts. This prevents an attacker from recursively calling the contract before the state update.

Consider the following example of a secure smart contract:

```solidity

contract SecureContract {
    mapping(address => uint256) balances;

    function withdraw(uint256 _amount) public {
        uint256 balance = balances[msg.sender];
        require(balance >= _amount, "Insufficient balance");
        balances[msg.sender] -= _amount;
        (bool success, ) = msg.sender.call{value: _amount}("");
        require(success, "Transfer failed");
    }
}
```

In this example, the `withdraw` function first checks if the user has sufficient balance, then updates the user's balance, and finally transfers the requested amount. This ensures that the contract state is updated before interacting with other contracts, preventing re-entrancy.

## 📚 ReentrancyGuard

The OpenZeppelin ReentrancyGuard library provides a simple way to prevent re-entrancy. The library implements the Checks-Effects-Interactions pattern by using a boolean variable to track the contract's state. The variable is set to `true` before interacting with other contracts and set to `false` after the interaction is complete. This prevents an attacker from recursively calling the contract before the state update.

Consider the following example of a secure smart contract using the ReentrancyGuard library:

```solidity

import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

contract SecureContract is ReentrancyGuard {
    mapping(address => uint256) balances;

    function withdraw(uint256 _amount) public nonReentrant {
        uint256 balance = balances[msg.sender];
        require(balance >= _amount, "Insufficient balance");
        balances[msg.sender] -= _amount;
        (bool success, ) = msg.sender.call{value: _amount}("");
        require(success, "Transfer failed");
    }
}
```

In this example, the `withdraw` function uses the `nonReentrant` modifier to prevent re-entrancy. The modifier ensures that the contract state is updated before interacting with other contracts, preventing re-entrancy.

## 🏁 Conclusion

Re-entrancy is a critical security vulnerability that arises when a contract allows external calls to other contracts before finishing its own execution. This can lead to unexpected behaviors, where an attacker exploits the contract's re-entrant nature to manipulate its state or drain its funds. The best way to prevent re-entrancy is to follow the Checks-Effects-Interactions pattern. This pattern ensures that the contract first checks all conditions, then updates the contract state, and finally interacts with other contracts. The OpenZeppelin ReentrancyGuard library provides a simple way to prevent re-entrancy. The library implements the Checks-Effects-Interactions pattern by using a boolean variable to track the contract's state. The variable is set to `true` before interacting with other contracts and set to `false` after the interaction is complete. This prevents an attacker from recursively calling the contract before the state update.




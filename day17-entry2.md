# Ethereum Storage and Execution 👀

Today, we will embark on a journey to explore the fascinating world of Ethereum's storage and execution mechanisms. Ethereum is not just a cryptocurrency; it's a decentralized virtual machine capable of executing smart contracts and decentralized applications (DApps). To understand how Ethereum accomplishes this, we'll delve into key concepts such as the World State, Account State, the Ethereum Virtual Machine, and the role of Gas in the execution process.

## Recap 🧠

Before diving into Ethereum's storage and execution, let's quickly recap the fundamental components of Ethereum:

- **Blockchain**: Ethereum's foundation is a distributed ledger called the blockchain, where all transactions and smart contract interactions are recorded in blocks.

- **Smart Contracts**: These are self-executing contracts with predefined rules that automatically execute when specific conditions are met. Smart contracts are at the heart of Ethereum's decentralized applications.

- **Decentralized Applications (DApps)**: DApps are applications that run on the Ethereum blockchain, leveraging smart contracts for their logic and functionality.

## World State 🗺️

The World State in Ethereum refers to the state of all accounts and contracts at a specific point in time. It represents the current balances, contract codes, and storage data for each account. The World State is an essential concept as it helps nodes in the network verify transactions and execute smart contracts consistently.

## Account State 📒

Each account in Ethereum has two components: **Account Balance** (in Ether) and **Contract Code** (for smart contracts). An account can be either an **Externally Owned Account (EOA)** or a **Contract Account**. EOAs are controlled by private keys, while contract accounts are controlled by the logic of their corresponding smart contracts.

## Types of Transactions 💵

In Ethereum, there are two main types of transactions:

1. **Message Transactions**: These transactions are sent by EOAs to invoke the execution of a smart contract. The transaction can include a payload with function arguments and Ether for value transfer.

2. **Contract Creation Transactions**: These transactions deploy a new smart contract onto the Ethereum blockchain. They contain the compiled code of the smart contract and any constructor arguments.

## Messages ✉️

Messages are an essential part of Ethereum's execution model. When a smart contract is executed, it can generate internal messages to other contracts. These messages trigger further contract executions and interactions, forming a chain of transactions.

## The Ethereum Virtual Machine 📠

The Ethereum Virtual Machine (EVM) is a runtime environment for executing smart contracts. It is a deterministic, stack-based machine that processes bytecode. The EVM is sandboxed, meaning it operates in isolation and has no access to the network or file system.

### Stack

The EVM employs a stack to store data and intermediate results during contract execution. Operations are performed on the top elements of the stack.

### Memory 🗓️

The EVM has an expandable memory area used during contract execution for temporary data storage.

### Account Storage 🔒

Each contract has its storage space to store persistent data. This storage is organized as a key-value mapping.

## Execution Model 🧨

Smart contracts are executed on the EVM in a deterministic manner. This ensures that all nodes on the network reach the same state after executing a transaction.

## Gas during Execution ⛽

Gas is a critical concept in Ethereum. It is a unit used to measure the computational effort required to execute a transaction or smart contract. Gas prevents malicious users from overloading the network with infinite loops or complex computations. Each operation consumes a specific amount of gas, and users must pay gas fees to compensate miners for computation.

## Conclusion 👋

Understanding Ethereum's storage and execution mechanisms is vital for anyone involved in blockchain development or exploring decentralized applications. The World State, Account State, EVM, and Gas all play crucial roles in maintaining the integrity and security of the Ethereum network.

In our quest to explore the depths of Ethereum's capabilities, we've touched on just a few aspects of this vast ecosystem. The world of blockchain and decentralized technologies continues to evolve, offering endless opportunities for innovation and disruption.

Happy exploring on the Ethereum blockchain!

## References

[1] Ethereum Whitepaper - https://ethereum.org/en/whitepaper/
[2] Ethereum Yellow Paper - https://ethereum.github.io/yellowpaper/paper.pdf
[3] Ethereum Improvement Proposals (EIPs) - https://eips.ethereum.org/
[4] Mastering Ethereum by Andreas M. Antonopoulos and Gavin Wood - https://github.com/ethereumbook/ethereumbook

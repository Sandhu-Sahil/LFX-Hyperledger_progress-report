# Mango Tracking Example on Hyperledger Fabric: Understanding Asset, Transactions, and Chaincode

## Introduction

Hyperledger Fabric is a robust and flexible framework for building enterprise-grade blockchain applications. In this blog post, we will explore a practical use case of mango tracking using Hyperledger Fabric. We will delve into the core components of the blockchain network, such as assets, transactions, and chaincode, to understand how this use case is implemented.

## Use Case: Mango Tracking

Imagine a scenario where a mango supplier wants to track the journey of their mangoes from the farm to the end consumer. This use case requires transparency and immutability to ensure the authenticity of the mangoes. Hyperledger Fabric provides a perfect solution for this with its permissioned and modular architecture.

## Asset, Transaction, and State

In the mango tracking use case, the asset is a "Mango," which will have specific attributes such as farm location, harvest date, and quality. Each mango will be represented as a unique asset on the blockchain.

A "Transaction" in this context refers to any activity related to the mango, such as harvesting, packaging, shipping, and delivery. Each transaction will update the state of the mango asset, reflecting its current status.

The "State" refers to the current state of the mango asset on the blockchain. It includes all the attributes of the mango, such as farm location, harvest date, and quality, at a particular point in time.

## Ledger, Transaction Log, and World State

Hyperledger Fabric maintains a distributed ledger that contains the transaction history of all assets on the network. This ledger is replicated across multiple nodes, ensuring fault tolerance and data integrity.

The "Transaction Log" is a chronological record of all transactions that have occurred on the network. It includes details such as the transaction ID, timestamp, and involved parties.

The "World State" is a snapshot of the current state of all assets on the blockchain. It provides efficient access to the latest state of an asset without the need to replay all transactions.

## Smart Contract vs. Chaincode

In Hyperledger Fabric, "Chaincode" is the term used to refer to the smart contract deployed on the network. It contains the business logic that governs the interactions with the assets.

A "Smart Contract" is a self-executing contract with the terms of the agreement between the parties written directly into code. It automatically enforces the terms of the contract and executes actions when predefined conditions are met.

## Fabric Contract API

The Fabric Contract API allows developers to interact with the chaincode and access the ledger. Here are some essential functions of the Fabric Contract API:

### PutState

The `PutState` function is used to add or update the state of an asset on the ledger. In the mango tracking use case, it would be used to record the latest state of a mango after each transaction, such as updating its location or quality.

### GetState

The `GetState` function allows querying the current state of an asset from the ledger. This function can be used to retrieve the attributes of a specific mango at any point in time.

### DeleteState

The `DeleteState` function is used to remove an asset from the ledger. In the mango tracking use case, it might be used if a mango becomes unsellable or is no longer valid.

## Conclusion

In this blog post, we explored the mango tracking use case on Hyperledger Fabric and gained insights into the key components of the blockchain network, such as assets, transactions, and chaincode. We learned how assets are tracked through their lifecycle using transactions, and how chaincode, as a smart contract, enforces the business logic.

Hyperledger Fabric's permissioned and modular architecture makes it an ideal choice for enterprise-level applications that require transparency, security, and scalability.

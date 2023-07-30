# 🤫 A Cautionary Tale to Never Use On-Chain Randomness

## 👀 Overview

As blockchain technology continues to evolve, developers are often faced with the challenge of generating random numbers within smart contracts. While it may seem convenient to use on-chain randomness, it comes with significant risks and potential vulnerabilities.

## 🎲 The Need for Randomness in Smart Contracts

Randomness is an essential component of various applications, including gaming, gambling, and distributed systems. In traditional web applications, developers can rely on the operating system's random number generator. However, in the decentralized world of blockchain, generating random numbers is not straightforward.

## 💔 The Risks of On-Chain Randomness

Using on-chain randomness, such as `block.timestamp` or `blockhash`, may appear to provide a solution for generating random numbers. However, it exposes smart contracts to potential manipulation and exploitation.

### Manipulation by Miners

Miners can manipulate the timestamp and the block hash to some extent, especially in Proof-of-Work (PoW) blockchains. This manipulation can affect the outcome of random events, making the results predictable and unfair.

### Front-Running Attacks

Front-running is another concern with on-chain randomness. Malicious actors can observe pending transactions and submit their own transactions with slightly altered parameters to take advantage of the randomness.

### Predictability

Blockchain data is publicly accessible, allowing anyone to analyze the chain's history and anticipate future randomness. This predictability compromises the integrity of random events.

### High Gas Costs

Generating on-chain randomness can be expensive due to the computational requirements and gas costs involved. This makes it impractical for many use cases.

## 👮 Preventions

To mitigate the risks associated with on-chain randomness, developers should consider alternative solutions:

### External Oracles

Using an external oracle service that provides off-chain randomness can be a more secure approach. These services fetch randomness from various sources and feed it into the smart contract.

### Commit-Reveal Scheme

The commit-reveal scheme involves a multi-step process where participants commit to their random choices first and reveal them later. This way, front-running attacks become more challenging as the true randomness remains hidden until the reveal phase.

### Chainlink VRF

Chainlink VRF (Verifiable Random Function) is a decentralized randomness solution provided by the Chainlink network. It offers a secure and tamper-resistant source of randomness for smart contracts.

### Off-Chain Computation

In some cases, random numbers can be computed off-chain and securely shared with the smart contract. This approach ensures that the randomness is not influenced by on-chain manipulations.

## 👋 Conclusion

Using on-chain randomness can expose smart contracts to severe security risks and compromise the integrity of random events. Developers should be cautious when employing on-chain randomness and consider alternative solutions that prioritize security and fairness.

# Resources

https://learnweb3.io/degrees/ethereum-developer-degree/senior/generating-random-numbers-on-chain/
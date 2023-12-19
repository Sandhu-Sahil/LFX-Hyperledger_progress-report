# Byzantine Distributed Ledger System (BDLS) - A Comprehensive Guide

## Introduction

In the realm of distributed systems, achieving consensus among participants is a critical challenge. The Byzantine Distributed Ledger System (BDLS) addresses this challenge through a robust consensus mechanism. This comprehensive guide delves into the mechanisms and workings of BDLS, shedding light on its protocol and decision message propagation.

## 1. Understanding Byzantine Fault Tolerant Protocols

Byzantine Fault Tolerant (BFT) protocols are designed to ensure the reliability of distributed systems in the presence of faulty or malicious nodes. BDLS builds upon this foundation, aiming to provide a secure and fault-tolerant environment for consensus among distributed participants.

## 2. The BDLS Protocol - Decision Message Propagation

At the core of BDLS is its unique approach to decision message propagation. Step 5 of the BDLS protocol involves strongly reliably broadcasting the decide message. The protocol relies on Bracha's strongly reliable broadcast protocol for this purpose. Remark 2 in the BDLS protocol emphasizes the importance of decision message propagation, highlighting potential issues in protocols like HotStuff that lack this crucial process.

## 3. HotStuff BFT Protocol

HotStuff BFT, a key player in the BFT landscape, is examined closely in this guide. The protocol includes basic and chained versions, but for simplicity, we focus on the basic HotStuff BFT protocol. With differences from traditional BFT protocols like PBFT, HotStuff introduces a star topology communication network and employs threshold digital signature schemes.

## 4. Phases and Variables in HotStuff

A detailed exploration of the HotStuff BFT protocol includes its phases: prepare, pre-commit, commit, and decide. Key state variables, including viewNumber, prepareQC, and lockedQC, play pivotal roles. The protocol utilizes a tree structure for pending commands, providing a unique perspective on consensus mechanisms.

## 5. Importance of Decision Message Propagation in HotStuff

This section underscores the critical role of decision message propagation in the HotStuff protocol. Through scenarios, we illustrate the repercussions of a lack of decision message propagation. Inconsistencies arise in command execution among participants, emphasizing the necessity of this process for maintaining the integrity of the consensus mechanism.

## 6. Semantics and Protocol Integrity

Examining the internals of HotStuff's tree nodes, we identify potential shortcomings related to command execution status. The absence of such information in tree nodes poses a challenge to ensuring the validity of executed commands. This section suggests the inclusion of command execution status in tree nodes to prevent inconsistencies.

## 7. Bracha's Strongly Reliable Broadcast Primitive

Delving deeper into the mechanics of BDLS, we explore Bracha's strongly reliable broadcast primitive. This primitive ensures that honest participants accept transmitted messages reliably. The protocol design guarantees consensus in the presence of malicious actors, offering a robust foundation for BDLS.

## 8. Conclusion

Summarizing the key points discussed in this guide, we underscore the significance of decision message propagation in BFT protocols. The insights into the HotStuff protocol, coupled with the exploration of Bracha's primitive, highlight the importance of considering command execution status for maintaining consistency and integrity in distributed ledger systems.

This comprehensive guide serves as a valuable resource for understanding the intricacies of BDLS, offering insights into decision message propagation, HotStuff BFT protocol, and the role of Bracha's strongly reliable broadcast primitive.

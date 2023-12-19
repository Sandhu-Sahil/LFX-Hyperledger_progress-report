# Processing Requests in Byzantine Distributed Ledger System (BDLS)

In the Byzantine Distributed Ledger System (BDLS), the processing of requests involves a series of steps to ensure the integrity and consensus among distributed participants. This blog post provides an in-depth exploration of how a request traverses through the BDLS protocol.

## 1. **Initiation of a Request**

The journey begins when a client initiates a request to the BDLS network. This request typically involves a transaction or operation that needs consensus agreement among the distributed participants.

## 2. **Proposal Phase**

Upon receiving the client's request, the designated leader participant takes charge. In BDLS, leader selection mechanisms vary, but for simplicity, let's consider a scenario where a leader is chosen to handle the proposal. The leader creates a proposal encapsulating the client's request.

## 3. **Broadcasting the Proposal**

The leader broadcasts the proposal to all participants in the network. This broadcast ensures that every participant is aware of the proposed transaction, laying the groundwork for consensus-building.

## 4. **Validation and Prepare Phase**

Upon receiving the proposal, each participant validates its authenticity and checks whether it complies with the current state of the ledger. This phase, known as the prepare phase, involves participants endorsing the proposal by signing it.

## 5. **Pre-Commit Phase**

After receiving a sufficient number of endorsements (often determined by a threshold), the leader aggregates these validations into a pre-commit message. This message signifies the collective agreement among participants during the prepare phase.

## 6. **Commit Phase**

The leader broadcasts the pre-commit message to all participants. Upon receiving the pre-commit message, each participant validates it and, if accepted, sends its commitment by signing the pre-commit message. This commitment phase ensures that participants are fully committed to the proposed transaction.

## 7. **Decision and Execution**

Once a participant receives a sufficient number of commitments, it enters the decision phase. In this phase, the leader aggregates commitments into a decision message, broadcasting it to all participants. Upon receiving the decision message, each participant executes the transaction locally, ensuring consistency across the network.

## 8. **Verification and Consensus**

Participants verify the executed transactions against the decision message. If consensus is reached, meaning a significant majority of participants agree on the transaction's validity, the request is considered processed successfully.

## Conclusion

The BDLS protocol's meticulous handling of requests through proposal, validation, commitment, and decision phases ensures that consensus is achieved among distributed participants. This robust process, coupled with Byzantine Fault Tolerant principles, makes BDLS a reliable framework for maintaining the integrity of distributed ledgers. Understanding the intricacies of request processing in BDLS is crucial for developers and architects working with distributed systems, providing insights into achieving consensus in challenging network environments.

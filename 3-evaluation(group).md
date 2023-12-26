# BiniBFT Consensus Framework Evaluation

## Overview

This README file provides an overview of the BiniBFT consensus framework, as presented in Evaluation 3. The evaluation report is a collaborative effort by Riddhi Katarki, Ajitesh Kumar Soni, Abhishek Ranjan, Ashna P S, Sahilsher Singh, and Siddhant Prateek Mahanayak during the Collaborative Learning Program under the mentorship of Dr. Anasuya Threse Innocent. The evaluation period was from 08-10-2023 to 13-12-2023, and the report was submitted on 14-12-2023.

![Random Polling](https://cdn.discordapp.com/attachments/904759123197952052/1186234940430483468/image.png)
![Time Weighted Voting](https://cdn.discordapp.com/attachments/904759123197952052/1186235044440838194/image.png)

## Consensus Mechanism with Random Polling

1. **Transaction Initiation:** The process starts with the client initiating a transaction (Trx initiation). This is where a user or an application requests a transaction to be processed by the network.

2. **Transaction Batching:** After a transaction is initiated, it is grouped with other transactions into a batch (Batched trx) which improves the efficiency of processing multiple transactions together rather than individually.

3. **Leader Selection:** Once transactions are batched, a leader is selected to propose the batch of transactions to the rest of the network. The leader selection is aided by a Verifiable Random Function (VRF), which helps in choosing the leader in a way that is random but verifiable by other participants in the network.

4. **Transaction Proposal:** The leader then proposes the batched transactions (Trx proposal) to the network. This involves sending out the transaction data to other nodes in the network for validation.

5. **Polling:** Concurrently, there is a random polling of 33% of the network. This suggests that a subset of the network is selected randomly to vote on the proposed transactions. The chart indicates that the process waits until 1/3 of the votes are received.

6. **Transaction Commitment:** Once the leader has successfully proposed the transaction and the necessary votes are received, the transaction is committed (Commit Trx) by the network.

7. **Transaction Settlement:** After the transaction is committed, it is then settled (Finalized Trx), which means it is officially recorded on the blockchain. This completes the process, and the client is informed that the transaction has been finalized.

## Consensus Mechanism with Time Weighted Voting

1. **Transaction Initiation:** A client starts the process by initiating a transaction.

2. **Transaction Batching:** Transactions are batched together for processing efficiency.

3. **Leader Selection:** A leader is selected through a Verifiable Random Function (VRF) to manage the batched transactions. This ensures randomness and fairness in leader selection.

4. **Transaction Proposal:** The selected leader proposes the batched transactions to the network.

5. **Time Weighted Voting (Polling):**
   - The network nodes participate in polling to approve the transaction proposal. This polling uses the Time Weighted Voting mechanism.
   - Each node in the network has a weight (w) that increases over time or epochs, representing their tenure in the network.

6. **Voting Constraints:**
   - Individual node weight is capped to ensure no single node can dominate the decision due to its longevity (as shown in the second chart, where w(i) <= 0.33 * (network_w)).
   - The sum of the weights (sum(w)) from the nodes participating in the polling must be greater than or equal to 51% of the total network weight to reach a decision (sum(w) >= (0.51 * network_w)).

7. **Transaction Commitment:** If the proposal receives enough weighted votes (>= 51% of network weight), the transaction is committed.

8. **Transaction Settlement:** The committed transaction is then finalized and recorded on the blockchain, and the client is notified of the transaction settlement.

## Dynamic Leader Allocation Process

1. **System Load Monitoring:** Continuously monitor the system's transaction rate, processing capacity, and overall network load.

2. **Load Thresholds:** Define load thresholds that trigger dynamic leader allocation. Consider factors such as transaction backlog and processing delays.

3. **Leader Availability:** Track the availability and performance metrics of potential leaders in the network.

4. **Allocation Trigger:** When the system load surpasses predefined thresholds, initiate dynamic leader allocation based on a Verifiable Random Function (VRF).

5. **VRF-Based Random Leader Selection:** Use a Verifiable Random Function to generate a random number that determines the leader selection. This ensures randomness while providing verifiability to other participants.

6. **Batch Queue Management:** If a batch queue exists, distribute batches among the selected leaders to ensure an even workload distribution.

7. **Concurrency Control:** Implement synchronization protocols to manage interactions between multiple leaders and maintain consistency.

8. **Transaction Proposal:** Each leader, determined by the VRF-based random selection, independently proposes its assigned batches to the network for validation.

9. **Polling and Voting:** Continue with the random polling and voting process for each proposed batch, ensuring decentralized agreement on transaction validity.

10. **Commitment Decision:** Based on the voting outcomes for each leader's proposed batches, make a commitment decision for each batch independently.

11. **Transaction Settlement:** Finalize the committed batches and record them on the blockchain.

12. **Leader Deallocation:** Periodically reassess the system load. If the load decreases and additional leaders are no longer needed, deallocate the surplus leaders.

## Integration of VRF:

### Random Leader Selection:

Utilize a Verifiable Random Function to generate random numbers for leader selection. This ensures that the leader selection process is not only random but also verifiable by other participants, enhancing transparency in the leader allocation mechanism.

## Network Load Consideration:

### Load-Driven Trigger:

Dynamically allocate leaders based on the load thresholds. This takes into account factors such as transaction backlog, processing delays, and overall network load to ensure that leader allocation aligns with the current demand on the system.

## Random Number for Leader Allocation:

### VRF-Based Random Allocation:

Leaders are allocated purely based on the random number generated by the Verifiable Random Function. This maintains a level of unpredictability while providing a means for participants to verify the legitimacy of the leader selection process.

## Group Members
- A Anasuya Threse Innocent 
- Riddhi Katarki
- Ajitesh Kumar Soni
- Abhishek Ranjan
- Ashna P S
- Siddhant Prateek
- Sahilsher Singh

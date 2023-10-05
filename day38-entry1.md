# BFT-SMART Performance Evaluation

In this section, we delve into the performance evaluation of BFT-SMART. We'll explore the results from various experiments, including micro-benchmarks, fault-scalability tests, multi-core awareness assessments, comparisons with other systems, and evaluations of BFT-SMART's performance under faults and reconfigurations.

## Experimental Setup

For our experiments, we used three replicas for Crash Fault Tolerance (CFT) and four replicas for Byzantine Fault Tolerance (BFT). We distributed up to 1600 client processes across four machines. All machines ran JRE 1.7.0_21 on Ubuntu Linux 10.04, hosted in Dell PowerEdge R410 servers. Each machine boasted 32 GB of memory and two quad-core 2.27 GHz Intel Xeon E5520 processors with hyperthreading (supporting 16 hardware threads). Communication between machines occurred via an isolated gigabit Ethernet network.

## Micro-benchmarks

We began with a series of micro-benchmarks designed to evaluate BFT-SMART's raw throughput and latency. These benchmarks assessed the system's performance with varying request/reply sizes, including 0/0, 100/100, 1024/1024, and 4096/4096 bytes.

In the results, we observed that the CFT protocol consistently outperformed its BFT counterpart. This discrepancy arises due to the reduced message exchange in the CFT setup, resulting in less work per client request for the replicas. Additionally, as expected, increasing the payload size led to decreased overall performance for BFT-SMART.

## Fault-Scalability

The next experiment explored the impact of the number of replicas on system throughput under different payloads. The results demonstrated that as the number of faults (denoted as 'f') increased, BFT-SMART's performance gracefully degraded for both CFT and BFT setups. This degradation occurred because BFT-SMART efficiently utilized the multiple cores of replicas for calculating Message Authentication Codes (MACs), had fewer messages to process in CFT setups, and avoided issues associated with IP multicast.

## Signatures and Multi-core Awareness

We examined the system's performance when client signatures were enabled. Clients signed every request, and replicas verified their authenticity before processing them. This introduced two significant service-throughput overheads: larger message sizes due to 1024-bit RSA signatures and the computational cost of signature verification.

Our results showed that BFT-SMART's architecture effectively exploited the multiple cores with hyperthreading. Signature verification was performed by the Netty thread pool, which utilized a number of threads proportional to the hardware threads on the machine.

## Comparison with Other Systems

We conducted a performance comparison between BFT-SMART and other representative State Machine Replication (SMR) systems using the 0/0 benchmark. The systems included PBFT, UpRight, and JPaxos.

The results demonstrated that BFT-SMART achieved a peak sustained throughput higher than PBFT and JPaxos in our environment. Although PBFT reached its peak throughput with only 10% of the clients required by BFT-SMART, it failed to achieve higher throughput with more than 100 clients, likely due to its single-threaded nature. JPaxos performed lower than reported in previous benchmarks, possibly due to differences in hardware threads. UpRight displayed considerably lower throughput compared to the others.

## Faults, Reconfigurations, etc.

In our final experiment, we assessed the behavior of an application implemented using BFT-SMART under replica failures, recoveries, and reconfigurations. The application involved an in-memory hashtable deployed on four replicas.

The results revealed how the system's throughput evolved during demanding workloads and various events. These events included adding replicas, crashing and recovering replicas, and reconfiguring the system. The system displayed resilience and adaptability in the face of such challenges.

## Conclusion

The performance evaluation of BFT-SMART highlights its robustness, efficiency, and adaptability in different scenarios. It consistently demonstrated competitive throughput and fault tolerance capabilities, making it a valuable choice for building distributed systems that require Byzantine Fault Tolerance.

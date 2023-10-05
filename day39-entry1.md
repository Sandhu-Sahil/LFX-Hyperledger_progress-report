# Lessons Learned from BFT-SMART Development

In this section, we will delve into the valuable insights and lessons learned from over five years of BFT-SMART's development. Through three generations of this Byzantine Fault-Tolerant (BFT) protocol, important knowledge was acquired regarding the implementation and maintenance of high-performance fault-tolerant systems in Java.

## Java as a BFT Programming Language

Despite some skepticism surrounding Java's suitability for high-throughput implementations of BFT protocols, the BFT-SMART team found it to be a viable choice. The decision was grounded in the need for a type-safe language with features conducive to secure software development, including a rich utility API and no direct memory access. Java's portability also factored into the choice.

However, it became evident that these features, if not used judiciously, could adversely impact protocol performance. For instance, object serialization presented a challenge. To optimize BFT-SMART, two key approaches were adopted:

1. Client-issued commands were defined as byte arrays instead of generic objects, eliminating the need for serialization and deserialization during message transmissions.
2. Standard object serialization on client requests was replaced with a custom method using data streams rather than object streams. This eliminated the serialization header from messages and significantly reduced batch size during consensus.

## Testing BFT Systems

Testing Byzantine Fault-Tolerant systems poses significant challenges. While there are no mature tools available for distributed system tracing, debugging, and verification, the BFT-SMART team adopted an approach based on JUnit, a popular unit testing tool. Automated test scripts were created to set up replicas, run client operations, verify results, and terminate replicas. Fault-injection frameworks and tools like the Netflix Chaos Monkey were considered to enhance the testing process. However, testing against malicious behaviors presented unique challenges.

1. Identifying critical malicious behaviors requiring injection into up to 'f' replicas demanded careful analysis of the protocol.
2. Injecting code for malicious behaviors could be achieved through patches, aspect-oriented programming, or commented code. The testing process faced the challenge of distinguishing liveness bugs from safety issues.

## Dealing with Heavy Loads

Under heavy loads, BFT-SMART exhibited several behaviors that shed light on the behavior of replication protocols:

1. Some replicas consistently lagged in message processing as only 'n - f' replicas were required for protocol progress.
2. Spontaneous total order (client requests reaching all replicas in the same order with high probability) was rare in switched networks under heavy loads, challenging assumptions of synchronized communication patterns.
3. The throughput of distributed systems tended to drop over time under heavy loads, a behavior known as thrashing. To mitigate thrashing, careful selection of data structures and queue bounds for thread communication was necessary.

## Maintenance & Robustness

Maintaining and developing a robust BFT system proved to be a substantial challenge. The BFT-SMART codebase, while relatively modest in size, was regarded as one of the most complex by experienced developers. Many seemingly unnecessary parts of the code were introduced to address unforeseen bugs that emerged as the system was deployed in various projects. The complexity arises from bridging the gap between protocol specifications and efficient, robust implementation.

One key lesson learned was that building a robust BFT replication library is an iterative process. Continual development, improvement, and adaptation to diverse application scenarios are essential. In academia, opportunities for funding, publication, and student projects can be sought as the software evolves.

Over the years, BFT-SMART was used to implement a variety of applications, providing valuable feedback for ongoing refinement. These use cases included coordination services, key-value stores, distributed file system metadata services, transaction processing engines for replicated databases, application-level firewalls, publish-subscribe middleware, and RADIUS-based authentication services.

The experience with BFT-SMART underscores the importance of ongoing maintenance and refinement in achieving robustness and high performance in Byzantine Fault-Tolerant systems.

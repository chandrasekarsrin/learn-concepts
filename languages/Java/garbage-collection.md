# Garbage collection

- Fast allocation
- efficient reclamation

# Strategy used by GC algorithms
- Tracing the object graph
- Stop the world or concurrent
- Generational collections

# Focus and tradeoffs of GC algorithms
- Throughput
- Latency
- Footprint (overhead)
It is often hard to optimise for all of this and we have to tradeoff between them.


# Supported collectors in java

Serial
- very low memory foot print.
- uses some small data structures in java heap.
- heap is divided into young and old generation. 
- it uses stop the world strategy. if we are using small containers then it is a better choice.
- more latency during gc
parallel
- throughput oriented
- good for batch like workloads.
- generational collections
- controllable latency
- suitable for long lived services.
- it was default collector until jdk8.
G1 (balanced)
- balance between latency and throughput
- region based. divides the heap into various regions. 
- its default collector since jdk9

ZGC
- low latency
- sub millisecond pauses
- region based
- fully concurrent collections (this is the main difference from G1)
- it will be available from jdk21.
- suitable for long lived services.


We need to have more memory than xmx in the container.




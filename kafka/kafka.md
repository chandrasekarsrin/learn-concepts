# kafka
# OCI Streaming service

- open-source distrubuted event streaming platform
- used for data pipelines, streaming analytics, data integration and mission critical applications.

# Features
- highly available(replication built-in)
- supports many consumers(publish/subscribe)
- gauranteed ordering within partitions


# Good practices for kafka consumers
- closing the consumer cleanly with finally including consumer.commitSync(currentOffsets); consumer.close()
    - called during shutdown hook when gracefully exiting or any other exception
- implement ConsumerRebalanceListener onPartitionsRevoked to commitSync(currentOffsets); to commit 
    - during rebalancing happens either adding new consumer to the group or removing consumer from the group or modifying partions in the topic, etc..
- add a shutdown hook and call consumer.wakeup() to exit/shutdown gracefully.
    - do this to complete processing of read records, commit offset and exit the application gracefully.

Reference to write good consumer code: https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/ch04.html


TOREAD:
https://www.confluent.io/blog/how-choose-number-topics-partitions-kafka-cluster/
https://docs.oracle.com/en-us/iaas/Content/Streaming/Tasks/streaming-quickstart-oci-sdk-for-java.htm
expose on how other applications have implemented
do a poc with vertx
https://confluence.oci.oraclecorp.com/pages/viewpage.action?spaceKey=DST&title=Streaming+Customers
https://developer.okta.com/blog/2022/09/15/kafka-microservices
https://github.com/apache/kafka/tree/trunk/examples/src/main/java/kafka/examples

https://www.confluent.io/blog/kafka-consumer-multi-threaded-messaging/
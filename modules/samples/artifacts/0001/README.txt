1. Copy {WSO2SPHome}/samples/artifacts/0001/kafka-sample.siddhi file to
{WSO2_SP_Home}/wso2/worker/deployment/siddhi-files/

Kafka libs to be added and converted to OSGI from {KafkaHome}/libs are as follows
    * kafka_2.10-0.9.0.1.jar
    * kafka-clients-0.9.0.1.jar
    * metrics-core-2.2.0.jar
    * scala-library-2.10.5.jar
    * zkclient-0.7.jar
    * zookeeper-3.4.6.jar

2. Add the OSGI converted kafka libs to {WSO2SPHome}/lib

3. Add the kafka libs to {WSO2SPHome}/samples/sample-clients/lib

4. Navigate to {KafkaHome} and start zookeeper node using bin/zookeeper-server-start.sh config/zookeeper.properties

5. Navigate to {KafkaHome} and start kafka server node using bin/kafka-server-start.sh config/server.properties

(step 6 and 7 is optional, since kafka consumer creates topic with partition if the topic is not available)

6. Navigate to {KafkaHome} and run bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic kafka_topic

7. Navigate to {KafkaHome} and run bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic kafka_result_topic

8. Navigate to {WSO2SPHome}/bin and start using ./worker.sh

9. Navigate to {WSO2SPHome}/samples/sample-clients/kafka-consumer and run ant command without arguments

10. Navigate to {WSO2SPHome}/samples/sample-clients/kafka-producer and run ant -Dbroker=localhost:9092 -DtopicName=kafka_topic -Dtype=xxxx -DsampleNo=0001 -DfileName=kafka_sample -DpartitionNo=0

Published values should be printed on the kafka-consumer console.

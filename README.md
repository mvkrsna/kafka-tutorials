# Kafka - Installing in Local and Running
The following was discovered as part of building this project:

* The original package name 'com.techbud.kafkatutorials.kafka-tutorials' is invalid and this project uses 'com.techbud.kafkatutorials.kafka_tutorials' instead.

# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Running Using Kraft configuration](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/3.5.7/maven-plugin)
* [Create an OCI image](https://docs.spring.io/spring-boot/3.5.7/maven-plugin/build-image.html)
* [Spring Web](https://docs.spring.io/spring-boot/3.5.7/reference/web/servlet.html)
* [Spring Boot DevTools](https://docs.spring.io/spring-boot/3.5.7/reference/using/devtools.html)

### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [Building REST services with Spring](https://spring.io/guides/tutorials/rest/)

### Maven Parent overrides

Due to Maven's design, elements are inherited from the parent POM to the project POM.
While most of the inheritance is fine, it also inherits unwanted elements like `<license>` and `<developers>` from the parent.
To prevent this, the project POM contains empty overrides for these elements.
If you manually switch to a different parent and actually want the inheritance, you need to remove those overrides.

## Open Source Kafka Startup in local ##

1. Start Zookeeper Server

   ```./bin/zookeeper-server-start.bat config/zookeeper.properties```

2. Start Kafka Server / Broker

   ```./bin/kafka-server-start.bat config/server.properties```

3. Create topic

   ```./bin/kafka-topics.bat --bootstrap-server localhost:9092 --create --topic NewTopic --partitions 3 --replication-factor 1```

4. list out all topic names

   ``` ./bin/kafka-topics.bat --bootstrap-server localhost:9092 --list ```

5. Describe topics

   ``` ./bin/kafka-topics.bat --bootstrap-server localhost:9092 --describe --topic NewTopic ```

6. Produce message

   ```./bin/kafka-console-producer.bat --broker-list localhost:9092 --topic NewTopic```


7. consume message

   ``` ./bin/kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic NewTopic --from-beginning ```


## Confluent Kafka Community Edition in local ##

1. Start Zookeeper Server

   ```bin/zookeeper-server-start etc/kafka/zookeeper.properties```

2. Start Kafka Server / Broker

   ```bin/kafka-server-start etc/kafka/server.properties```

3. Create topic

   ```bin/kafka-topics --bootstrap-server localhost:9092 --create --topic NewTopic1 --partitions 3 --replication-factor 1```

4. list out all topic names

   ``` bin/kafka-topics --bootstrap-server localhost:9092 --list ```

5. Describe topics

   ``` bin/kafka-topics --bootstrap-server localhost:9092 --describe --topic NewTopic1 ```

6. Produce message

   ```bin/kafka-console-producer --broker-list localhost:9092 --topic NewTopic1```


7. consume message

   ```bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic NewTopic1 --from-beginning ```

8. Send CSV File data to kafka

   ```bin/kafka-console-producer --broker-list localhost:9092 --topic NewTopic1 <bin/customers.csv```
   
   

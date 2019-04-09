1.  Create Topic

 1) 실행문

 [training@localhost ~]$ kafka-topics --create \
> --zookeeper localhost:2181 \
> --replication-factor 1 \
> --partitions 1 \
> --topic weblogs

 2) 결과
 Created topic "weblogs".

2. Display all Kafka topics
1)실행문
[training@localhost ~]$ kafka-topics --list \
> --zookeeper localhost:2181

2)결과
weblogs

3. Review the details of the weblogs topic
1)실행문
[training@localhost ~]$ kafka-topics --describe weblogs \
> --zookeeper localhost:2181

2)결과
Topic:weblogs	PartitionCount:1	ReplicationFactor:1	Configs:
	Topic: weblogs	Partition: 0	Leader: 0	Replicas: 0	Isr: 0

4. Start a Kafka producer for the weblogs topic
1)실행문(기존터미널)
[training@localhost ~]$ kafka-console-producer \
> --broker-list localhost:9092 \
> --topic weblogs
test weblog entry 1

2) Consumer 터미널 실행문
[training@localhost ~]$ kafka-console-consumer \
> --zookeeper localhost:2181 \
> --topic weblogs \
> --from-beginning

3) 결과( consumer  터미널)
test weblog entry 1

4) test weblog entry 2 입력 시  Consumer  터미널에도 test weblog entry 2가 시현됨

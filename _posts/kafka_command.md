# 카프카 명령어 모음

```
kafka-topics.sh --create --bootstrap-server 127.0.0.1:9092 --replication-factor 1 --partitions 1 --topic mytopic
kafka-topics.sh --list --bootstrap-server 127.0.0.1:9092
kafka-topics.sh --describe --bootstrap-server 127.0.0.1:9092 --topic mytopic

kafka-run-class.sh kafka.tools.GetOffsetShell --broker-list 127.0.0.1:9092 --topic mytopic

kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic mytopic --partition 0 --offset 0
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic mytopic --partition 0 --offset earliest
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic mytopic --from-beginning
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic mytopic --consumer-property group.id=my-consumer-group

kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092 -list
kafka-consumer-groups.sh --bootstrap-server 127.0.0.1:9092 -describe -group my-consumer-group

kafka-log-dirs.sh --describe --bootstrap-server 127.0.0.1:9092 --topic-list '???'

kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic mytopic
```

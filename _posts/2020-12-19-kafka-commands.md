

![截图](../img/2020-12-19-kafka-commands-img1.png)


## 常用命令

```

kafka-consumer-groups.sh \
--bootstrap-server 127.0.0.1:9092 \
--describe \
--group check_data


kafka-consumer-groups.sh \
--bootstrap-server 127.0.0.1:9092 \
--reset-offsets \
--execute \
--to-datetime 2020-10-15T02:00:00.000 \
--group check_data \
--topic demo


kafka-consumer-groups.sh \
--bootstrap-server 127.0.0.1:9092 \
--reset-offsets \
--execute \
--to-latest  \
--group check_data \
--topic demo


nohup kafka-console-consumer.sh \
--bootstrap-server 127.0.0.1:9092 \
--topic demo \
--property print.timestamp=true \
--consumer-property group.id=check_data \
--delete-consumer-offsets > demo.out 2>&1 &




nohup kafka-console-consumer.sh \
--bootstrap-server 127.0.0.1:9092 \
--topic demo \
--delete-consumer-offsets > demo.out 2>&1 &


```
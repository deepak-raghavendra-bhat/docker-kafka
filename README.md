docker compose -f docker-compose.yml up -d

docker exec -it kafka /bin/bash

#create topic
kaftopics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic demo_kafka_topic

kafka-topics.sh --list --zookeeper zookeeper:2181

#produce message

kafka-console-producer.sh --broker-list kafka:9092 --topic demo_kafka_topic
>{'user_id':1,'recipient_id':2,'message':'msg 1'}
>{'user_id':2,'recipient_id':1,'message':'msg 2'}

#consumer

kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic demo_kafka_topic

#list messages

kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic demo_kafka_topic --from-beginning

#python code steps



conda create --name kafka

conda activate kafka



conda install -c conda-forge kafka-python
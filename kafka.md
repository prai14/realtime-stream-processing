# realtime-stream-processing


#### 0. Install KAFKA
wget http://www-us.apache.org/dist/kafka/2.4.0/kafka_2.13-2.4.0.tgz

tar xzf kafka_2.13-2.4.0.tgz

sudo mv kafka_2.13-2.4.0 /usr/local/kafka


#### 1. Start Zookeeper
sudo bin/zookeeper-server-start.sh config/zookeeper.properties 

#### 2. Start kafka
sudo bin/kafka-server-start.sh config/server.properties 

sudo bin/kafka-server-start.sh /usr/local/kafka/config/server_3.properties 

sudo bin/kafka-server-start.sh /usr/local/kafka/config/server_2.properties 

sudo bin/kafka-server-start.sh /usr/local/kafka/config/server_1.properties  

#### 3. list of the active brokers 
bin/zookeeper-shell.sh localhost:2181 ls /brokers/ids

output:   [0, 1, 2, 3]

#### 4. list of the active brokers 
./bin/zookeeper-shell.sh localhost:2181 ls /brokers/topics

output: [__consumer_offsets, greek, greek_R3]

#### 5. describe kafka topics
sudo bin/kafka-topics.sh --describe --zookeeper localhost:2181 

sudo bin/kafka-run-class.sh kafka.admin.ConsumerGroupCommand --bootstrap-server localhost:9092 --group group_id --describe

#### 6. kafka manager
sudo ./kafka-manager -Dkafka-manager.zkhosts="localhost:2181" -Dconfig.file=cong/application.conf -Dhttp.port=8080


https://www.michael-noll.com/blog/2013/03/13/running-a-multi-broker-apache-kafka-cluster-on-a-single-node/

# Create the "zerg.hydra" topic
$ bin/kafka-topics.sh --zookeeper localhost:2181 \
    --create --topic zerg.hydra --partitions 3 --replication-factor 2
# List the available topics in the Kafka cluster
$ bin/kafka-topics.sh --zookeeper localhost:2181 --list

# List the available topics in the Kafka cluster
$ bin/kafka-topics.sh --zookeeper localhost:2181 --describe --topic zerg.hydra

# Start a console producer in sync mode
$ bin/kafka-console-producer.sh --broker-list localhost:9092,localhost:9093,localhost:9094 --sync \
    --topic zerg.hydra
    
# Start a console consumer
$ bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic zerg.hydra --from-beginning






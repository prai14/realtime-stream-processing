# realtime-stream-processing

#### 1. Start Zookeeper
sudo bin/zookeeper-server-start.sh config/zookeeper.properties 

#### 2. Start kafka
sudo bin/kafka-server-start.sh config/server.properties
sudo bin/kafka-server-start.sh /usr/local/kafka/config/server_3.properties 
sudo bin/kafka-server-start.sh /usr/local/kafka/config/server_2.properties
sudo bin/kafka-server-start.sh /usr/local/kafka/config/server_1.properties 

#### 3. list of the active brokers 
./bin/zookeeper-shell.sh localhost:2181 ls /brokers/ids

output:   [0, 1, 2, 3]

#### 4. list of the active brokers 
./bin/zookeeper-shell.sh localhost:2181 ls /brokers/topics

output: [__consumer_offsets, greek, greek_R3]

#### 5. describe kafka topics
sudo bin/kafka-topics.sh --describe --zookeeper localhost:2181 
sudo bin/kafka-run-class.sh kafka.admin.ConsumerGroupCommand --bootstrap-server localhost:9093 --group group_id --describe

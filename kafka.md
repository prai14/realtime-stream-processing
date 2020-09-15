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


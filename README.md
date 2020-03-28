simple deployment of Kafka in Kubernetes cluster that can be accessed from outside the Kubernetes cluster



# Testing Method
Execute from a host outside the Kubernet cluster  
Testing with kafkacat  
192.168.99.100 is the IP of the Kafka node hosting the pod. make sure that the correct broker ip and port is advertised externally
```
wouyang-mbp:edi wouyang$ kafkacat -b 192.168.99.100:32001 -L
Metadata for all topics (from broker 0: 192.168.99.100:32001/0):
 1 brokers:
  broker 0 at 192.168.99.100:32001 (controller)
 2 topics:
  topic "__consumer_offsets" with 50 partitions:
    partition 0, leader 0, replicas: 0, isrs: 0
    partition 1, leader 0, replicas: 0, isrs: 0
    partition 2, leader 0, replicas: 0, isrs: 0
```

Using Python
```
from kafka import KafkaProducer
producer = KafkaProducer(bootstrap_servers=['192.168.99.100:32001'])
data = b"hio"
producer.send('test', value=data)

from kafka import KafkaConsumer
consumer = KafkaConsumer(
    'test',
     auto_offset_reset='earliest',
     bootstrap_servers=['192.168.99.100:32001']
     )
for message in consumer:
    message = message.value
    print(message)

```

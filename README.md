# eventDrivenKubernetes

```
from kafka import KafkaConsumer
consumer = KafkaConsumer(
    'test',
     auto_offset_reset='earliest',
     bootstrap_servers=['kafka:9092']
     )
for message in consumer:
    message = message.value
print(message)
 
 
 
from kafka import KafkaConsumer
consumer = KafkaConsumer(
    'test',
     auto_offset_reset='earliest',
     bootstrap_servers=['100.123.34.0:9092']
     )
for message in consumer:
    message = message.value
    print(message)
 
 
from kafka import KafkaProducer
producer = KafkaProducer(bootstrap_servers=['100.123.34.0:9092'])
data = b"hifromcontainerA2"
producer.send('test', value=data)
 
 
 
from kafka import KafkaProducer
producer = KafkaProducer(bootstrap_servers=['172.18.0.3:9092'])
data = b"hio"
producer.send('test', value=data)
```

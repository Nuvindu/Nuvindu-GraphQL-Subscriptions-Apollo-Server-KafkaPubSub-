# GraphQL-Subscriptions-Apollo-Server-KafkaPubSub

</br>

### Server
</br>
Start a node package: 

```javascript
npm init -y
```

Install Dependencies:

```javascript
npm install
```

</br>

### Kafka Server

</br>

Use this [link](https://kafka.apache.org/) to install and configure the Kafka server.</br>
(Recommended Version: 2.8.0)

</br>

Run the Zookeeper Server:

</br>

Open a terminal and enter the Kafka directory. 
Run the following command.

Linux
```
bin/zookeeper-server-start.sh config/zookeeper.properties
```

Windows
```
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```
</br>


Run the Kafka Server:

</br>

Open another terminal and enter the Kafka directory.
Run the following command.

Linux
```
bin/kafka-server-start.sh config/server.properties
```

Windows
```
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

</br>

### Testing GraphQL Subscriptions

</br>
Open a GraphQL IDE and set the url as http://localhost:4000/graphql

</br>

Run a Subscription

```
subscription receive {
  receiveMessage{
    id
    name
    content
  }
}
```


Run a Mutation
</br>

```graphql
mutation send($params: DataInput) {
  sendMessage(params: $params) {
    id
    name
    content
  }
}
```
Add the following to the query variables

```
{
  "params": {"name": "User", "content": "Hello"}
}
```

After running a mutation you should see the new data has been received by the subscription request 
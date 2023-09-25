Topic is a type of [[Communication in ROS]], 
![[Pasted image 20230924152909.png]]


A node may publish data to any number of topics, and at the same time have subscriptions to any number of topics.


## rqt_graph
Type this in terminal to start
```
rqt_graph
```


## Important CLI command

```
ros2 topic list
ros2 topic list -t #return the list with the topic type, which is the message type the topic accepts



```


```
ros2 topic echo <topic_name> 
```
this command creates a node that subscribes to the topic, and output the messages from that topic in terminal, you can check this node in rqt_graph



```
ros2 topic info <topic_name>

#sample return
Type: geometry_msgs/msg/Twist
Publisher count: 1
Subscription count: 2



```
### interface show

if a topic have a message type, say: `geometry_msgs/msg/Twist`, we can use the command:
```
ros2 interface show <msg type>
```
it will show the structure of data the message expects.


#### topic pub
```
ros2 topic pub <topic_name> <msg_type> '<args>'


ros2 topic pub --once /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.8}}"
# here we using --once to specify frequency, use --rate <number> to specify other frequencies.

```
This command will send data to a topic, and its subscribers will then receive the data from the topic.

#### topic hz

This command shows a frequency of messages sent to topic in terminal.
```
ros2 topic hz <topic_name>


```
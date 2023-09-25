![[Pasted image 20230923235332.png]]



## Nodes
Each node in ROS should be responsible for a single, module purpose(e.g one node for controlling wheel motors, one node for controlling a laser ranger-finder)
Each node can send and receive data to other nodes via topics, services actions, or parameters

```
ros2 run <package_name> <executable_name>
ros2 node list
ros2 node info <node_name>

```


## Topics
ROS2 breaks complex systems down into modular nodes. Topics are like a bus for nodes to exchange messages
- A node 

```
rqt_graph #shows graph
ros2 topic list 
ros2 topic list -t
ros2 topic echo <topic_name>
ros2 topic info <topic_name>
ros2 interface show <msg_type>
ros2 topic pub <topic_name> <msg_type> '<args>'
ros2 topic hz <topic_name>
```

## Services
another method of communication for nodes. Based on a call-and-response model

```
ros2 service list
ros2 service type <service_name>
ros2 service list -t
ros2 service find <type_name>
ros2 interface show <type_name>.srv
ros2 service call <service_name> <service_type> <arguments>
```

## Actions
consist of goal, feedback and a result
It is built on top of [[services]] and [[topics]], different from services, you can cancel them while executing.
Also provides steady feedback, unlike services which return a single response

uses client-server model. Action client sends a **goal** to an action server, server returns a stream of feedback and a result.


## Parameters
configuration for nodes.
https://roboticsbackend.com/ros2-yaml-params/


## Workspace
a workspace is a directory containing ROS2 packages.
```
#creating new workspace
mkdir -p <workspace_name>/src

#resolving dependencies
cd <workspace>
rosdep install -i --from-path src --rosdistro foxy -y
```

### colcon

```
colcon build 
#parameters
--packages-up-to:builds package you wnat, plus all its dependencies. but not the whole workspace, saves time if you don't need all the packages in the workspace
--symlink-install
saves you from having to rebuild every time you weak python scripts
--event-handlers console_direct+ 
shows console output while building



install directory after build finish is the workspace's setup file. 



```


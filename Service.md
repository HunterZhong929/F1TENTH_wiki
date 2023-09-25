
- based on call-and-response model, different from publisher-subscriber model that [[Topics]] uses. Meaning service only provide data when they are being called by client.
- ![[Pasted image 20230924154153.png]]

## Commands

```
ros2 service list
ros2 service type <service_name>
ros2 service list -t 
#show the service lsit with message type
ros2 service find <type_name>
#find all service with the message type

ros2 interface show <type_name>.srv
#return a format of both call and response message of a service 

ros2 service call <service_name> <service_type> <arguments>
#make a call to a service, the <arguments> needs to be in yaml format
```

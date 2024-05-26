"Request / reply is done via a _Service,_ which is defined by a pair of [messages](http://wiki.ros.org/Messages): one for the request and one for the reply"
[doc](http://wiki.ros.org/Services), [msg and srv file guide](http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv), [writing service guide](http://wiki.ros.org/ROS/Tutorials/WritingServiceClient%28python%29)
### .srv file
[doc](http://wiki.ros.org/srv)
example:
```
int64 A
int64 B
---
int64 Sum
```
### [rosservice](http://wiki.ros.org/rosservice)
Command-line tool for listing and querying ROS [Services](http://wiki.ros.org/Services).
### rossrv
show service description: `rossrv show <service type>`
### call
`call` command will call a service of a node
to check a service type structure use [[#rossrv]]: `rossrv info turtlesim/Spawn`
```sh
float32 x
float32 y
float32 theta
string name
---
string name
```
the first part is the request and the second part is the response.
To send this request use: `rosservice call /spawn 7 7 0 t2`, the `7 7 0 t2` are parameters to this service:`x y theta name`.

"[Nodes](http://wiki.ros.org/Nodes) ([[Technology/Robotics/ROS/Graph/Node]]) communicate with each other by publishing **messages** to [topics](http://wiki.ros.org/Topics) ([[Topic]])"
[doc](http://wiki.ros.org/Messages), [msg and srv file guide](http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv)

### .msg file
[doc](http://wiki.ros.org/Messages)
example:
```
  Header header
  string child_frame_id
  geometry_msgs/PoseWithCovariance pose
  geometry_msgs/TwistWithCovariance twist
```
## rosmsg
Example:
`rosmsg show beginner_tutorials/Num` or `rosmsg show Num` - this will show the `Num` messages from all packages.
To see all available `std_msgs` for example, type: `rosmsg show std_msgs/` and double tap auto-completion key (usually Tab):
![[std_msgs.png]]

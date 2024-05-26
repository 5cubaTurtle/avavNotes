"rospy is a pure Python client library for ROS."
[doc](http://wiki.ros.org/rospy), [tutorial](http://wiki.ros.org/rospy/Tutorials)

import: `import rospy`
## ROS objects
- [[Publisher]]
- [[Subscriber]]
- [[Rate]]
## functions
### init_node
Initialize a node to tell rospy the name of the node. Until then, rospy cannot start communicating the the ROS [[Master]].
```python
 rospy.init_node('talker', anonymous=True)
```
>NOTE: the name must be a [base name](http://wiki.ros.org/Names), i.e. it cannot contain any slashes."/".

 In ROS, nodes are uniquely named. If two nodes with the same name are launched, the previous one is kicked off. The `anonymous = True` ensures that your node has a unique name by adding random numbers to the end of NAME. For example, a possible node name that could be generated is "*talker_72222_1693227895388*". Refer to [Initialization and Shutdown - Initializing your ROS Node](http://wiki.ros.org/rospy/Overview/Initialization%20and%20Shutdown#Initializing_your_ROS_Node) in the rospy documentation for more information about node initialization options.
### is_shutdown()
returns a boolean whether the node received a termination signal.
### loginfo
```python
rospy.loginfo(log_msg)
```
`rospy.loginfo(str)` performs triple-duty: the messages get printed to screen, it gets written to the Node's log file, and it gets written to [[rosout]].
### spin
`rospy.spin()` simply keeps python from exiting until this node is stopped. Unlike [[roscpp]], `rospy.spin()` does not affect the subscriber callback functions, as those have their own threads.

## built-ins
### message types
`std_msgs.msg.String` is a very simple message type, so you may be wondering what it looks like to publish more complicated types. The general rule of thumb is that _constructor args are in the same order as in the .msg file_. You can also pass in no arguments and initialize the fields directly, e.g.
```python
msg = String()
msg.data = str
```
or you can initialize some of the fields and leave the rest with default values:
`String(data=str)`

### exceptions
- *rospy.ROSInterruptException* - the `rospy.ROSInterruptException` exception can be thrown by `rospy.sleep()` and [[Rate|rospy.Rate.sleep()]] methods when Ctrl-C is pressed or your Node is otherwise shutdown. The reason this exception is raised is so that you don't accidentally continue executing code after the *sleep()*.
 
[doc](http://wiki.ros.org/ROS/EnvironmentVariables)
"There are many environment variables that you can set to affect the behavior of ROS. Of these, the most important to understand are *ROS_MASTER_URI*, *ROS_ROOT*, and *ROS_PACKAGE_PATH* as they are commonly used in the system and frequently mentioned in documentation."

- [ROS_PACKAGE_PATH](http://wiki.ros.org/ROS/EnvironmentVariables#ROS_PACKAGE_PATH) should contain a list of directories where you have ROS packages separated by colons
	- With the introduction of catkin, the need to manually update *ROS_PACKAGE_PATH* becomes obsolete.
	- Note that each entry in *ROS_PACKAGE_PATH* is searched recursively--all ROS packages below the named path will be found.
- [ROS_ROOT](http://wiki.ros.org/ROS/EnvironmentVariables#ROS_ROOT) sets the location where the ROS core packages are installed.
- [ROS_MASTER_URI](http://wiki.ros.org/ROS/EnvironmentVariables#ROS_MASTER_URI) is a required setting that tells nodes where they can locate the master. It should be set to the XML-RPC URI of the master.
- [ROS_NAMESPACE](http://wiki.ros.org/ROS/EnvironmentVariables#ROS_NAMESPACE). Parameter names that are not globally specified are resolved with respect to ROS_NAMESPACE. For example, setting this parameter to */some/name/space*  and then starting a node, will set all the nodes parameters with the prefix */some/name/space*:
	```sh
	$ export ROS_NAMESPACE=/some/name/space
	$ rosrun turtlesim turtlesim_node
	[ INFO] [1692699747.157517568]: Starting turtlesim with node name /some/name/space/turtlesim
	```
	Notice that the new namespace of the node. All the parameters of the node also changed to this namespace.

Launch files are of the format .launch and use a specific [XML format](http://wiki.ros.org/roslaunch/XML). They can be placed anywhere within a package directory, but it is common to make a directory named “Launch” inside the workspace directory to organize all your launch files.

## xml format
- [node](http://wiki.ros.org/roslaunch/XML/node)`<node pkg="turtlesim" type="turtlesim_node" name="avas_node"/>` - start a node; from the package `turtlsim`, the node `turtlesim_node` and call it `avas_node`.
	- `output="screen"` adding this flag will redirect the nodes output to the terminal from which this launch file is launched.
	 - `args="--test"` provide an argument to the node (`--test` in this case).
	 - `respawn="true"` respawn the node if it dies.
-  [include](http://wiki.ros.org/roslaunch/XML/include): `<include file="$(find play_pkg)/playingaround.launch"/>` - to launch another launch file.
- [arg](http://wiki.ros.org/roslaunch/XML/arg)`<arg name="sim_name" default="avas_turtle"/>` -  An arg is used to pass to a launch file. This example defines an argument named `sim_name` with the default value of `avas_turtle`. If a default value is not provided, the argument must be passed to this launch file from either the command line or from inclusion from other launch file.
	- Passing an argument via the command-line: `roslaunch <package> launchfile.launch hoge:=some_value`
	- Passing an argument to an include tag:
	```xml
	<include file="included.launch">
	  <!-- all vars that included.launch requires must be set -->
	  <arg name="hoge" value="fuga" />
	</include>
	```
- [param](http://wiki.ros.org/roslaunch/XML/param) - parameter of a launch file or a node.
- [remap](http://wiki.ros.org/roslaunch/XML/remap):
	```xml
	<node pkg="turtlesim" type="turtle_teleop_key" name="$(arg ctrl_name)">
        <remap from="/turtle1/cmd_vel" to="$(arg vel_topic)"/>
    </node>
	```
	 The remap tag will force the node to publish to `vel_topic` arg instead of */turtle1/cmd_vel* topic.
- [group](http://wiki.ros.org/roslaunch/XML/group)`<group ns="namespace">` - create an isolated namespace for a node.
	```xml
	<group ns="turtlesim1" if="$(arg show_sim)">
	   <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
    </group>
	```
	This allows having several nodes with the same name as long as their group-namespace is different. The `if=..` attribute conditions the execution of the group on the value of the argument `show_sim`, i.e. the group will only execute if `show_sim` is *true* or *1*.

## roslaunch
`roslaunch` starts nodes as defined in a launch file.
Links: [doc](http://wiki.ros.org/roslaunch), [wiki guide](http://wiki.ros.org/ROS/Tutorials/UsingRqtconsoleRoslaunch#Using_roslaunch), [introduction pdf](https://jokane.net/agitr/agitr-small-launch.pdf), [clearpath guide](http://www.clearpathrobotics.com/assets/guides/melodic/ros/Launch%20Files.html)
Usage: `roslaunch [package] [filename.launch]`

## Info from chatGPT:
A `.launch` file is an XML-based configuration file used to launch and manage a collection of ROS nodes. It is a central component of the ROS launch system, which simplifies the process of starting and configuring multiple nodes that need to work together to accomplish a specific task.

A `.launch` file contains a set of instructions that define the nodes to be launched, the node parameters, remappings, and other configuration settings. It allows you to specify the order in which nodes should be launched, establish communication between nodes, and configure various ROS settings.

Here are some key elements that can be included in a `.launch` file:
1. **Node Definition:** You can define multiple nodes within a `.launch` file. Each node definition specifies the name of the node, the ROS package it belongs to, the node's executable or plugin name, and any required arguments or parameters.
2. **Node Parameters:** You can set parameters for each node, providing values that control its behavior. Parameters can be static or dynamically reconfigurable, allowing you to adjust them during runtime.
3. **Remapping:** Remapping enables you to redirect the input and output topics of nodes. It allows you to connect nodes that expect different topic names or remap topic namespaces, simplifying the integration of different components.
4. **Include Files:** `.launch` files can include other `.launch` files, allowing for modular configuration and reuse of launch configurations.
5. **Arguments:** You can define arguments in a `.launch` file, which provide a way to parameterize the launch file and make it more flexible. Arguments can be set when launching the file, either through command-line arguments or through the ROS parameter server.

Once a `.launch` file is created, it can be executed using the `roslaunch` command-line tool. The `roslaunch` command reads the `.launch` file and starts the specified nodes with the defined configurations. It also provides options for managing the launch, such as automatically restarting nodes if they crash and logging output to files.

## use
To use a `.launch` file in ROS, you need to follow these steps:
1. **Create or locate the `.launch` file:** Start by creating a `.launch` file or finding an existing one that suits your needs. The file should have a `.launch` extension and be written in XML format.
2. **Edit the `.launch` file:** Open the `.launch` file in a text editor and modify it according to your requirements. Specify the nodes to be launched, their parameters, remappings, and any other necessary configurations.
3. **Launch the file using roslaunch:** Open a terminal and use the `roslaunch` command to launch the `.launch` file. The basic syntax is as follows:
```sh
roslaunch package_name file_name.launch
```
Replace `package_name` with the name of the ROS package containing the `.launch` file, and `file_name.launch` with the actual name of the `.launch` file.
4. **Specify launch arguments (optional):** If your `.launch` file has defined arguments, you can pass values to them while launching. For example:
```sh
roslaunch package_name file_name.launch arg1:=value1 arg2:=value2
```
Replace `arg1` and `arg2` with the argument names defined in the `.launch` file, and `value1` and `value2` with the desired values.
5. **Observe the output:** Once launched, the nodes specified in the `.launch` file will start executing, and their output will be displayed in the terminal. You can monitor the output and check for any errors or warnings.
6. **Terminate the launch:** To stop the execution of the launched nodes, press `Ctrl+C` in the terminal where the `roslaunch` command was executed.

By using a `.launch` file, you can conveniently start and manage multiple nodes with their respective configurations and interconnections. It allows for easy launching of complex robot systems and promotes modularity and reusability in ROS application development.
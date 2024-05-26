[doc](http://wiki.ros.org/rosbash)
Assorted shell commands for using ros with bash.
For rsbash to work source the *setup.bash* file.
For example: `source /opt/ros/noetic/setup.bash`

rosbash includes the following command line utilities:
- [roscd](http://wiki.ros.org/rosbash#roscd) - change directory starting with package, stack, or location name
- [rospd](http://wiki.ros.org/rosbash#rospd) - pushd equivalent of roscd
- [rosd](http://wiki.ros.org/rosbash#rosd) - lists directories in the directory-stack
- [rosls](http://wiki.ros.org/rosbash#rosls) - list files of a ros package
- [rosed](http://wiki.ros.org/rosbash#rosed) - edit a file in a package
- [roscp](http://wiki.ros.org/rosbash#roscp) - copy a file from a package
- [rosrun](http://wiki.ros.org/rosbash#rosrun) - run executables of a ros package
#### [roscd](http://wiki.ros.org/rosbash#roscd)
`roscd` allows you to change directories using a package name, stack name, or special location.
`roscd <package-or-stack>[/subdir]`
example `roscd core_autonomy`

change directory to ROS log files: `roscd log`
#### [rosls](http://wiki.ros.org/rosbash#rosls)
`rosls` allows you to view the contents of a package, stack, or location.
example: `rosls roscpp`

#### roscp
syntax: `roscp [package_name] [file_to_copy_path] [copy_path]`
#### rosrun
`rosrun` allows you to run an executable in an arbitrary package.
`rosrun <package> <executable>`
example: `rosrun roscpp_tutorials talker`
It's also possible to pass a \_parameter using the following syntax:
`rosrun package node _parameter:=value`
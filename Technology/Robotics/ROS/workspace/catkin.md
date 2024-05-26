Low-level build system macros and infrastructure for ROS
[doc](http://wiki.ros.org/catkin)
create package: `catkin_create_pkg <package-name> <dependencies>`
- `<dependencies>` is a space separated list.
To build packages (invokes cmake and make):  `catkin_make`
- `catkin_make` also creates the workspace layout
>To add the workspace to your ROS environment you need to source the generated setup file: `. ~/catkin_ws/devel/setup.bash`.
- Or use `catkin build` which also builds the catkin workspace.
	- `catkin build` makes (compiles) a ROS package in an isolated manner while maintaining efficiency due to parallelization
>To build the package [[cd]] to root workspace.

## What makes up a catkin Package?
For a package to be considered a catkin package it must meet a few requirements:
- The package must contain a [catkin compliant package.xml](http://wiki.ros.org/catkin/package.xml) file.
    - That package.xml file provides meta information about the package.
- The package must contain a [CMakeLists.txt which uses catkin](http://wiki.ros.org/catkin/CMakeLists.txt).
    - If it is a [catkin metapackage](http://wiki.ros.org/catkin/package.xml#Metapackages) it must have the relevant boilerplate CMakeLists.txt file.
- Each package must have its own folder
    - This means no nested packages nor multiple packages sharing the same directory.
	
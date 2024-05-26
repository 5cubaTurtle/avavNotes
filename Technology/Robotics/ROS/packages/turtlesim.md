Basic robot simulator

Start a sim node: `rosrun turtlesim turtlesim_node`. This will display the simulator window.
-  adding the flag `__name:=avas_turtle` to the command will name the node *avas_turtle*. 

Control the sim via keyboard: `rosrun turtlesim turtle_teleop_key`. This will start a node called */teleop_turtle* which will allow to send speed commands to the *turtlesim_node* using the keyboard.
rosbag is a package for recording and playing back ROS message data. It enables you to capture data published on ROS topics during runtime and save it to a file. Later, you can play back the recorded data to analyze or replay experiments.

To use rosbag, you can start recording by running the `rosbag record` command, specifying the topics you want to record. The recorded bag file can then be played back using the `rosbag play` command, allowing you to visualize or analyze the data.

`rosbag -h`
record rosbag: `rosbag record /fix -O fix_stationary`
- `/fix` - [[Topic|rostopic]]
- `-O fix_stationary` - output file name

play rosbag: `rosbag play sigPrediction1.bag --pause -s 83.1`
- *sigPrediction1.bag* is the rosbag file name
- `--pause` will start the play-through in pause
- `-s 83.1` will start the play-through at the 83.1sth second
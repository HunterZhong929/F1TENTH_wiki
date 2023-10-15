
Open a new terminal. Make the following directories:
```bash
	mkdir workspace_name
	cd workspace_name
	mkdir src
```
Now, making sure you are in workspace_name/src, to make your package:
```bash
	catkin_create_pkg package_name std_msgs rospy roscpp
	cd workspace_name
	catkin_make
```
To add the workspace to your ROS environment you need to source the generated setup file. This needs to be done in every new terminal opened
```bash
	source devel/setup.bash
	source /opt/ros/melodic/setup.bash
```

Note1: Any scripts/nodes that you create are placed into your package folder.
```bash
	cd ~/catkin_ws/package_name
```
Note2: Catkin workspaces do not come with the F1Tenth simulator installed. You must follow the "F1Tenth Simulator Install" instructions to get it running.

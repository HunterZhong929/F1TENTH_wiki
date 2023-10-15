### Dependencies
You will need the following dependences:

> - tf2_geometry_msgs
>     
> - ackermann_msgs
>     
> - joy
>     
> - map_server
>     

Install them using
```bash
	sudo apt-get install ros-melodic-tf2-geometry-msgs ros-melodic-ackermann-msgs ros-melodic-joy ros-melodic-map-server
```
The full list of dependencies can be found in the `package.xml` file.

## Package
To install the simulator package, clone the simulator repository into your catkin workspace:
```bash
	cd ~/catkin_ws/src
	git clone https://github.com/f1tenth/f1tenth_simulator.git
```
Then run catkin_make to build it:
```bash
	cd ~/workspace_name
	catkin_make
	source devel/setup.bash
```
To run the simulator on its own, run:
```bash
	roslaunch f1tenth_simulator simulator.launch
```

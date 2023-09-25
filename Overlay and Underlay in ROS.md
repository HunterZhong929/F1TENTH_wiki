

https://www.hadabot.com/learn-ros2-intro-nodes.html?step=ros2-underlay-overlay
```
#commands for starting up the sim, you should be in the sim_ws when using the command

source /opt/ros/foxy/setup.bash
source install/local_setup.bash
ros2 launch f1tenth_gym_ros gym_bridge_launch.py
```

## Why the source command?

When you "source" something in bash, it will execute each line of the file as is it were typed into the current shell. This is contrasted to actually executing the script, which will be run in a new shell.

The setup.bash file is merely adding environment variables to your path to allow ROS to function.

You can add the `source setup.bash` command to your ~/.bashrc file, so that it will be executed every time that you open a new shell.

Your third sequence shows you first using a local workspace, which is overlaying the system indigo installation. When you source the `/opt/ros/indigo/setup.bash` file, you are no longer using the local workspace, but rather only the system installation, which is why the local workspace variables are no longer available.

You should always source your local workspace setup last.


## Overlay
**Overlay:** The overlay, in the context of the `source` command, refers to the fact that when you use `source` to execute a script, it runs within the current shell environment. This means that any changes to environment variables, functions, or other settings made within the script will affect the current shell session. It's as if the script's contents are overlaid onto your current shell.

For example, if you have a script that sets an environment variable `MY_VARIABLE` to a certain value, running `source script.sh` will make `MY_VARIABLE` available in your current shell session with the value set in `script.sh`.

## Underlay


To write the nodes, first change the directory into the one that is in your catkin workspace. Then, you can make a directory to store your scripts.
```bash
	mkdir scripts
	cd scripts
```
Once you have your script, it needs to be made executable.
```bash
	chmod +x script_name.py
```
Add the following to your CMakeLists.txt. This makes sure the python script gets installed properly, and uses the right python interpreter.
```
	catkin_install_python(PROGRAMS scripts/script_name.py
	  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
	)
```
Then go to your catkin workspace and run:
```bash
	cd ~/catkin_ws
	catkin_make
```
Make sure roscore is running in a separate terminal
```bash
	roscore
```
If you have not done so already, source your files. Then, to run a script:
```bash
	rosrun package_name script_name.py
```
Note: For C++ scripts, everything is basically the same except you omit '.py' from the script names. 
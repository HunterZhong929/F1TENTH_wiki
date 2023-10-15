https://wiki.ros.org/msg
### In the `Package.xml` file

The ROS [Client Libraries](https://wiki.ros.org/Client%20Libraries) implement message generators that translate .msg files into source code. These message generators must be invoked from your build script.

Note that at build time, we need "message_generation", while at runtime, we only need "message_runtime".

Use 'build_depend' for packages you need at compile time:
```
	<build_depend>message_generation</build_depend>
```
Use 'exec_depend' for packages you need at runtime
```
	<exec_depend>message_runtime</exec_depend>
```

### In the `CMakeLists.txt` file found in your package

Uncomment/add the following line:
```
	catkin_python_setup()
```
Add the message_generation dependency to the find package call.
```
	find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs   message_generation)
```
Generate messages in the 'msg' folder.
```
	add_message_files(
	  FILES
	  name_of_file.msg
	)
```
Generate added messages and services with any dependencies listed here
```
	generate_messages(
	  DEPENDENCIES
	  std_msgs # Or other packages containing msgs
	)
```

The 'catkin_package' macro generates cmake config files for your package
Declare things to be passed to dependent projects
INCLUDE_DIRS: uncomment this if your package contains header files
LIBRARIES: libraries you create in this project that dependent projects also need
CATKIN_DEPENDS: 'catkin_packages' dependent projects also need
DEPENDS: system dependencies of this project that dependent projects also need
Make sure you export the message runtime dependency (the uncommented one)
```
	catkin_package(
     #INCLUDE_DIRS include
     #LIBRARIES lejun_jiang_roslab
     CATKIN_DEPENDS roscpp rospy std_msgs message_runtime
     #DEPENDS system_lib
	)
```
Specify additional locations of header files
Your package locations should be listed before other locations
```
	include_directories(
	 #include
	 ${catkin_INCLUDE_DIRS}
	)
```
Mark executable scripts (Python etc.) for installation. In contrast to 'setup.py', you can choose the destination.
```
	catkin_install_python(PROGRAMS
	 scripts/my_node.py
	 DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
	 )
```


### In a 'msg' folder within your package

Generate a '.msg' file. It will look like this:
```
	Header header
	fieldtype1 fieldname1
	fieldtype2 fieldname2
	fieldtype3 fieldname3
```

### In a 'launch' folder within your package

You can generate a '.launch' file that you will call to launch all necessary nodes.
```
<launch>
    <node pkg="package_name" type="python_script.py" name="any_name" output="screen">
        
    </node>
</launch>
```

### In your 'scripts' folder, make a `setup.py` script
```python
#!/usr/bin/env python
from distutils.core import setup
from catkin_pkg.python_setup import generate_distutils_setup

setup_args = generate_distutils_setup(
packages=['package_name'],
package_dir={'': 'src'}
#scripts=['scripts/my_scan_node.py']
)
setup(**setup_args)

```

Lastly, execute the 'catkin_make' command in the console and GL debugging




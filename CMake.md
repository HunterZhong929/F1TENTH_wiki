# What is CMake

A generator of build systems. 
- multiplatform
- it generates necessary file for build to work on different platform. For linux it generates a Makefile, in windows the file for the VisualStudio

## Difference btw CMake and Makefile
Makefile is a build system. Drives compiler and other build tools to build your code.

CMake generates such build system, and can be platform-independent.


## Usage in ROS

### step by step guide of creating a package

1. under your `workspace` folder:
```
colcon build
```
2. your folder now should look like this:
```
build  install  log  src

```
3. go to `<workspace>/src`, 
```
ros2 pkg create <package_name> --dependencies <dependencies name>

```
4. go to the package src folder `<workspace>/src/<package>/src`:
This is where your cpp or python file for this package should be.
Create those file using any code editor you like

5. go to package folder:
Do necessary editing on `CMakeLists.txt`

6. in `~/<workspace>` run `colcon build`
7. In another window, after sourcing `source ~/<workspace>/install/setup.bash`, run:
`ros2 run <pacakge_name> <excutable_name>`
The `<executable_name>` should be defined in your `CMakeLists.txt`


```CMake
add_executable(vision_node src/vision_node.cpp)
ament_target_dependencies(vision_node rclcpp)
```



## Ament CMake
A build system to enhance CMake for ROS2
#### Reference
https://docs.ros.org/en/foxy/How-To-Guides/Ament-CMake-Documentation.html

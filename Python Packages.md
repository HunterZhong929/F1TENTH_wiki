

## Steps 


#### 1 After creating workspace, create python package using this command in `<workspace>/src`


`ros2 pkg create --build-type ament_python lab1_pkg --dependencies ackermann_msgs
`
--build-type:
--dependencies:

**note**: it is important to specify the build type because the structure of a python package and cpp package is different.

#### 2 add python file in `<workspace>/src/<pkg_name>/<pkg_name>`

#### 3 change package.xml and setup.py

**Sample setup.py**


```python
from setuptools import setup

package_name = 'lab1_pkg'

setup(
    name=package_name,
    version='0.0.0',
    packages=[package_name],
    data_files=[
        ('share/ament_index/resource_index/packages',
            ['resource/' + package_name]),
        ('share/' + package_name, ['package.xml']),
    ],
    install_requires=['setuptools'],
    zip_safe=True,
    maintainer='hunterz',
    maintainer_email='hunterz@todo.todo',
    description='TODO: Package description',
    license='TODO: License declaration',
    tests_require=['pytest'],
    entry_points={
        'console_scripts': [
            'talker = lab1_pkg.talker:main',
        ],
    },
)
```

	
	
in `entry_points` the console_scripts field is where we need to change,
`"<excutable name> = <pkg_name>.<python_file name>:main"`

**Sample package.xml**

```xml
<?xml version="1.0"?>
<?xml-model href="http://download.ros.org/schema/package_format3.xsd" schematypens="http://www.w3.org/2001/XMLSchema"?>
<package format="3">
  <name>lab1_pkg</name>
  <version>0.0.0</version>
  <description>TODO: Package description</description>
  <maintainer email="hunterz@todo.todo">hunterz</maintainer>
  <license>TODO: License declaration</license>

  <depend>ackermann_msgs</depend>
  <exec_depend>rclpy</exec_depend>
  <exec_depend>std_msgs</exec_depend>
  <test_depend>ament_copyright</test_depend>
  <test_depend>ament_flake8</test_depend>
  <test_depend>ament_pep257</test_depend>
  <test_depend>python3-pytest</test_depend>

  <export>
    <build_type>ament_python</build_type>
  </export>
</package>

```

For now,just focus on adding the imported library to the <exec_depend> tag

#### 4 build the workspace in `~/<workspace>`
`colcon build`

#### 5 running the node

In a new terminal source:
`source /opt/ros/foxy/setup.bash`
`source ~/<workspace>/install/local_setup.bash`

then run:`ros2 run <pkg_name> <excutable_name>`



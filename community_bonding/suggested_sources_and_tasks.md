## Community Bonding period (May 17 - June 7, 2021)

### 1. Get familiar with JdeRobot Robotics Academy
 - Most of the code related to the exercises are available in [Robotics Academy repo](https://github.com/JdeRobot/RoboticsAcademy). Briefly go through the structure of this repo can help you to understand the structure of the Jderobot Robotics Academy and find necessary references.
 - Take a look at the [Academy forum](https://forum.jderobot.org/c/english/10/none) and the developer Slack channel time to time
 - Check available exercises and play with them, especially those that are updated to v2.3.

### 2. Get familiar with Industrial Robot exercises
There are three available exercises: pick and place, machine vision, and mobile manipulation. 
 - **MoveIt**: Each of them has its own dependencies, but MoveIt is necessary for all of them. There are less documents about python API of MoveIt. [Here](http://docs.ros.org/en/melodic/api/moveit_commander/html/classmoveit__commander_1_1move__group_1_1MoveGroupCommander.html) is a list of python API that can be used as reference. MoveIT official tutorial also contents a few introduction of [python interface](http://docs.ros.org/en/melodic/api/moveit_tutorials/html/doc/move_group_python_interface/move_group_python_interface_tutorial.html).

 - **PCL**: The second exercises uses [PCL](https://pcl.readthedocs.io/projects/tutorials/en/latest/). Current implementation is based on C++. We can migrate it to python in this year to make it easier to maintain. There are a few python bindings now, such as [python-pcl](https://strawlab.github.io/python-pcl/) and [pclpy](https://pypi.org/project/pclpy/). You can make some test to check whether the binding can work properly and provided necessary color and shape filter functions.
 
 - **Navigation stack**: The third uses [navigation stack](http://wiki.ros.org/navigation) in ROS based on the [simulation package from Neobotix](https://docs.neobotix.de/display/ROSSim/ROS-Simulation). If you are still not familiar with the ROS navigation stack, it would be easier to get started with the ROS tutorial.

 - **Grasp fix plugin**: Currently, [grasp fix plugin](https://github.com/jenniferBuehler/gazebo-pkgs/wiki/The-Gazebo-grasp-fix-plugin) is used in Gazebo to make sure the object can be fixed with the gripper when the robot arm is moving. Understanding how does the plugin work can help with improving the grasping performance, but it is not the core requirement.You can take a look at it later when we are moving to the performance improvement step.

### 3. Get familiar with the Web template and Docker
 - There are already nine web-template based exercises. They can be used as a reference to develop industrial robot exercises. The related code can be found in [the exercises folder of Robotics Academy repo](https://github.com/JdeRobot/RoboticsAcademy/tree/master/exercises). 
 - Here is a tutorial of [Docker](https://docs.docker.com/get-started/). After getting a brief understanding of docker, it should be helpful to take a look at the structure of [RADI](https://hub.docker.com/r/jderobot/robotics-academy)  (Robotics Academy Docker Image). 

After going through these contents, you should have a rough idea of how they work. Here are two suggested goals you can consider to sharpen your understanding and get started the development of the project.

(1) Migrate industrial robot repo to current Robotics Academy Docker image and test how it works
(Understand how to work with docker; )

(2) Build a web-template exercise with the robot arm in the first exercise and add a few button to start and stop its movement
(Understand how to use the webtemplate)

### 4. Test web-based Rviz

Rviz is necessary in the second exercise to show the octomap built with the point cloud. [RVizWeb](https://github.com/osrf/rvizweb) provides necessary components to build a web application similar to RViz. Make a test to check how it works.
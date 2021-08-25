---
layout: post
title: GSoC'21 Summary
subtitle: Final Evaluation
categories: [coding period]
tags: Evaluation
---

[Robotics-Academy](https://jderobot.github.io/RoboticsAcademy/) is an open source collection of exercises and challenges to learn robotics in a practical way. There are exercises about drone programming, about computer vision, about mobile robots, about autonomous cars, etc. It is mainly based on Gazebo simulator and ROS. 

The main goal of this project was to migrate three industrial robots exercises(i.e. Pick & Place, Machine Vision and Mobile Manipulation) to web-templates and integrate Rviz graphical interface which will allow the user to visualize a lot of information, using plugins for many kinds of available topics.

## Deliverables

- Migrated Pick & Place exercise without Rviz from ROS templates to RADI 2.4
- Integrated Rviz in the pick and place exercise
- Migrated Machine Vision exercise from ROS templates to RADI 2.4 along with RViz, however an error is yet to be resolved.
- Migrated Mobile Manipulation exercise from ROS templates to RADI 2.4 along with RViz, however an error is yet to be resolved.

The following sections of this blog will provide a detailed summary of the completion/errors/future works for this project.

## Pick & Place Exercise

The goal of this exercise is to learn the underlying infrastructure of Industrial Robot exercises(ROS + MoveIt + Industrial Robotics API) and get familiar with the key components needed for more complex exercises by completing the task of pick and place multiple objects and classify them by color or shape.

### Pull Request

- [Pick & Place (Gazebo + Console)](https://github.com/JdeRobot/RoboticsAcademy/compare/melodic...predator4hack:pick-place-without-rivz?expand=1)
- [Pick & Place (Gazebo + Console + Rviz)](https://github.com/JdeRobot/RoboticsAcademy/pull/1153)
- [Documentation](https://github.com/JdeRobot/RoboticsAcademy/pull/1163)

### Progress

- Exercise is working along with simulation on RADI 2.4

### Future Works

- Migrate the exercise to RADI 3
- Integrate RQT window in the exercise
- The user can stop the simulation at any moment by using the Stop button in the web-templates. However, because the APIs are called in pick and place grasp APIs, the simulation will only end after the picking/placing operation is done. This may be regarded one of the future versions' enhancements, as the simulation will cease as soon as we press the stop button (This may be achived using threading).

### Simulation

[Demo of pick and place exercise](https://www.youtube.com/watch?v=1rrcCzl-JWI)

## Machine Vision

The goal of this exercise is to learn how to use vision to assist industrial robot by detecting known objects and unknown obstacles.

### Pull Request

- [Machine Vision (Gazebo + Console)](https://github.com/predator4hack/RoboticsAcademy/tree/machine-vision)
- [Machine Vision (GAzebo + Console + Rviz)](https://github.com/predator4hack/RoboticsAcademy/tree/rviz-machine-vision)
- [Documentation](https://github.com/predator4hack/RoboticsAcademy/tree/machine_vision_doc)

### Progress

- Exercise is migrated to web-templates along with Rviz
- HAL/ENV APIs are working

### TODO

- Need to resolve : `ERROR: cannot launch node of type [pcl_filter/pcl_filter_server]: Cannot locate node of type [pcl_filter_server] in package [pcl_filter]. Make sure file exists in package path and permission is set to executable (chmod +x)`

    Steps taken to resolve this issue:
    - **Created ROS Entrypoint** : According to this [post](https://github.com/microsoft/AirSim/issues/2591), the reason behind this error is sourcing each of the docker sub-shell. So I created a ROS EntryPoint in order swource every subshell. But this doesn't seem to work.
    - **Installed pcl driver** - Because the pcl driver used in our Industrial Robots is custom and has some distinct functionalities than the standard driver, it does not appear to operate.
    - **Explicitly added paths in the enviornment variables** : Added the path of this driver directly in the enviornemnt variable but this didn't worked.


### Future Works

- Migrate the exercise to RADI 3
- Integrate rqt window in the exercise
### Simulation

[Demo video of the progress](https://youtu.be/YgRQSqbyP3s) 

## Mobile Manipulation

The goal of this exercise is to practice integrating navigation and manipulation. The mobile manipulator is MMO-500 robot from [Neobotix](https://www.neobotix-robots.com/homepage). They provides a set of ROS simulation packages and tutorials to test their mobile robot and mobile manipulators. The MMO-500 is one of them, combining the omnidirectional robot MPO-500 with a light-weight robot arm UR10. The navigation part of this exercise is based on their provided packages.

### Pull Request

- [Mobile Manipulation (Gazebo + Console + Rviz)](https://github.com/predator4hack/RoboticsAcademy/tree/mobile_manipulation)
- [Documentation](https://github.com/predator4hack/RoboticsAcademy/tree/mobile_manipulation_doc)

### TODO

- Need to resolve : `ERROR: Cannot locate node of type [scan_unifier_node] in package [cob_scan_unifier]. Make sure file exists in package path and permission is set to executable (chmod +x)`

    Steps taken to resolve this issue:
    - **Created ROS Entrypoint** : According to this [post](https://github.com/microsoft/AirSim/issues/2591), the reason behind this error is sourcing each of the docker sub-shell. So I created a ROS EntryPoint in order swource every subshell. But this doesn't seem to work.
    - **Installed COB driver** : Because the cob driver used in our Industrial Robots is custom and has some distinct functionalities than the standard driver, it does not appear to operate.
    - **Explicitly added paths in the enviornment variables** : Added the path of this driver directly in the enviornemnt variable but this didn't worked.

- 

- Need to resolove : `Failed to load plugin libgazebo_ros_moveit_planning_scene.so: libgazebo_ros_moveit_planning_scene.so: cannot open shared object file: No such file or directory`

    Steps taken to resolve this issue:
    - **Added libgazebo_ros_moveit_planning_scene from a git repo** : In [this](https://github.com/ros-simulation/gazebo_ros_pkgs/pull/713) pull request, the libgazebo_ros_moveit_planning_scene was integrated in kinetic devel, so I tried to add the same plugin to our workspace. This error was resolved but it came with some other errors(Refer week 10 blog).

### Future Works

- Migrate exercise to RADI 3
- Integrate RQT window in the exercise

### Simulation

[Demo video of the progress](https://youtu.be/BKCUI70vJnc)
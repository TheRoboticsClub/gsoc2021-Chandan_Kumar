---
layout: post
title: Community Bonding week 1
subtitle: Getting Familiar with Robotics Acadmey/Industrial Robots/Docker
---

Google Summer of Code starts with the Community Bonding period where we get to know about the community and get familiar with the code base and work style.

The first week of community bonding was all about getting familiar with JdeRobt Robotics Acadmey. Currently there are nine exercises that are updated in v2.3. The primary goal of this project is to add add three more exercises that are pick and place, machine vision and mobile manipulation exercise.

## Pick and Place exercise
The goal of this exercise is to learn the underlying infrastructure of Industrial Robot exercises(ROS + MoveIt + our own industrial robotics API) and get familiar with the key components needed for more complex exercises by completing the task of pick and place multiple objects and classify them by color or shape. Link to the [exercise](http://jderobot.github.io/RoboticsAcademy/exercises/IndustrialRobots/pick_place)

## Machine Vision
The goal of this exercise is to learn how to use vision to assist industrial robot by detecting known objects and unknown obstacles. The shape, size and color of the objects are known, but the pose of them and the situation of obstacles in surrounding environment need to be found using two cameras. Link to the [exercise](http://jderobot.github.io/RoboticsAcademy/exercises/IndustrialRobots/machine_vision)

## Mobile Manipulation
The goal of this exercise is to practice integrating navigation and manipulation. You will need to use a mobile manipulator(AGV+robot arm+gripper) to pick objects on one conveyor and place them on three other conveyors. Link to the [exercise](http://jderobot.github.io/RoboticsAcademy/exercises/IndustrialRobots/mobile_manipulation)

# Getting familiar with the web-template and docker
Ros is very specific to the versions of operating systems, packages and other dependencies. This is why it becomes difficult for a beginner to start off with the project. The installation has been greatly simplified, as all the required dependencies are already pre-installed in the [Robotics-Academy Docker Image](https://hub.docker.com/r/jderobot/robotics-academy). Robotics Academy (2.3 release) supports Linux (Ubuntu 18.04, 20.04 and other distributions), MacOS and Windows.

## Docker
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. More in the [documentaion](https://docs.docker.com/get-started/) of Docker

## Migration of Industrial Robots Repository to current RADI
The sole purpose of this task was to get familiarized with the structure of Robotics Academy Docker Image(RADI) and understand how to work with docker.

### Warnings and Errors
As Robotics Acadmey is using multi stage build which uses a build.sh script to automate the whole process, one small error occured which was due to limited permissions given while executing ```./build.sh <tag>```
This can be easily resolved using ```bash ./build.sh```.
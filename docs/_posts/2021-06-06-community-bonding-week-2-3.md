---
layout: post
title: Community Bonding Week 2-3
subtitle: Docker Bind Mount and finalizing Rviz display options
categories: [community bonding]
tags: docker Rvizweb Gzweb
---

## Docker Bind Mount

The first step in starting development in a docker container is to use bind mounts or volumes so that the changes in the docker container can be seen without having to rebuild the image. Bind mounts can be used to create side-by-side development environments and also to share data that needs to persist longer than the lifespan of the docker container.

When you use a bind mount, a file or directory on the host machine is mounted into a container. The file or directory is referenced by its absolute path on the host machine. By contrast, when you use a volume, a new directory is created within Docker’s storage directory on the host machine, and Docker manages that directory’s contents.

<p align="center"><img src="https://docs.docker.com/storage/images/types-of-mounts-volume.png"></p>

### Warnings and errors

#### ROS GPG Key Expiration

ROS GPG keys inadvertently expired and caused apt failures for a number of users. A full description of the security breach and the remediation can be found in this [ROS Discourse post](https://discourse.ros.org/t/new-gpg-keys-deployed-for-packages-ros-org/9454).

To fix this issue one will need to update the public key used for ROS apt repositories. To do this for ROS 1 installations you need to run a single command:

```curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -```

A [commit](https://github.com/JdeRobot/RoboticsAcademy/commit/842c0758a856c7119b6435fc8f17907bd17fdab1) has been created in order to fix this issue.

#### RLE Exception

After successfully mounting the container with my local repository, I discovered that none of the exercises are connecting to the server and following error was displayed:

```RLE Exception: [./RoboticsAcademy/exercises/follow_line/web-template/launch/simple_line_follower_ros_headless.launch] is not a launch file name The traceback for the exception was written to the log file```

After altering the GAZEBO_RESOURCE_PATH and paths in instruction.json, the error was rectified.

## GazeboWeb Testing

Robotics Academy uses GazeboWeb as a front-end graphical interface to gzserver which provides visualization of the simulation. Gzweb lets you interact with the simulation from the comfort of a web browser. This means cross-platform support, minimal client-side installation, and support for mobile devices.

To learn how Gzweb works, I made a basic webpage, connected it to ROS with rosbridge server, and used the roslibjs package  to drive turtlebot3 around in a circle.  A short video below demonstrates the moving turtlebot after recieving commands from html page.

<p align="center"><img src="https://lh3.googleusercontent.com/OeIUv2RfDsURUvdcR9ojQEpCPRSWOIiE2lpwqOqH6frcVf0Bmz5utv6MeMOFW2coihkK5X8Nxe7kd-mtl-4di16d7tWgp_WTDPuSD4TBRdTmM8pXSgpRYyIyuDUh2RZMjV5J4hUuLdnc0wknr6aNZvfOQPcO7ycKoVcthp_OnLdlvNz40DCrEpZgOkV511ZtIfO7Chz5nUMykFql8CMLXc134C7YENwSKo8hM_mJzgIfOLBlXJZCwn4rdjHXYuMaG4Y8hMQV6droGe4LCaybPo18PDF9PHyXtXg5CpRFoocgZA3pyD4HveVvfVqXk59wgzIzw1qOBT5BFr-5jdBEMBt4-fgYpWKgygxSLzj8w4pthvm7vhzmEk46geQof1d4SFQvNmxXJrfkkAXxHQ9GyRcx9IX-o5-9Om39ktTbnCxfIk6J3Zxre0xzeD91akcSKqZL52h7byPjH1OFiwojT8Vail2q0ZJGnu0NQE1Ah220dScrQmK15x4Cfoypp5lUV2xt1GORM-3cca_U5M9_LXMm3gEb1Xf0cQb8V3g4OH9aH8e0yTSgGNTJmTO1u1szsVvxG2TfrnffBRF8QYV1vN3utemu0IMILzNRMVTzH-Ir8d0VNGV9hkDGPSj0w3O4heGRTjKiJ8hcnueaX2cwzRl1PQL0N6emje8-qpomnz9yc3nfMTp1Q3PTCaOt1Bzs2cIcjRFZ8u54cNeWRYhC1kc=w600-h338-no?authuser=0"></p>

## RvizWeb Testing

Rviz is required for Industrial Robot exercises, and RviWeb is one method for incorporating Rviz into a web page. RVizWeb provides a convenient way of building and launching a web application with features similar to RViz. This [documentation](https://github.com/osrf/rvizweb) contains further information on RvizWeb.

<p align="center"><img src="https://lh3.googleusercontent.com/3C_RFxIe0YD038mqlItSh8OlaAEvjsEqEL8HuHbl2XUPn0Ia1RmUd7yJlAjGDHWh7jbo6Iaieu9uM2Dm5qulk_nXJYplXrbXyg_67eCke-bEcU6TB-Ba8tya94xpCW8PcTXoolsIJ6KcbMoa6P22mdZUm05LqjbPiJ9ZDfO76Zq5GkAnwWJy78GoAobItslhscmz0Jl18Z2Pq2avg5NX0JVDXO8f6CiMaLI3WcDcaMNr3Zxw2oHjUKLUZsPDBy7puxeYxYOSirit_o7OYXPfMar4kBTu2LFBwVGst_yiaIJl2g9CuCL8pwufHx0oMpfvYVTRXLeq_uuQ22YPV952v3_ZCfC0HCBYOkStj-RDlwmnHvn7YcLRx5Oii0gnTW-i5OZzVrmp3fySIfEgIKHfw2hQuhm-QqlqBB4xza015i-MOunVxNgsQMUxiUsMlFpnDqbaLwUGNcGHGF5210l_ijwb0SgaGSv4qMfaL4vzJ4sJMuUVXCQwIHoXu9S7CvMNWNIXV9bAfDLKt29NoN2HBEGuf2VpjVsy5dX6rBpUM-qXJCuqoJGhW-esLrEY0J1pj0PKlpO7QyTOo_gjDKpxxaIQy7_vUlzeRmztAaZOL6Fo-aPolDw8Bu8D-el37elBSkLfCALXhCv3I57I4JazhZTJNO_ovmhJkx305vKleuDKXjYzS6qqRIW9jqIFkxRaFJrN_335FgaNZI0xU7Lgzks=w1477-h830-no?authuser=0"></p>

## Using Bullet for Collision Checking

According to the project proposal, we planned to use bullet for collision checking. Bullet has continuous collision capabilities. This means that it can be guaranteed that no collision occurs during the transition between two discrete robot states with the environment.

<p align="center"><img src="https://lh3.googleusercontent.com/RqqVC1F_ckEQjFGbrMxM8pejX-04uICab4NrQ2nF7hQNPYiGYMVmIlQIDG7Q8ZQrxnroydZTUfTbXsKji4jYwEkUK4Zk8CpQ8QBg_4pAIGt22m9puTW0zK7XL63XoMIkSQ50-PNZjqsZpFXKzOT-MX3Y5H9n5wpkyeopGucEbVC-qG0hSsKMV-mnVdZ58MejrZkNc3GxFTxKwx0qZBkS27PPLb9nLcgUCLtlLb8v7FC_3U73T-BXP9rKvWL_DxuJ_oA_heqgLmdqClozC57R9WEgw8RitvtIxt1KkW8aoxS1mz0KeLhKORFOcF6nDxYbSgVIP50CzK51gEhmRDZ_en0fWvzvZxIMCTFOoI-VdGgiWuwGMX096P-Ju7ASi3eCrBwLGLG1ThruiA_KnpzQofqWi54jZ8KYLSUiBeG7jD9olsk_pY52utvw3TN0gY7xcByS4HpzSX61JjED3F8L-KEMw_VHipplto9VrDbhy_gDbTuzl9IVJ8m38Z7vwsJurME6uQ8v99mzELPBy43RMgKOalt9FqY0_bW0FEkvhH8OUlcUef-tyo4aJRRVNOOjszmppyGeWhVpw0PSqF5WxEZQohYvBUfRpspC8gX7U4gpb58jJ_aCShyrs57swtsKURl7ValitwxCZZ1XgjQK-kVbLFQsN9IgaA1jOZSdc3Z1O9pmZXig0rEfrNMzTqKxjaYP6Zpx6rE34mp4qmJmuj4=w1477-h830-no?authuser=0"></p>

Bullet's only drawback is that it is not compatible with all versions. Bullet is a ROS1-Noetic and ROS2-Foxy. I also discovered that the bullet took a long time to compute the place of collision (much slower than using traditional non-continuous collision). As a result, I feel we can put the process of adding bullets into the industrial robot exercise on hold until we get to Noetic.
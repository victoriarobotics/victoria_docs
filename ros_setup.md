# ROS Setup
This document covers the steps to install the Robot Operating System (ROS) that is used by
Team Victoria on the 2017 RoboMagellan robot.

## Install ROS Kinetic Kame
The Kinetic Kame is the version of ROS used for 2017 RoboMagellan. See http://wiki.ros.org/kinetic/Installation/Ubuntu.
The following steps install the full desktop version.

* Open terminal
* `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
* `sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116`
* `sudo apt-get update`
* `sudo apt-get install ros-kinetic-desktop-full`
* `sudo rosdep init`
* `rosdep update`
* `echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc`
* `source ~/.bashrc`
* `sudo apt-get install python-rosinstall`

You can test that ROS is installed correctly by running:

*

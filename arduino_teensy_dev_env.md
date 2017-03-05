# Arduino-Teensy Development Environment
This document covers the steps to install the required development environment used by Team Victoria to develop
the Arduino-Teensy code used for the 2017 RoboMagellan robot.

These steps are not required to install the software that will run the robot, only for developing the Arduino-Teensy
code thar tuns the robot.

## Install Arduino IDE
For Teensy development, we are using the 1.6.12 version of the Arduino IDE.

* Download the 1.6.12 version (see https://www.arduino.cc/en/Main/OldSoftwareReleases#previous).
Make sure to download the "Linux Arm" version.
* Assuming the file was downloaded to ~/Downloads:
  * Open Terminal
  * `cd ~/Downloads`
  * `tar -xf arduino-1.6.12-linuxarm.tar.xz`
  * `cd ~`
  * `mv ~/Downloads/arduino-1.6.12/ ~/`
  * `cd arduino-1.6.12`
  * `sudo ./install.sh`

This will result in a directory installed at ~/arduino-1.6.12 and ~/Arduino. You can launch the Arduino IDE
from the system menu Applications->Programming->Arduino IDE.

## Install TeensyDuino

## Install rosserial_arduino

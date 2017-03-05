# Arduino-Teensy Development Environment
This document covers the steps to install the required development environment used by Team Victoria to develop
the Arduino-Teensy code used for the 2017 RoboMagellan robot.

These steps are not required to install the software that will run the robot, only for developing the Arduino-Teensy
code that runs the robot.

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
from the system menu Applications->Programming->Arduino IDE. You can add a shortcut to the toolbar at the
bottom of the desktop.

## Install TeensyDuino
The microcontroller used for the 2017 RoboMagellan robot is the Teensy 3.5. Development for the Teensy
is performed in the Arduino IDE, but it requires for supporting libraries to be installed. Latest Teensy
information can be found [here](https://www.pjrc.com/teensy/teensyduino.html). These instructions are for
the TeensyDuino version 1.35.

* Download the TeensyDuino for ARM/Rasberry Pi (see https://www.pjrc.com/teensy/td_download.html).
Make sure to download the ARM/Rasberry Pi version.
* On https://www.pjrc.com/teensy/td_download.html, right click on "Linux udev rules" link and "Save link as..."
to ~/Downloads.
* Assuming all files were downloaded to ~/Downloads:
  * Open Terminal
  * `cd ~/Downloads`
  * The udev rule file gives non-root users permission to use the Teensy device.
    * `sudo cp 49-teensy.rules /etc/udev/rules.d/`
  * `chmod 755 TeensyduinoInstall.linuxarm`
  * `./TeensyduinoInstall.linuxarm`
  * The Teensyduino installer window will appear
    * First step: press "Next" button.
    * Second step: Navigate to the "/home/team-victoria/arduino-1.6.12" directory, press the "Next" button.
    The "Next" button will not be enabled until you navigate to the correct directory.
    * Third step: Choose "All" libraries, press the "Next" button.
    * Fourth step: Press the "Install" button.
    * Fifth step: After installation complete, press "Done".

This will result in a directory being installed at ~/arduino-1.6.12/hardware/teensy.

## Install rosserial_arduino
The Teensy uses the rosserial_arduino library to communicate with the ROS system. The rosserial_arduino
library must be installed so that is available for development. More information about the library
can be found at http://wiki.ros.org/rosserial_arduino. More details of rosserial_arduino installation
with the Arduino IDE can be found at http://wiki.ros.org/rosserial_arduino/Tutorials/Arduino%20IDE%20Setup.
These instructions will install the Kinetic version.

* Open Terminal
* `sudo apt-get install ros-kinetic-rosserial-arduino`
* `sudo apt-get install ros-kinetic-rosserial`
* `cd ~/Arduino/libraries`
* `rm -rf ros_lib`
* `rosrun rosserial_arduino make_libraries.py .`

This will result in a directory at ~/Arduino/libraries/ros_lib.

## Install Pololu IMU and Mangetometer Libraries
The Pololu [MinIMU-9 v5](https://www.pololu.com/product/2738) is used for gyro, accelerometer, and
compass data. Pololu provides libraries that access the LSM6DS33 and LIS3MDL chips via I2C. The
stock versions of these libraries use the Arduino Wire library, which is not directly compatible
with the Teensy. So, the Team Victoria repository contains forked versions of the original
repositories with modified versions to use the Teensy i2c_t3 library instead. These versions
of the modified libraries need to be installed before compiling the Team Victoria Teensy code.

### Using git clone
You can use git to clone copies of the libraries.

* Open Terminal
* `cd ~/Arduino/libraries`
* `git clone https://github.com/victoriarobotics/lis3mdl-arduino.git`
* `git clone https://github.com/victoriarobotics/lsm6-arduino.git`

### Using zip archives
You can download zip archives from github and install the libraries manually.

* Navigate to https://github.com/victoriarobotics/lis3mdl-arduino and download the zip file.
* Navigate to https://github.com/victoriarobotics/lsm6-arduino and download the zip file.
* Assuming the files were downloaded to ~/Downloads:
  * Open Terminal
  * `cd ~/Downloads`
  * `unzip lis3mdl-arduino-master.zip`
  * `unzip lsm6-arduino-master.zip`
  * `mv lis3mdl-arduino-master ~/Arduino/libraries/lis3mdl-arduino`
  * `mv lsm6-arduino-master ~/Arduino/libraries/lsm6-arduino`

This will result in two directiories being added to ~/Arduino/libraries, lis3mdl-arduino
and lsm6-arduino.

## Install Victoria Platform Repository
Now everything needed to develop the Team Victoria Teensy code is installed. Now the
Team Victoria Platform repository can be installed.

### Using git clone
You can use git to clone the repository.

* Open Terminal
* `cd ~`
* `git clone https://github.com/victoriarobotics/victoria_platform.git`

### Using zip archives
You can download zip archives from github and install the repository manually.

* Navigate to https://github.com/victoriarobotics/victoria_platform and download the zip file.
* Assuming the files were downloaded to ~/Downloads:
  * Open Terminal
  * `cd ~/Downloads`
  * `unzip victoria_platform-master.zip`
  * `mv victoria_platform-master ~/victoria_platform`

This will result in the ~/victoria_platform directory being created.

You can now use the Arduino IDE to compile any sketches located in ~/victoria_platform/Arduino.

# Raspberry Pi Setup
This document covers the steps to setup a stock version of the system Team Victoria is using
for Raspberry Pi 3 controller used on the 2017 RoboMagellan robot.

## SD Card Setup
The SD card for the Raspberry Pi 3 needs to be setup with an image. The SD card should
be at least 16 GB in size.

* Download "Ubuntu MATE 16.04.1 LTS" from the website https://ubuntu-mate.org/download/. 
Download the image for "Raspberry Pi" (ie ARM). The image is about 1.1 GB and should be
named something like "ubuntu-mate-16.04-desktop-armhf-raspberry-pi.img.xz".
* On Windows (see https://ubuntu-mate.org/raspberry-pi/):
  * Install 7-zip.
  * Use 7-zip to extract the image.
  * Install Win32DiskImager.
  * Use Win32DiskImager to write the image to the SD card.
  
## Ubuntu Setup
Once the SD card has been imaged, Ubuntu can be configured using the Raspberry Pi.

* Insert SD card into Raspberry Pi 3 and start it
* Superuser system configuration will appear:
  * Language: English
  * Time zone: Los Angeles
  * Keyboard layout: English (US)
  * Your name: Team Victoria
  * Computer name: Victoria
  * Username: team-victoria
  * Password: `r0b0magellan`
* System will then be installed and rebooted
* Login as team-victoria
* Repartition the image to use full SD card:
  * Open terminal
  ```
  sudo fdisk /dev/mmcblk0
  ```
  * Delete existing partition 2: d, 2
  * Create a new parition 2: n, p, 2, enter, enter
  * Write the partition, exit fdisk: w
  * Reboot, login as team-victoria
  * Open Terminal
  ```
  sudo resize2fs /dev/mmcblk0p2
  ```
  * You can use fdisk to verify the size of partition 2
* Configure WiFi
  * Open terminal
  * Scan for existing wifi networks:
  ```
  sudo iwlist wlan0 scan
  ````
  * Note the ESSID of the network you to join
  * Open the supplicant configuration file
  ```
  sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
  ```
  * Add the following configuration:
  ```
  network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
  }
  ```
  * Reboot
  * After reboot, use `ifconfig wlan0`. If the  inet addr field has an address beside it,
  the Pi has connected to the network. If not, check your password and ESSID are correct.
* Disable X11 desktop - Ubuntu MATE provides a built in command to disable/enable the graphical
desktop.
  * Disable: `sudo graphical disable`
    * Then reboot and a command line interface will present itself for login.
  * Enable: `sudo graphical enable`
    * Then reboot and the graphical interface will present itself for login.

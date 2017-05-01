# Victoria v1 Items
* Remove Lidar
* Voltage Monitor
  * Make it visible
  * Publish value as a topic
* GPS
  * Consolidate FTDI/GPS connections - New proto board
* Fob control
  * Investigate options for longer range, easy to hold
* Motors
  * Faster motors after calculating needs
  * Check if encoders work correctly at higher speed
* Network
  * Explore options for better link
* Chassis
  * Seal up holes
    * Lidar
    * Underneath
    * r200 front panel
* Teensy
  * PID controller
  * Voltage monitoring (publish value on topic)
  * Restructure repository
  * Use interrupts for fob detection
  * Overflow issue with encoder, explore
  * Report motor current (from TReX)
  * Break up into libraries, testing
* Base repository
  * General cleanup
* ros repository
  * depth_laser_filter, rename and move to perception
* localization repository
  * Get working with move_base
  * Use r200 for obstacle avoidance
  * Use optical flow?
  * vslam package?
  * photodiode to detect inside/outsied for r200
* upboard
  * Add shutdown button
  * Startup script to bring up the robot

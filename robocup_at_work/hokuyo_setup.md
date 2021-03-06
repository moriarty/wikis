hokuyo laser scanner setup
==========================

This tutorial describes how to configure and test hokuyo laser scanner with ROS.

Some general information about the sensor:

		Hokuyo is a small and lightweight laser range finder with an approx. maximum scanning
		distance of 5.6 m, it has a scan angle of 240° and can acquire scans with a frequency of 10.0 Hz

Documentation is available at:

		http://wiki.ros.org/hokuyo_node/Troubleshooting
		http://wiki.ros.org/hokuyo_node/Tutorials/UsingTheHokuyoNode
		http://www.youbot-store.com/youbot-developers/software/drivers/hokuyo-laser-range-finder-driver

Installation
============

Connect hokuyo to your computer via USB cable, the green led should blink

try to check if it is detected by your computer:

		ls /dev/ttyACM*

you should get something like this:

		/dev/ttyACM0

check for hokuyo permissions:

		ls -l /dev/ttyACM0

you should get something like this:

		crw-rw-rw- 1 root dialout 166, 0 Dec  7 10:49 /dev/ttyACM0

if not then use this command to change the permissions:

		sudo chmod a+rw /dev/ttyACM0

Test the hokuyo laser sensor
============================

Try this commands:

		roscore
		rosparam set hokuyo_node/calibrate_time false
		rosparam set hokuyo_node/port /dev/ttyACM0
		rosrun hokuyo_node hokuyo_node
		rosrun rviz rviz

configure rviz:

		set fixed frame to laser
		Add "LaserScan" visualization
		expand and select the topic to /scan

You should now be able to visualize the readings in rviz

Troubleshooting
===============

Error -> device is already locked:

Check which processes are currently accesing the hokuyo:

		lsof|grep /dev/ttyACM0

If you recive a non empty response then ensure hokuyo is really not being used by any other process and reconnect it to you computer (disconnect and connect again)

--------------------------------------------

Error -> premission denied:

Give proper permissions to the hokuyo node as described in the first part:

		sudo chmod a+rw /dev/ttyACM0
		
--------------------------------------------

Error -> device or resource busy:

		...just restart your machine -.-

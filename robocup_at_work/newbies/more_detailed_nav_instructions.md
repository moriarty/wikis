ROS NAVIGATION on hydro
========================

Launching mir_2dnav nodes
=========================

For simulation:

		roslaunch mir_bringup_sim robot.launch

For real robot:

		roslaunch mir_bringup robot.launch

For omnidirectional navigation:

		roslaunch mir_2dnav 2dnav_omni.launch

For differential navigation:

		roslaunch mir_2dnav 2dnav_diff.launch

Run gazebo and rviz:

		rosrun gazebo_ros gzclient
		rosrun rviz rviz

Configure rviz
==============

Select:

		global options -> set the fixed frame to -> map

Add visualization (expand and select topic):

		LaserScan -> /scan_front
		LaserScan -> /scan_rear
		Map -> /map
		Path -> /move_base/DWAPlannerROS/global_plan
		Path -> /move_base/DWAPPlannerROS/local_plan

Navigate
========

Check for this first:

		make sure you have configured properly rviz, and that the map is loaded and displayed

Estimate 2D nav pose from the simulation environment (gazebo):

		Visualize on gazebo the youbot and see where is it located and in which direction the robot is pointing

Give the 2D nav pose information to rviz:

		On rviz click on "2D Pose Estimate" button and give the estimated pose of the youbot obtained from the previous step

Set the goal pose of the youbot:

		Click on "2D Nav Goal" and give the goal pose

The robot should be navigating now from the current pose to the requested goal pose.

remark: map is being loaded from this location:

		~/ros_ws/at_work/src/mas_common_robotics/mcr_environments/mcr_default_env_config/brsu-c025/map.pgm

make sure map.gpm is there along with map.yaml configuration file


Troubleshooting
===============

1. Missing tranformations does not allow me to fully visualize the youbot on rviz.

Solution: Most probably you need to recompile and run with internet connection for the first time as well as

using the supported linux version 12.04 LTS.

2. gksudo error while compiling.

Solution: Set environment variable USE_NORMAL_SUDO to value 1:

		export USE_NORMAL_SUDO=1
		sudo ls

run openni tracker
==================

Documentation available at:

		http://wiki.ros.org/openni_tracker
		http://answers.ros.org/question/128116/openni_tracker-find-user-generator-failed-cant-create-any-node-of-the-requested-type/

1. Run roscore

		roscore

2. Run rviz

		rosrun rviz rviz

3. Run the openni tracker

		rosrun openni_tracker openni_tracker

4. Stand in front of kinect at a distance of 2 m roughly and surrender 
 
in Pi position -> http://3.bp.blogspot.com/-t9FxKt9JUts/TWfK4juSF7I/AAAAAAAABBI/36-uvouIG7I/s320/PsiPose.gif

5 Configure rviz:

select fixed frame : openni_depth_frame

add tf topic


Done! now you should be able to track your body with rviz and tf by using depth camera


Troubleshooting
===============

Verify that depth camera is publishing pointclouds on ros:

Run openni.launch

		roslaunch openni_launch openni.launch
	
Open and configure rviz:

		rosrun rviz rviz
		
Select fixed frame as camera link, add pointcloud2 topic and select pointcloud topic.

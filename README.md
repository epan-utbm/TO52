# SLAM with a 3D lidar

## 2018 UTBM TO52 project

### Romain Henry, Florent Willemin, Zhi Yan, and Yassine Ruichek

## Result of branch two_velodynes (it uses 2 HDL-32E LiDAR for Laser Odometry and Mapping (LOAM))

<a href="https://imgflip.com/gif/2bnubu"><img src="https://i.imgflip.com/2bnubu.gif" title="made at imgflip.com"/></a>

## Result of branch octomap (it uses octomap server for mapping)

<a href="https://imgflip.com/gif/2bpppi"><img src="https://i.imgflip.com/2bpppi.gif" title="made at imgflip.com"/></a>

![alt text](https://github.com/epan-utbm/TO52/blob/master/ocotmap_full_map4.png)

## How to build and run the project with Qt

- Select the branch that is interesting to you
- !!! Don't install Qt !!!
- Follow this tutorial first : https://ros-industrial.github.io/ros_qtc_plugin/_source/How-to-Install-Users.html
- Open Qt, create new project by using "other project" and selecting "ros workspace" and your dedicated workspace
- Manage your compilation and run tool chain (click on projects on the left)
- In run, you may have one launch step with package loam_velodyne and [loam_velodyne.launch] {depend of your branch} as target.

### ROS

See : http://wiki.ros.org/ROS/Concepts to get informations about it.

- the [loam_velodyne.launch] {depend of your branch} will :
	- start the master (allow the nodes to find each other, exchange messages and use services)
	- start the nodes (processes) written in cpp (or py) and compiled using gcc + rviz (a nodes)
	- start the the LiDAR record (we used a ".bag")
	- start a node that will translate the content of the ".bag" in pointclouds



## How to debug with Qt

To debug, only one object (one node) could be debug  : 
- Don't forget to allow ptrace ! by following these instructions :
	- Open file: sudo gedit /etc/rc.local
	- Add this line before the exit 0 line: echo 0 | tee /proc/sys/kernel/yama/ptrace_scope
- Insert your breakpoint
- Menu Bar > Debug > Start Debugging > Attach to Unstarted Application...
- Browse to the executable (devel/lib/loam_velodyne/multiScanRegistration) by exemple
- select start watching
- run your project (Ctrl + R)
- depending on where the breakpoints it should be stop when it reaches one 


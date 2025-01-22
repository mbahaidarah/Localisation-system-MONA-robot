# Localisation-system-MONA-robot
This repository explains how to install Whycon localisation system for robotics experiments using (ROS noetic) and Ubuntu 20.04.

## System Setup:
1. Install Ubuntu 20.04.
2. Install ROS Noetic from this [link](https://wiki.ros.org/noetic/Installation/Ubuntu).
3. Install Python3.
4. Install OpenCV: `sudo apt install libopencv-dev python3-opencv`
5. Install 'usb_cam' package: `sudo apt-get install ros-noetic-usb-cam`
6. In the terminal, go to 'catkin_ws' directory, and type: `catkin_make` to build the ROS.
7. Do not forget to source ROS by typing in the terminal: `source devel/setup.bash`.
8. Test 'usb_cam' package to make sure your camera is working fine by typing this: `roslaunch usb_cam usb_cam-test.launch`.

## Camera Calibration:
1. Download the chessboard paper for calibration in which the intersections between the black and white squares are 8 on the x-axis and 6 on the y-axis.


   




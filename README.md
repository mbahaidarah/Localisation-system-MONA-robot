# Localisation-system-MONA-robot
This repository explains how to install the Whycon localisation system for robotics experiments using (ROS noetic) and Ubuntu 20.04.

## 1. System Setup:
1. Install Ubuntu 20.04.
2. Install ROS Noetic from this [link](https://wiki.ros.org/noetic/Installation/Ubuntu).
3. Install Python 3.
4. Install OpenCV: `sudo apt install libopencv-dev python3-opencv`
5. Install 'usb_cam' package: `sudo apt-get install ros-noetic-usb-cam`
6. In the terminal, go to 'catkin_ws' directory, and type: `catkin_make` to build the ROS.
7. Do not forget to source ROS by typing in the terminal: `source devel/setup.bash`.
8. Test 'usb_cam' package to make sure your camera is working fine by typing this: `roslaunch usb_cam usb_cam-test.launch`.
9. To find the 'usb_cam-test.launch' file, go to (Other Locations) in the Ubuntu system as shown in the image below:
<img src="https://github.com/user-attachments/assets/45104c08-9cbb-4fc2-acf5-6adfacae6279" width="300" height="200">

10. Then, navigate to: opt > ros > noetic > share
11. In the share folder, search for 'usb_cam' to find the launch file.
12. If the camera did not work, check the following steps that might help to fix:
   a. You might need to change the camera number: /dev/video0 or video1
   b. If the camera window shows a green screen, you need to change the pixel format from 'yuyv' to 'mjpeg'.
13. If the camera works fine, go to the next step.

## 2. Camera Calibration:
1. Download the chessboard paper (Checkerboard-A4-25mm-8x6.pdf) in this repository for calibration, in which the intersections between the black and white squares are 8 on the x-axis and 6 on the y-axis.
2. In one terminal, open the camera using the 'usb_cam' launch file.
3. In another terminal, go to 'catkin_ws' and source it. Then, type this command: `rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.108 image:=/usb_cam/image_raw camera:=/usb_cam`
4. A grey-scale camera window will be shown, and you should show the (Chessboard paper) to the camera from different angles, and repeat this process until the 'calibrate' button is activated (in green colour).
5. Press activate and wait till it's done. When the activation is completed, you will notice in the terminal some information such as: camera matrix, distortion, rectification, and projection.
6. Finally, press the 'commit' button, which will close the grey window of the calibration.



## 3. Whycon Localisation System with ROS:




   




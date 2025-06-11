# Localisation-system-MONA-robot
This repository explains how to install the Whycon localisation system for robotics experiments using (ROS noetic) and Ubuntu 20.04.

## 1. System Setup:
1. Install Ubuntu 20.04.
2. Install ROS Noetic from this [link](https://wiki.ros.org/noetic/Installation/Ubuntu).
3. Install Python 3.
4. Install OpenCV: `sudo apt install libopencv-dev python3-opencv`
5. Install 'usb_cam' package: `sudo apt-get install ros-noetic-usb-cam`
6. In the terminal, go to the 'catkin_ws' directory `cd catkin_ws`, and type: `catkin_make` to build the ROS.
7. Do not forget to source ROS by typing in the terminal: `source devel/setup.bash`.
8. Test the 'usb_cam' package to make sure your camera is working fine by typing this: `roslaunch usb_cam usb_cam-test.launch`.
9. To find the 'usb_cam-test.launch' file, go to (Other Locations) in the Ubuntu system as shown in the image below:
<img src="https://github.com/user-attachments/assets/45104c08-9cbb-4fc2-acf5-6adfacae6279" width="300" height="200">

10. Then, navigate to: opt > ros > noetic > share
11. In the share folder, search for 'usb_cam' to find the launch file.
12. If the camera did not work, check the following steps that might help to fix:
   a. You might need to change the camera number: /dev/video0 or video1
   b. If the camera window shows a green screen, you need to change the pixel format from 'yuyv' to 'mjpeg'.
13. If the camera works fine, go to the next step.

## 2. Camera Calibration:
1. Download the chessboard paper **(Checkerboard-A4-25mm-8x6.pdf)** in this repository for calibration, in which the intersections between the black and white squares are 8 on the x-axis and 6 on the y-axis.
2. In one terminal, open the camera using the 'usb_cam' launch file.
3. In another terminal, go to 'catkin_ws' and source it. Then, type this command: `rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.108 image:=/usb_cam/image_raw camera:=/usb_cam`
4. A grey-scale camera window will be shown, and you should show the (Chessboard paper) to the camera from different angles, and repeat this process until the 'calibrate' button is activated (in green colour).
5. Press activate and wait till it's done. When the activation is completed, you will notice in the terminal some information such as: camera matrix, distortion, rectification, and projection.
6. Finally, press the 'commit' button, which will close the grey window of the calibration.



## 3. Whycon Localisation System with ROS:
1. In the terminal, go to the 'src' folder > 'catkin_ws', then source it.
2. git clone: `https://github.com/jiriUlr/whycon-ros.git`
3. Type: `catkin_make` to build the directory.
4. Change the folder name from 'whycon-ros' to 'whycon'.
5. Go to the launch folder of 'whycon'. Open 'whycon-test.launch' file and modify it as follows:
   a. In the first node, change from 'camera' to 'usb_cam' for both: image_raw & cam_info.
   b. You can change the diameter value of the tag based on the printed tag you have. You can measure the diameter of the circle after you print it. It is measured by meter, so if the diameter of your tag is (8 cm), you can write 0.08.
   c. Add <usb_cam> node from the 'usb_cam' original launch file to the whycon launch file.
6. Run the launch file: `roslaunch whycon whycon-test2.launch`. A camera window should be opened, and by showing the tag, it can be detected.
7. In the meantime, you can write in the terminal: `rostopic list` to see the currently activated topics.
8. There is a topic called **(markers)** that gives us the position and orientation of the tags and also their IDs.
9. You can type in the terminal: `rostopic echo /whycon/markers`. Then, you will see continuous data displayed in the terminal, which indicates all the information of the tags that are recognised by the camera.
10. At this point, you can write a subscriber in Python or C++ to get these values and process them.
11. It is very important when you run the 'whycon' launch file, we need to specify the number of bits that we used to generate the tags (It will be explained in the next section), e.g, `roslaunch whycon whycon.launch id_bits:= 7`. We do that to allow the Whycon system using the camera to detect the tags in the arena, and when we listen to the topic, the IDs of the tags will be shown in the terminal.


## 4. Generate the Whycon Tags:
1. In a terminal, go to 'catkin_ws' then, 'src' directory.
2. Clone the repository: `git clone https://github.com/jiriUlr/whycode-gen.git`
3. In the same terminal, go to the folder 'whycode-gen', and type: `make`, to compile.
4. Open a new terminal and go to 'catkin_ws' and source it. Then, go to the 'whycon-gen' folder.
5. Type this command: `./whycode_gen bits_number` to generate the tags in the same directory, where in the command:
   a. If bits_number = 4, the generated tags are 3
   b. If bits_number = 5, the generated tags are 6
   c. If bits_number = 6, the generated tags are 9
   d. If bits_number = 7, the generated tags are 18
**((You can increase the bits_number to get more tags if needed))**


## 5. Calibrate the Arena Dimensions:
1. The Whycon system needs to be launched, and if you have a rectangular arena, four tags should be placed on the corners to be detected by the camera.
2. Open a new terminal, go to 'catkin_we' directory, source it and then, go to the 'src' folder.
3. Clone the 'rqt whycon ros' program that is responsible for calibrating the arena by typing: `git clone https://github.com/jiriUlr/rqt-whycon-ros.git`.
4. Make sure that only the four tags on the corners are there and there are no other robots with tags in the arena.
5. Type this command: `rosrun rqt_whycon rqt_whycon` to run the program. However, because in the Python code of ‘rqt_whycon.py’ the first line is: (#!/usr/bin/env python). It should be converted to Python3. Then, the previous command will work fine.
6. However, if you didn’t change Python to Python3, the program can work by going to the folder 'src/rqt-whycon-ros/scripts'. Then, type: `python3 rqt_whycon`. It will work as the previous step.
7. You should see the window below:
<img src="https://github.com/user-attachments/assets/c378dcf2-8cc6-4374-b769-5ba0a3fa8806" width="500" height="400">

8. Click 'refresh', which is the yellow arrow.
9. From the drop-down menu on the left (blue arrow), select '/whycon'.
10. Click auto calib (green arrow). You will see some numbers and processing showing in the terminal of the (whycon.launch), wait till it finishes.
11. Then, select from the drop-down menu on the right (red arrow) ‘2D coordinates’. You will see the default height and width, which range from (0,0) to (1,1).
12. To change the height and width, go to the (rqt_reconfigure_Param) window and set the length (x-axis) and the width (y-axis) according to your arena size. For example, in the above small arena image (x=0 to 80cm & y=0 to 100cm). So, we put length=0.8 and width=1.0 in meters.
13. Change the menu in (red arrow) to ‘camera coordinates’. Then, click again on 'auto calib' (yellow arrow), and wait for some processing.
14. After that, in the menu with (red arrow), select ‘2D coordinates’ to see the requested dimensions of the arena.
15. Finally, close the ‘rqt_whycon’ window so, we will have only one operating camera window: /whycon/processed_image.
16. We can place a MONA robot to see its [x,y] position on the arena in red colour, as shown below:
<img src="https://github.com/user-attachments/assets/594e0d1c-eece-4d58-9b9f-1f2f8059c42a" width="500" height="300">



 
   




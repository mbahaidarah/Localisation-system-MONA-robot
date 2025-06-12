# Arduino Setup and Implementation
Since the MONA robots can be programmed using Arduino software, we need to prepare all the libraries that allow us to program it and use the Wi-Fi module for communication.


## Arduino Setup:
1. Install Arduino on your PC.
2. Go to this GitHub page: https://github.com/yorkrobotlab/swarmhack/tree/master/mona/lib/MONA_ESP_lib
3. Follow the steps on that website above by installing the required libraries. Don’t forget to test the (MONA-ESP Robot Library), which is the last step on the GitHub page above. If the library worked fine, then go to the next step.
4. After that, we need to install the ESP Websocket library for wireless communications between the PC and MONA.
5. Go to this GitHub page to get the library: https://github.com/morrissinger/ESP8266-Websocket, click on the green button (<> code) and ‘download zip’. Unzip the folder ‘ESP8266-Websocket-master.zip’. After that, take this folder to the library directory in the ‘Arduino’ folder (remove -master from the folder name).
6. For sending JSON data, we need to install the ArduinoJson library (Ref: https://arduinojson.org/ ). This can be done in Arduino IDE by going to ‘Library Manager’ and searching for “ArduinoJson”. Select the version, e.g. 7.0.1, then install.
7. Set the board name, baud rate and the port in Arduino IDE, as shown below:
<img src="https://github.com/user-attachments/assets/7bb46d37-669f-4af6-9ef9-813dc5945734" width="500" height="300">

8. Now, go to the examples in Arduino (MONA_ESP_lib), then the 'Socket_control.ino' file
9. Make sure that you type the **SSID** and **PASSWORD** of the Wi-Fi router to allow MONA to connect to it.
10. Upload the Arduino code to MONA by using the USB cable.
11. If you face problems in uploading the code to MONA, check the following solutions (if not, just go to step 12):
- For the serial module not found error, we need to install 'pyserial' in the system by typing: `python3 -m pip install pyserial`
- When you can’t upload the code because of the 'ttyUSB0' and the port is not recognised, you need to add yourself to dialout and change permissions on it by typing these two commands one by one:
         `sudo adduser <username> dialout`
         `sudo chmod a+rw /devttyUSB0`

12. While MONA is connecting to the PC by a cable, open the serial monitor in Arduino IDE and then, press the reset button on MONA to see the IP address of MONA in the serial monitor.
13.	Take that IP address and put it in the Python/MATLAB code to allow communication with MONA.
14.	Now, you have to fix the code of ‘Socket_control.ino’ to fit you communication code of transferring data between MONA and host PC.





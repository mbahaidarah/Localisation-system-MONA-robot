# Arduino Setup and Implementation
Since the MONA robots can be programmed using Arduino software, we need to prepare all the libraries that allow us to program it and use the Wi-Fi module for communication.


## Arduino Setup:
1. Install Arduino on your PC.
2. Go to this GitHub page: https://github.com/yorkrobotlab/swarmhack/tree/master/mona/lib/MONA_ESP_lib
3. Follow the steps on that website above by installing the required libraries. Don’t forget to test the (MONA-ESP Robot Library), which is the last step on the GitHub page above. If the library worked fine, then go to the next step.
4. After that, we need to install the ESP Websocket library for wireless communications between the PC and MONA.
5. Go to this GitHub page to get the library: https://github.com/morrissinger/ESP8266-Websocket, click on the green button (<> code) and ‘download zip’. Unzip the folder ‘ESP8266-Websocket-master.zip’. After that, take this folder to the library directory in the ‘Arduino’ folder (remove -master from the folder name).
6. For sending JSON data, we need to install the ArduinoJson library (Ref: https://arduinojson.org/ ). This can be done in Arduino IDE by going to ‘Library Manager’ and search for “ArduinoJson”. Select the version e.g. 7.0.1 then, install.
7. Set the board name, baud rate and the port in Arduino IDE as shown below:


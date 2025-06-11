# Prepare Python Subscriber
We need Python files to write subscribers to get the data, e.g. robots' positions, and process them in your code in VS Code. The project in this repository uses the MONA robot that has an ESP32 MCU. To send some data to the MONA via Wi-Fi, we need to install some dependencies.

## Installations:
You need to install ujson, websocket-client, and numpy by typing the commands below:
- `sudo apt-get install python3-ujson`
- `pip3 install websocket-client`


## Running a Python file:
1. You need to work in the same directory of the 'whycon' folder in the 'catkin_ws'.
2. Bear in mind that when you want to run a Python file in the terminal, it should be an executable file. This can be done by checking the files in the folder by typing: `ls` command. If the file’s name is in white colour, that means it’s not an executable file.
3. Therefore, you need to type: `chmod +x file_name.py`
4. By applying the command above, the file’s name will be in green colour.
5. Now, you can run the Python file in the terminal by typing: `python3 file_name.py` then, press enter.


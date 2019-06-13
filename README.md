# Anti-BadUSB
A python script that is for temporary uses. WHID Devices Only Detected As Of Right Now!

# OS (Operating System)
* Linux (All Distrobutions as far as i know!)

# Installation
* RUN "python requirements.py" in order to install such prequisites!
* RUN "python abusb.py" to run script!

# Features
* Will NOT let you move mouse after running.
* Will NOT allow you to press Ctrl + C Otherwise... SHUTDOWN!
* Will allow you to type but once USB device is inserted... SHUTDOWN!
* Has a hidden button-combo in order to stop script and head to python!
* Has a customizable delay in "Data/Data.yaml"!
* Button combo is customizable in the configuration file "Data.yaml"!

# Problems
* Yet to be determined why module does not detect any other devices other than such WHID devices! I have contacted the developer directly on such page of module!

# Delay Configuration
* Head oever to "Data/Data.yaml"!
* Think of a delay value!
* Put such number in like such "3"!

# Button-Combo Configuration
* Head over to "Data/Data.yaml"!
* Find 2 button YOU wish to utilize for such script!
* Next input them like such "ctrl+shift"!

# The CODE:
```
# CODE BELOW: Imports the required prequisites/modules!
from os import system
import os
import pynput
import yaml
import time
import random
import exit
from pynput.mouse import Button, Controller
import keyboard
# WILL DETECT IF USER PRESSES EXIT BUTTON-COMBO
# AND WILL THEN PROCEED TO SHUTDOWN!
def on_exit():
    system('sudo shutdown now')
# CODE BELOW: Defines what mouse is... CONTROLLER!    
mouse = Controller()

# CODE BELOW: Opens the configuration file
with open('Data/Data.yaml', 'r') as data:
    data = yaml.load(data)
# CODE BELOW: Defines the delay, and buttcombo then resets terminal
# then generates a random number in a stirng form from 1, 777
delay = data['delay']
buttcombo = data['buttcombo']
system('reset')
number = str(random.randint(1, 777))

# CODE BELOW: Repeats the code indented below "for i in range(999):
# FOR 999x
for i in range(999):
    time.sleep(delay)
    mouse.position = (999, 335)
    # CODE BELOW: Runs COMMMAND "python find.py" and writes such output
    # to "output.txt"
    system('python find.py > output.txt')
    # CODE BELOW: Repeats 99x
    # then moves mouse to screen coords (999, 335)
    for i in range(999):
        mouse.position = (999, 335)
    # CODE BELOW: Says if "Device" is found in "output.txt" then print
    # "USB FOUND!" then will proceed to repeat again 999x in order to see
    # devices are found and if such devices are found such script WILL proceed to
    # Shutdown Computer! If USB is NOT found it will search again and wait for hidden exit
    # to be initiated!
    if "Device" in open('output.txt').read():
        print('USB FOUND!')
        for i in range(999):
            mouse.position = (999, 335)
            print('SHUTTING DOWN!')
            system('sudo shutdown now')                
    else:
        print('USB NOT FOUND! Starting Search Again!!!')
        if keyboard.is_pressed(buttcombo):
            system('python')
```

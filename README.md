# PAVED
This is a repository for all the software that will run on the Personal Autonomous Vehicle for Education and Development (PAVED) project.

## ROS
### Version: Kinetic Kame
### Linux Version: Ubuntu 16.04

This repository master will content the latest STABLE version of the ROS architecture running on PAVED.

### Installation:
To run on the dedicated laptop, copy the entire "ROS" folder to the "home" directory and the "ROS_Launch" and associated startup and shutdown shortcuts to the "Desktop" directory.

### Current ROS Capabilities:
- Receive simple input from LabJack (potentiometer connected to AIN0) and publish to topics/nodes.
- Process voltages received from LabJack in ROS "compute.py" node.
- Output command voltages to arduino in the form of percent of servo range (0% - 100%) from "translator.py" node. These voltages are sent as strings over serial communication.
- Arduino reads in strings and converts to floats. Applies floats to servo.

### Known Issues:
1. **Serial communication overflow:** Serial buffer does not flush and overflows after a certain number of commands have been sent (worsens with higher speeds). This causes the servo to slowly stop responding to inputs as it is trying to catch up to the commands in the buffer.

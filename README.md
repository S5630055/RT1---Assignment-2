Research Track I - Assignment 2
================================

This project shows up a mobile robot moving in a 3D space, which has to reach a desired position by avoiding obstacles. This happens in a virtual environment, managed by the standard virtual simulator of ROS, called Gazebo.

Installing and running
----------------------
To run the program, we have to install xterm:
```bash
$ sudo apt-get install xterm
```
and SciPy:
```bash
$ sudo apt-get install python3-scipy
```
Go inside the src folder of your ROS workspace and clone the repository folder:
```bash
$ git clone
```
Then, from the root directory of your ROS workspace, run the command:
```bash
$ catkin_make
```
You can run `$ roscore`  in a terminal or skip it. Anyway, it will be runned automatically. Run the string below to start the programme:
```bash
$ roslaunch assignment_2_2022 assignment2.launch
```

Troubleshooting
----------------------
Check your python version running:
```bash
$ python --version
```
If it appears Python 3, there is no problem. If appears Python 2, run this:
```bash
$ sudo apt-get install python-is-python3
```

Nodes
----------------------
Inside `~/<your ros workspace folder>/src/assignment_2_2022/scripts/` there are 6 python files, representing the 6 programme nodes:

1. `bug_as.py`: action server node receiving the requested position from the client and calling the necessary services to bring the robot to the required position;
2. `user_input.py`: action client node responsible for asking the user to enter the coordinates X and Y of the final destination that the robot has to reach, or to delete them. Then, it publishes the robot position and speed as a custom message on the /_position_velocity_ topic, based on the values of the /_odom_ topic.
3. `print_info.py`: node printing on the terminal the distance of the robot from the target position and its average speed. These parameters are taken from the _/position_velocity_ topic as a custom message.
4. `go_to_point_service.py`: implementation of a service node. When called, it moves the robot to the requested position.
5. `wall_follow_service.py`: implementation of a service node. When called, it allows the robot to move around an obstacle (in our case a wall).
6. `service.py`: it is a service node. When called, it prints the number of successful reached targets and the number of cancelled targets.

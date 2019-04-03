---
title: "Car keyboard control"
date: 2019-04-03T01:29:57-04:00
draft: true
---

## Demo:

[Steering control](https://streamable.com/m3k5l)

[Throttle control](https://streamable.com/xba2p)

## Progress

Our team met on Sunday, 31 March 2019 to work on Assignment 3 - F1/10 Teleop. Following the directions in the assignment specifications and the lecture slides, we were successfully able to modify the provided `talker.py` and `keyboard.py` files to accept keyboard input and control the F1/10 vehicle. 

While modifying the `keyboard.py` file, we had to examine the `curses` python library to determine which key matched `curses.KEY_DC`. We found that this mapped the delete key on the keyboard. Additionally, we had to change the increment/decrement value to 0.3 instead of 0.1 to more easily see changes while debugging our code. The assignment specification document says that we must use 0.1, but does not provide a reason. We changed it back to 0.1 once we verified it was working.
Writing the `talker.py` file was similar to the work we had done with turtlesim before as we only had to subscribe and publish to some topics. We followed the mapping formula in the assignment specifications to convert from [-100, 100] to pulse width modulation values of [6554, 13108]. We originally tested a formulation for this conversion using round(
Additionally, we discovered that the Jetson board has a power button.

## Problems we ran into:

The kill command for this project was one of the problems we initially ran into as we could not discover why. However, it turned out that the problem was due to the us not correctly sending the msg to set velocity and angle to 0.

Turns out that the car requires the battery to be plugged in before the wheels would run even when code is fine.



A technical issue we ran into was that sometimes files and directories would appear like they would simply vanish. This occurred suddenly sometimes when running:

{{< highlight cmd >}}
rosrun rosserial_python serial_node.py /dev/ttyACM0
{{< /highlight >}}

This problem would not be fixed by rerunning roscore, re-sshing into the jetson, and restarting the VM that held ROS.
It appears however that simply restarting the entire vehicle(replug everything, restarting onboard computer, ) would make it reappear.



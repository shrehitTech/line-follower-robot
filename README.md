# Line Follower Robot

## Overview
This project is a simple Arduino-based line-following robot that detects a path and follows it autonomously.  
I built this to learn about sensors, motors, and real-time programming. I have also attached a code that I have explained in detail.

## Hardware Used
- Arduino Uno / Nano
- Infrared sensors (IR sensor module)
- DC motors + motor driver (L298N)
- Wheels & chassis
- Battery pack

## Software
- Arduino IDE
- Arduino C++ libraries (Servo, Motor Control)

## How It Works
1. IR sensors detect the black line on the floor.
2. Arduino reads the sensor signals.
3. Depending on which sensor detects the line, the robot adjusts the motor speed to follow the path.
4. The robot moves forward while correcting its path automatically.

## Challenges & Fixes
- **Problem:** The robot sometimes turned too late on curves.  
  **Solution:** Adjusted sensor sensitivity and motor speed.
- **Problem:** Wheels slipped on smooth surfaces.  
  **Solution:** Added rubber wheels for better grip.

## Improvements
- Add speed control via Bluetooth.
- Use multiple sensors for sharper turns.
- Add obstacle avoidance while following the line.

## Media

https://github.com/user-attachments/assets/234ba36d-9b9f-414d-ac6f-3ea3c4fc4ea2
// If you open this link in new tab then you will see an example image of the line following robot



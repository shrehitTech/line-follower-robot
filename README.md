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

## Code

// -------- Pin Definitions --------
#define R_S 2     // Right IR sensor
#define L_S 3     // Left IR sensor

#define in1 4 //Right Motor Forward Pin
#define in2 5 //Right Motor Backward Pin
#define in3 6 //Left Motor Backward Pin
#define in4 7 //Left Motor Forward Pin

#define enA 9 //Used to power the Right Motor Pins
#define enB 10 //Used to power the Left Motor Pins

void setup() {
  // The input and output sets the usage so we can obtain the appropriate result that we wish for.
  pinMode(R_S, INPUT);
  pinMode(L_S, INPUT);

  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(in3, OUTPUT);
  pinMode(in4, OUTPUT);

  pinMode(enA, OUTPUT);
  pinMode(enB, OUTPUT);

  digitalWrite(enA, HIGH);  // Enable motors
  digitalWrite(enB, HIGH);

  delay(1000);
}

void loop() {

  // Both sensors on white → go forward
  if ((digitalRead(R_S) == 0) && (digitalRead(L_S) == 0)) {
    forward();
  }

  // Right sensor on black, left on white → turn right
  else if ((digitalRead(R_S) == 1) && (digitalRead(L_S) == 0)) {
    turnRight();
  }

  // Right sensor on white, left on black → turn left
  else if ((digitalRead(R_S) == 0) && (digitalRead(L_S) == 1)) {
    turnLeft();
  }

  // Both sensors on black → stop
  else if ((digitalRead(R_S) == 1) && (digitalRead(L_S) == 1)) {
    Stop();
  }
}

// -------- Motor Functions --------

void forward() {
  digitalWrite(in1, HIGH); //Right Motor Forward Pin
  digitalWrite(in2, LOW); //Right Motor Backward Pin 
  digitalWrite(in3, LOW); //Left Motor Backward Pin
  digitalWrite(in4, HIGH); //Left Motor Forward Pin
}

void turnRight() {
  digitalWrite(in1, LOW);  //Right Motor Forward Pin
  digitalWrite(in2, HIGH); //Right Motor Backward Pin 
  digitalWrite(in3, LOW); //Left Motor Backward Pin
  digitalWrite(in4, HIGH); //Left Motor Forward Pin
}

void turnLeft() {
  digitalWrite(in1, HIGH); //Right Motor Forward Pin
  digitalWrite(in2, LOW); //Right Motor Backward Pin 
  digitalWrite(in3, HIGH); //Left Motor Backward Pin
  digitalWrite(in4, LOW); //Left Motor Forward Pin
}


void Stop() {
  digitalWrite(in1, LOW); //Right Motor Forward Pin
  digitalWrite(in2, LOW); //Right Motor Backward Pin 
  digitalWrite(in3, LOW); //Left Motor Backward Pin
  digitalWrite(in4, LOW); //Left Motor Forward Pin
}

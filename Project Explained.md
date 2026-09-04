# Smart-Car
Arduino and Python based smart safety car with line tracking, obstacle avoidance, automatic braking, and driver drowsiness detection.
Smart Safety Car

A group project that combines an Arduino-controlled car with Python-based driver monitoring to create a small smart vehicle with safety features.

The car can follow a line, detect obstacles, slow down, stop automatically, avoid obstacles, and return to the line. A camera-based drowsiness detection system also checks the driver's eyes and can control the car when signs of drowsiness are detected.

-------------------------------------

Project Overview
This was developed as a group project.

The main idea was to combine different sensors, an Arduino, and a Python program to create a car with basic autonomous and safety features.

The car has two main parts:

* **Car control system** – Arduino controls the motors, sensors, line tracking, and obstacle avoidance.
* **Driver monitoring system** – Python uses a camera to check the driver's eyes and detect possible drowsiness.

The Python program communicates with the Arduino through a serial connection. This allows the driver monitoring system to tell the car when it should drive normally, slow down, or stop.


-------------------------------------

 My Contribution

This was a group project, and my main responsibility was the software side of the project.

Software

I worked on:

* Arduino programming
* Python programming
* Driver drowsiness detection
* Eye detection using MediaPipe
* Communication between Python and Arduino
* Automatic car commands
* Telegram emergency alerts
* Voice warnings
* Camera monitoring interface
* Testing and adjusting the system

Hardware

I also helped with parts of the hardware setup, including working with:

* IR sensors
* Ultrasonic sensor
* Servo motor
* Motor driver
* DC motors
* Arduino
* Camera setup

The hardware and other parts of the project were completed together with the rest of the group.


-------------------------------------

#  Car Functions

##  1. Line Tracking

The car uses two IR sensors underneath the car to detect a line on the ground.

The sensors help the car decide whether it should:

* Move forward
* Turn left
* Turn right
* Stop

This allows the car to follow a planned path without needing someone to control the steering manually.


-------------------------------------

 2. Obstacle Detection

An ultrasonic sensor is placed at the front of the car.

It continuously checks how far away an object is.

The car has two distance levels:
if More than 35 cm,  Normal movement,           
if 15–35 cm, Slow down,                 
if 15 cm or less, Stop and avoid the obstacle

This helps the car react before hitting something in front of it.


-------------------------------------

 3. Automatic Slowdown

When an object gets closer than **35 cm**, the car reduces its speed.

This gives the car more time to react instead of continuing at its normal speed.


-------------------------------------

 4. Automatic Emergency Stop

If an object is detected within **15 cm**, the car stops.

The car then checks the surrounding area before deciding where to go.

This is one of the main safety features of the project.


-------------------------------------
 5. Obstacle Avoidance

The ultrasonic sensor is attached to a servo motor.

When the car stops because of an obstacle, the servo moves the sensor:

**Right > Left > Center**

The car measures the available space on both sides.

It then compares the two distances and turns toward the side with more space.

After turning, the car moves forward and searches for the line again.


-------------------------------------

 6. Return to Line

After avoiding an obstacle, the car does not simply continue driving randomly.

It checks the IR sensors while moving and tries to find the original line again.

Once the line is detected, normal line tracking can continue.


-------------------------------------

 Driver Drowsiness Detection

The project also includes a camera-based system that checks whether the driver may be falling asleep.

The system was built using **Python, OpenCV, and MediaPipe**.

The camera looks at the driver's face and tracks the eyes.

The program calculates an **Eye Aspect Ratio (EAR)** to estimate whether the eyes are open or closed.

### The system has three states:

 Normal

If the driver's eyes are open normally:


Driver Awake
     ↓
NORMAL
     ↓
Car continues normally


 Warning

If the driver's eyes stay closed for several frames:

---

Eyes closed
     ↓
Drowsiness detected
     ↓
SLOW
     ↓
Car slows down

---

Critical

If the eyes remain closed for longer:


Eyes closed for too long
          ↓
   Critical drowsiness
          ↓
        STOP
          ↓
     Car stops


This prevents the system from reacting to just one momentary blink.


-------------------------------------

 Python & Arduino Communication

Python communicates with the Arduino using a serial connection.

The Python program sends simple commands:


NORMAL
SLOW
STOP


The Arduino receives these commands and changes the car's behavior.
Python detects drowsiness > "SLOW" > Arduino > Car slows


If serious drowsiness is detected:


Python detects severe drowsiness > "STOP" > Arduino> Car stops


The program also avoids repeatedly sending the same command to the Arduino. It only sends a new command when the car's state changes.



-------------------------------------

 Telegram Emergency Alert

When serious driver drowsiness is detected, the system sends an emergency message through **Telegram**.

The message informs the selected Telegram account that:

- Driver drowsiness was detected
- The vehicle was automatically stopped
- The driver should be checked




-------------------------------------

Voice Warning

The Python program also uses text-to-speech to give the driver a warning.

When serious drowsiness is detected, the system gives a voice warning such as:

> "Wake up! Wake up! You are falling asleep!"

The voice warning runs separately so that it does not stop the camera detection.


-------------------------------------

 Driver Monitoring Dashboard

The Python program displays a live camera window.

It shows information such as:

EAR: 0.31
STATUS: AWAKE
Closed Frames: 0




When drowsiness is detected, the status changes to show a warning.

This makes it easier to see what the system is detecting while it is running.

---

 Hardware Used

- Arduino mega board
- DC motors
- L298N motor driver
- 2 IR line sensors
- Ultrasonic distance sensor
- Servo motor
- Robot car chassis
- Camera
- Computer/laptop
- Connecting wires
- Battery/power supply (alot of them testing phrase consumes lot of battery)



**Software Used**

**Arduino**

* Arduino IDE
* C/C++

**Python**

* Python
* OpenCV
* MediaPipe
* PySerial
* Requests
* Pyttsx3


Communication

USB Serial Communication
Telegram Bot API



How Everything Works Together

The whole system can be simplified like this:

 <img width="1222" height="1287" alt="image" src="https://github.com/user-attachments/assets/fd35a97c-387b-4e1f-bbe0-72c3e03feac2" />
   



this is the main hardware of the car.


<img width="700" height="420" alt="image" src="https://github.com/user-attachments/assets/16b2ea21-42b6-4e1e-a6be-2e09e5f4864e" />


**What I Learned**

This project gave me experience working with both software and hardware.

Some of the main things I learned were:

* Writing Arduino programs
* Working with sensors and motors
* Controlling a robot car
* Using Python with a camera
* Using OpenCV for image processing
* Using MediaPipe for face and eye tracking
* Detecting drowsiness using eye movement
* Sending commands between Python and Arduino
* Working with APIs
* Sending Telegram notifications
* Using text-to-speech
* Testing and fixing problems in a system where software and hardware depend on each other

One of the most useful parts of the project was learning how to connect different technologies together instead of working with just one program.

-------------------------------------

 Project Photos

Photos and screenshots of the car and software will be added here.

### Car

<img width="1280" height="1066" alt="image" src="https://github.com/user-attachments/assets/958f920f-fb6f-4fbd-bd52-ae2ab43cb48a" />

<img width="960" height="800" alt="image" src="https://github.com/user-attachments/assets/6af9648c-1114-4f53-aa18-2b0f9499b11c" />

## (also this project had a time limit so the exterior looks bad but i ensure you the functions works perfectly)






Reference

The driver drowsiness detection part of this project was developed with reference to the following tutorial:


[YouTube tutorial used as reference]([https://youtu.be/oRetfsmyu1s](https://youtu.be/oRetfsmyu1s))

The tutorial helped me understand how eye detection and drowsiness detection could be done using Python, OpenCV, and MediaPipe.

I then adapted the idea for this project and connected the drowsiness detection system to the Arduino car so that detected drowsiness could affect the vehicle's behavior.

The other parts of the project, including the line tracking, obstacle detection, obstacle avoidance, automatic stopping, Python-Arduino communication, Telegram alerts, and overall system integration, were developed as part of our group project.



 Note

This project was created as an **educational group project** and is a prototype demonstrating basic vehicle safety and automation features.

It should not be treated as a real-world vehicle safety system. (also this project had a time limit so the exterior looks bad but i ensure you the functions works perfectly)


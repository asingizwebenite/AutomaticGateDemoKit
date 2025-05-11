 #Automatic Gate System with Ultrasonic Sensor
This Arduino project simulates an automatic gate that opens when an object (such as a person or vehicle) approaches within a certain distance, and closes automatically after a few seconds if no object is detected.

 #Components Used
Arduino board (e.g., Uno)

Ultrasonic Sensor (HC-SR04)

Servo Motor

Red and Blue LEDs

Buzzer

Jumper wires

Breadboard

# Pin Configuration
Component	Arduino Pin
Ultrasonic Trigger	2
Ultrasonic Echo	3
Red LED (+)	4
Red LED (-)	8 (acts as GND)
Blue LED (+)	5
Blue LED (-)	7 (acts as GND)
Servo Motor	6
Buzzer	12

# Working Principle
The ultrasonic sensor continuously measures distance in front of the gate.

If an object is detected within 50 cm, the gate:

Opens via the servo motor.

Red LED turns OFF, Blue LED turns ON.

Buzzer sounds to signal the presence.

If the object moves away or is no longer detected for more than 5 seconds:

The gate closes.

Red LED turns ON, Blue LED turns OFF.

Buzzer turns OFF.

# How It Works (Logic Flow)
Starts with the gate closed (servo at 0°).

Continuously checks for objects.

Uses pulseIn() to get distance from ultrasonic sensor.

Gate opens only when an object comes close (less than 50 cm).

Uses a timer to determine when to close the gate (5 seconds after the object is no longer detected).

LEDs and buzzer give visual and audio feedback of the state.

# Code Explanation Highlights
getDistance(): Calculates the distance using the ultrasonic sensor.

loop(): Main logic for detecting object, opening/closing gate, and controlling LEDs and buzzer.

Uses non-blocking timing with millis() instead of delay() to control gate closing logic.

# Output Behavior
Condition	Gate	Red LED	Blue LED	Buzzer
No object nearby	Closed	ON	OFF	OFF
Object within 50 cm	Open	OFF	ON	ON

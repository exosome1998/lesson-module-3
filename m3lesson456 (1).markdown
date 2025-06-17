# Combined Lesson: Sensors, Actuators, and Servo Motor Control

## Overview
Welcome to an exciting journey into the world of sensors, actuators, and servo motor control! This combined lesson builds on your Wokwi experience with LEDs and introduces you to the core components that bring mechatronic systems to life. You’ll explore how sensors detect the environment, actuators respond to commands, and servo motors enable precise movement. Through step-by-step theory, interactive questions, and hands-on code exercises, you’ll simulate these elements using Wokwi, deepening your understanding of Arduino programming.

## Learning Intention
- Understand the roles of sensors and actuators in mechatronic systems.
- Simulate motion and environmental sensors (PIR, accelerometer, ultrasonic, light).
- Program and control servo motors in a simulated environment.

## Success Criteria
- I can explain the purpose and examples of sensors and actuators.
- I can simulate and interpret data from motion and environmental sensors.
- I can program a servo motor to perform specific movements.

---

## Theory: Foundations of Sensors, Actuators, and Control

### What Are Sensors and Actuators?
- **Sensors**: Devices that detect changes in the environment and convert them into electrical signals. They are the “eyes and ears” of a mechatronic system, providing data for decision-making.
  - **Examples**: PIR (motion), accelerometer (acceleration), ultrasonic (distance), light (intensity).
  - **Role**: Sensors feed real-time information to the microcontroller, enabling responsive behavior (SE-11-03).
- **Actuators**: Components that convert electrical signals into physical actions. They are the “muscles” of the system, executing commands from the microcontroller.
  - **Examples**: Motors, LEDs, servo motors.
  - **Role**: Actuators perform tasks like movement or illumination based on processed sensor data (SE-11-01).

### How Sensors and Actuators Work Together
- **Interaction**: Sensors collect data (e.g., motion detected by a PIR), the microcontroller processes it with software, and actuators respond (e.g., a servo motor moves).
- **Example**: In a smart security system, a PIR sensor detects motion, the Arduino decides if it’s a threat, and a servo motor locks a door.
- **Importance**: This feedback loop is fundamental to automation, requiring precise programming (SE-11-08).

### Types of Sensors: Motion and Environmental
- **PIR (Passive Infrared) Sensor**: Detects motion by sensing infrared radiation from moving objects (e.g., humans).
  - **Use Case**: Security systems to trigger alarms.
- **Accelerometer**: Measures acceleration or tilt in multiple axes (e.g., X, Y, Z).
  - **Use Case**: Fitness trackers to count steps.
- **Ultrasonic Sensor**: Measures distance using sound waves, calculating the time for echoes to return.
  - **Use Case**: Parking sensors in cars.
- **Light Sensor (Photoresistor)**: Detects light intensity, changing resistance based on brightness.
  - **Use Case**: Automatic streetlights.

### Actuators: Focusing on Servo Motors
- **Definition**: Servo motors are actuators that provide precise angular movement, controlled by pulse-width modulation (PWM) signals.
- **Components**: Include a motor, gear train, and control circuitry.
- **Applications**: Robotic arms, camera pan-tilts, remote-controlled cars.
- **Control**: The Arduino sends PWM signals to set the motor’s position (e.g., 0° to 180°).

### Programming for Sensors and Actuators
- **Arduino Role**: The Arduino Uno reads sensor data via analog or digital pins and sends commands to actuators through PWM or digital outputs.
- **Debouncing**: Ensures clean input from buttons or sensors by filtering rapid signal changes.
- **Simulation**: Wokwi allows virtual testing, mimicking real hardware behavior.

---

## Interactive Questions

### Multiple-Choice Questions
Write your answer ('a', 'b', 'c', or 'd') in the box below each question. Compare with the answer key at the end.

#### Question 1: What is the primary role of a sensor in a mechatronic system?
- a) To execute physical actions
- b) To detect environmental changes
- c) To store program data
- d) To power the system

**Your Answer:**
```
(Type your answer here: a, b, c, or d)
```

#### Question 2: Which actuator provides precise angular control?
- a) LED
- b) Servo motor
- c) Buzzer
- d) Relay

**Your Answer:**
```
(Type your answer here: a, b, c, or d)
```

### Short-Answer Questions
Write detailed responses in the boxes below to demonstrate your understanding.

#### Question 3: Describe the difference between a sensor and an actuator, and provide one example of each.
**Your Answer:**
```
(Type your response here)
```

#### Question 4: Explain how an ultrasonic sensor works to measure distance, including its practical use.
**Your Answer:**
```
(Type your response here)
```

#### Question 5: What is a servo motor, and how does it differ from a regular motor in terms of control?
**Your Answer:**
```
(Type your response here)
```

---

## Hands-On Exercises: Simulating Sensors and Actuators in Wokwi

### Exercise 1: Setting Up Wokwi for Sensor Simulation
Let’s simulate a basic sensor setup. Follow these steps:

1. **Log In**: Go to [Wokwi](https://wokwi.com/) and sign in with GitHub.
2. **New Project**: Click **"New Project"**, then select **"Arduino Uno"**.
3. **Add a PIR Sensor**:
   - Click the **"+"** button, search for **"PIR Sensor"**, and place it.
   - Connect the **VCC** to 5V, **GND** to GND, and **OUT** to pin 2.
4. **Add Code**: Use this sketch to detect motion:
   ```cpp
   const int pirPin = 2;    // PIR sensor output pin
   int pirState = LOW;      // Motion detection state

   void setup() {
     pinMode(pirPin, INPUT); // Set PIR pin as input
     Serial.begin(9600);     // Start serial monitor
   }

   void loop() {
     int reading = digitalRead(pirPin);
     if (reading == HIGH && pirState == LOW) {
       Serial.println("Motion detected!");
       pirState = HIGH;
     } else if (reading == LOW && pirState == HIGH) {
       Serial.println("Motion ended.");
       pirState = LOW;
     }
     delay(100); // Small delay to debounce
   }
   ```
5. **Run and Observe**: Click **"Start"**, then open the Serial Monitor to see motion detection messages.
6. **Experiment**: Change `delay(100)` to `delay(500)` and note the difference.

**Your Observations:**
```
(Type your observations here)
```

### Exercise 2: Simulating an Accelerometer
Simulate an accelerometer to measure tilt.

1. **Add Components**: Add an **"Accelerometer (ADXL335)"** (search in Wokwi).
   - Connect **VCC** to 5V, **GND** to GND, **X** to A0, **Y** to A1, **Z** to A2.
2. **Add Code**: Use this sketch:
   ```cpp
   const int xPin = A0;  // X-axis pin
   const int yPin = A1;  // Y-axis pin
   const int zPin = A2;  // Z-axis pin

   void setup() {
     Serial.begin(9600); // Start serial
   }

   void loop() {
     int xValue = analogRead(xPin);
     int yValue = analogRead(yPin);
     int zValue = analogRead(zPin);
     Serial.print("X: "); Serial.print(xValue);
     Serial.print(" Y: "); Serial.print(yValue);
     Serial.print(" Z: "); Serial.println(zValue);
     delay(500); // Update every 0.5 seconds
   }
   ```
3. **Run and Tilt**: Click **"Start"**, tilt the virtual accelerometer in Wokwi, and watch the Serial Monitor.
4. **Experiment**: Adjust `delay(500)` to `delay(1000)` and compare refresh rates.

**Your Observations:**
```
(Type your observations here)
```

### Exercise 3: Simulating an Ultrasonic Sensor
Measure distance with an ultrasonic sensor.

1. **Add Components**: Add an **"Ultrasonic Sensor (HC-SR04)"**.
   - Connect **VCC** to 5V, **GND** to GND, **Trig** to pin 9, **Echo** to pin 10.
2. **Add Code**: Use this sketch:
   ```cpp
   const int trigPin = 9;  // Trigger pin
   const int echoPin = 10; // Echo pin
   long duration;
   int distance;

   void setup() {
     pinMode(trigPin, OUTPUT);
     pinMode(echoPin, INPUT);
     Serial.begin(9600);
   }

   void loop() {
     digitalWrite(trigPin, LOW);
     delayMicroseconds(2);
     digitalWrite(trigPin, HIGH);
     delayMicroseconds(10);
     digitalWrite(trigPin, LOW);
     duration = pulseIn(echoPin, HIGH);
     distance = duration * 0.034 / 2; // Speed of sound = 0.034 cm/us
     Serial.print("Distance: ");
     Serial.print(distance);
     Serial.println(" cm");
     delay(500);
   }
   ```
3. **Run and Test**: Click **"Start"**, adjust the virtual distance in Wokwi, and check the Serial Monitor.
4. **Experiment**: Modify the `delay(500)` to `delay(100)` and observe the update frequency.

**Your Observations:**
```
(Type your observations here)
```

### Exercise 4: Simulating a Light Sensor
Control an LED based on light intensity.

1. **Add Components**: Add a **"Photoresistor"** and an **"LED"**.
   - Connect Photoresistor to A0 and GND (with a 10k resistor to 5V).
   - Connect LED anode to pin 13, cathode to GND.
2. **Add Code**: Use this sketch:
   ```cpp
   const int lightPin = A0;  // Photoresistor pin
   const int ledPin = 13;    // LED pin
   int lightValue;

   void setup() {
     pinMode(ledPin, OUTPUT);
     Serial.begin(9600);
   }

   void loop() {
     lightValue = analogRead(lightPin);
     Serial.print("Light value: ");
     Serial.println(lightValue);
     if (lightValue < 500) {
       digitalWrite(ledPin, HIGH); // LED on in low light
     } else {
       digitalWrite(ledPin, LOW);  // LED off in bright light
     }
     delay(500);
   }
   ```
3. **Run and Adjust**: Click **"Start"**, vary the virtual light level in Wokwi, and observe the LED and Serial Monitor.
4. **Experiment**: Change the threshold `500` to `300` and test the sensitivity.

**Your Observations:**
```
(Type your observations here)
```

### Exercise 5: Simulating Servo Motor Control
Control a servo motor’s position.

1. **Add Components**: Add a **"Servo Motor"**.
   - Connect **VCC** to 5V, **GND** to GND, **Signal** to pin 9.
2. **Add Code**: Use this sketch:
   ```cpp
   #include <Servo.h>
   Servo myServo;           // Create servo object
   const int servoPin = 9;  // Servo signal pin

   void setup() {
     myServo.attach(servoPin); // Attach servo to pin
     Serial.begin(9600);
   }

   void loop() {
     myServo.write(0);      // Move to 0 degrees
     Serial.println("Servo at 0 degrees");
     delay(1000);
     myServo.write(90);     // Move to 90 degrees
     Serial.println("Servo at 90 degrees");
     delay(1000);
     myServo.write(180);    // Move to 180 degrees
     Serial.println("Servo at 180 degrees");
     delay(1000);
   }
   ```
3. **Run and Observe**: Click **"Start"**, watch the servo move, and check the Serial Monitor.
4. **Experiment**: Modify the angles (e.g., `45`, `135`) and `delay(1000)` to `delay(500)`, then test.

**Your Observations:**
```
(Type your observations here)
```

---

## Answers

### Multiple-Choice Answers
- **Question 1**: b) To detect environmental changes
- **Question 2**: b) Servo motor

### Short-Answer Answers
- **Question 3**: A sensor detects changes (e.g., a PIR sensor for motion), while an actuator responds (e.g., a servo motor for movement). Example: PIR in security, servo in robotics.
- **Question 4**: An ultrasonic sensor emits sound waves, measures the echo time, and calculates distance (e.g., distance = time × speed of sound / 2). Used in parking sensors to avoid obstacles.
- **Question 5**: A servo motor provides precise angular control via PWM signals, unlike a regular motor which offers continuous rotation. Used in robotic arms for exact positioning.

### Reflection Answer
- Manufacturing uses microcontrollers to control robotic arms, improving precision and reducing human error in production.

---
# Bluetooth Robot Car

This project is a Bluetooth-controlled robot car that can move forward, backward, turn left, and turn right based on commands received via a Bluetooth module. The car is powered by an Arduino Uno and uses an H Bridge DC Stepper Motor Controller (L298N) to control the motors.

## Tools and Components

- **Arduino Uno**
- **H Bridge DC Motor Controller L298N Module**
- **2 DC motors and wheels**
- **Bluetooth module**
- **Battery (12V) or powerbank**

## Application used to control you Car-Robot using a mobile
- Arduino Bluetooth  Control
- OR
- RemoteXY

## Code

```cpp
char cmd; // The Bluetooth Command

// The L298N Control Pins
const int rightMotorForward = 2;
const int rightMotorBackward = 3;
const int leftMotorForward = 4;
const int leftMotorBackward = 5;

void setup() {
  pinMode(leftMotorForward, OUTPUT);   // left motor forward
  pinMode(leftMotorBackward, OUTPUT);  // left motor reverse
  pinMode(rightMotorForward, OUTPUT);  // right motor forward
  pinMode(rightMotorBackward, OUTPUT); // right motor reverse
  Serial.begin(9600);
}

void loop() {
  if (Serial.available()) {
    cmd = Serial.read();
  }

  if (cmd == 'F') { // move forward
    digitalWrite(leftMotorForward, HIGH);
    digitalWrite(rightMotorForward, HIGH);
    digitalWrite(leftMotorBackward, LOW;
    digitalWrite(rightMotorBackward, LOW);
  } else if (cmd == 'B') { // move reverse
    digitalWrite(leftMotorBackward, HIGH);
    digitalWrite(rightMotorBackward, HIGH);
    digitalWrite(leftMotorForward, LOW);
    digitalWrite(rightMotorForward, LOW);
  } else if (cmd == 'L') { // turn Left
    digitalWrite(rightMotorForward, HIGH);
  } else if (cmd == 'R') { // turn Right
    digitalWrite(leftMotorForward, HIGH);
  } else { // STOP (all motors stop)
    digitalWrite(leftMotorForward, LOW);
    digitalWrite(leftMotorBackward, LOW);
    digitalWrite(rightMotorForward, LOW);
    digitalWrite(rightMotorBackward, LOW);
  }
  delay(50);
}

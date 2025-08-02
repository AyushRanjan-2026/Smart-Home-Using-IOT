Description
This project is a multi-functional Internet of Things (IoT) solution built on the ESP32 microcontroller platform. It integrates various sensors to collect real-time environmental and physical data, which is then sent to the Blynk cloud application for remote monitoring and control. The system is designed to automate common tasks, such as managing water levels and controlling a smart garden, demonstrating practical applications of embedded systems and cloud integration.

Features
Remote Monitoring: Real-time data from a DHT11 sensor (temperature/humidity), ultrasonic sensor (distance), and soil moisture sensor is sent to the Blynk app.

Water Tank Management: An ultrasonic sensor measures the water level, and the data is used to control a servo motor (simulating a valve) and a relay (for a pump) to manage water levels.

Smart Garden Automation: A soil moisture sensor automatically triggers a relay to turn a water pump on or off, ensuring the soil remains adequately hydrated.

Remote Control: Actuators like a fan and a bulb can be remotely controlled through the Blynk application's virtual pins.

Visual Feedback: An RGB LED provides visual status indications based on sensor readings.

Easy Setup: The system is configured to connect to a Wi-Fi network and a Blynk project using simple credentials.

Tech Stack
Microcontroller: ESP32

Language: C++ (with Arduino framework)

Cloud Platform: Blynk

Sensors: Ultrasonic Sensor, DHT11 (Temperature & Humidity), Soil Moisture Sensor, LDR

Actuators: Relay Module, Servo Motor, RGB LED

Connectivity: Wi-Fi

Setup and Installation
Prerequisites
Arduino IDE or Visual Studio Code with the PlatformIO extension.

ESP32 board.

Blynk account and mobile application.

Required sensors and actuators (e.g., DHT11, ultrasonic sensor, relay, servo motor).

Instructions
Install Libraries: Open your Arduino IDE or PlatformIO and install the necessary libraries:

BlynkSimpleEsp32.h

ESP32Servo.h

DHT.h

Configure Blynk:

Create a new project in the Blynk app.

Get your BLYNK_AUTH_TOKEN, BLYNK_TEMPLATE_ID, and BLYNK_TEMPLATE_NAME.

Update the corresponding values in the C++ code files.

Update Wi-Fi Credentials:

In the code, replace ssid[] and pass[] with your Wi-Fi network name and password.

Hardware Connections:

Connect the sensors and actuators to the specified pins on the ESP32 as defined in the code files.

Ensure proper power supply for the ESP32 and all components.

Upload Code:

Open the desired code file (LDR,DHT INTEGRATION, Moisture_sensor, etc.) in your IDE.

Select your ESP32 board and port.

Upload the code to your ESP32.

Run:

Open the Serial Monitor to view sensor data and debug messages.

Use the Blynk app to remotely monitor sensor readings and control the actuators.

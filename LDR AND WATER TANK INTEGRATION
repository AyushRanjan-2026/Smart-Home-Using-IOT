#define BLYNK_TEMPLATE_ID "TMPL6Bv4K8KDp"
#define BLYNK_TEMPLATE_NAME "water tank"
#define BLYNK_AUTH_TOKEN "00InV81eYnRYO9E2A8xzy9AEEUWIq1Ep"

#include <ESP32Servo.h>
#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>

Servo riya;
#define SERVO_PIN 33
const int relayPin = 13;
// Ultrasonic Sensor
#define TRIG_PIN 5
#define ECHO_PIN 18

// Blynk settings
#define BLYNK_PRINT Serial

// WiFi credentials
char auth[] = BLYNK_AUTH_TOKEN;
char ssid[] = "realme C30";     // Type your WiFi name
char pass[] = "86d20877";   // Type your WiFi password

BlynkTimer timer;
//fan

void setup() {
  Serial.begin(115200);
  Serial.println(F("Starting the setup"));
  
  Blynk.begin(auth, ssid, pass);
  riya.attach(SERVO_PIN);
  
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(relayPin, OUTPUT);
  timer.setInterval(1000L, sendSensorData); // Call sendSensorData every second
}
//BULB
BLYNK_WRITE(V1)
{
  int pinValue = param.asInt(); // Get the value of the virtual pin V1

  // Control the relay
  if (pinValue == 1)
  {
    digitalWrite(relayPin, HIGH); // Turn on relay (and bulb)
    Serial.println("Bulb is ON via Blynk");
  }
  else
  {
    digitalWrite(relayPin, LOW); // Turn off relay (and bulb)
    Serial.println("Bulb is OFF via Blynk");
  }
}
//FAN
BLYNK_WRITE(V0)
{
  int pinValue = param.asInt(); // Get the value of the virtual pin V1

  // Control the relay
  if (pinValue == 1)
  {
    digitalWrite(relayPin, HIGH); // Turn on relay (and fan)
    Serial.println("Fan is ON");
  }
  else
  {
    digitalWrite(relayPin, LOW); // Turn off relay (and fan)
    Serial.println("Fan is OFF");
  }
}
void sendSensorData() {
  long duration, distance;
  
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);
  
  duration = pulseIn(ECHO_PIN, HIGH);
  // Calculate distance
  distance = (duration / 2) * 0.0343; // Convert duration to distance in centimeters
  
  Serial.print("Distance: ");
  Serial.println(distance);
  
  Blynk.virtualWrite(V4, distance);
  if (distance >= 0 && distance <= 2) {
    riya.write(0);
  } else {
   for(int i=0;i<180;i++){
      riya.write(i);
    }
    for(int i=180;i>=0;i--){
      riya.write(i);
    }
    delay(10);
  }
}
void checkLDR()
{
  ldrValue = analogRead(ldrPin);
  Serial.print("LDR Value: ");
  Serial.println(ldrValue);

  // Control the relay based on LDR value
  if (ldrValue < threshold)
  {
    digitalWrite(relayPin, HIGH); // Turn on relay (and bulb)
    Serial.println("Bulb is ON due to low light");
  }
  else
  {
    digitalWrite(relayPin, LOW); // Turn off relay (and bulb)
    Serial.println("Bulb is OFF due to sufficient light");
  }
}
void loop() {
  Blynk.run();
  checkLDR();
  sendSensorData();
  timer.run();
}

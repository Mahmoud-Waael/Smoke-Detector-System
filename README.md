# Smoke Detector System

An embedded system project for detecting smoke using an Arduino UNO, MQ-2 sensor, buzzer, and LED.

## Project Overview

This project aims to monitor smoke levels in the environment and trigger an alert when the smoke level exceeds a defined threshold. It serves as a basic prototype for safety and fire alert systems.

## Components Used

- Arduino UNO
- MQ-2 Smoke Sensor
- Buzzer
- LED
- Jumper wires
- Breadboard (optional)

## How It Works

1. The MQ-2 sensor continuously reads analog smoke levels.
2. If the smoke level is below the threshold (400), the system remains silent.
3. If the level exceeds the threshold:
   - The buzzer sounds an alarm.
   - The LED blinks to visually indicate danger.

## Code (Arduino C)

```cpp
#define smoke  A0  
#define buzzer  2  
#define led  3 
#define fan 4
float data ;
int flag = 400 ;

void setup() {
  Serial.begin(9600);
  pinMode(smoke, INPUT);
  pinMode(led, OUTPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(fan, OUTPUT);
  digitalWrite(fan, LOW);
  digitalWrite(led, LOW);
  digitalWrite(buzzer, LOW);
}

void loop() {
  data = analogRead(A0);

  if(data < flag){
    digitalWrite(buzzer, LOW);
    digitalWrite(led, LOW);
    digitalWrite(fan, LOW);
  }
  else if(data >= flag){
    digitalWrite(buzzer, HIGH);
    delay(200);
    digitalWrite(led, HIGH);
    delay(200);
    digitalWrite(buzzer, LOW);
    delay(200);
    digitalWrite(led, LOW);
    delay(200);
  }
}
```

## Future Improvements

- Add an LCD to display real-time smoke levels.
- Integrate a Wi-Fi module (ESP8266) to send alerts to a mobile app.
- Power the system with a rechargeable battery.
- Add a user interface with control buttons or multi-level indicators.

## Project Image

![Smoke Detector](project_image.jpg)

---

**Created by:** Mahmoud Waael

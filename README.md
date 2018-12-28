# homebridge-mqtt-433-sensor

This plugin is based on [homebridge-mqtt-sonoffrf-receiver](https://github.com/miskui/homebridge-mqtt-sonoffrf-receiver). Thanks for [miskui](https://github.com/miskui).

Get Motion Sensor status via MQTT in Homebridge using [Sonoff RF Bridge 433](https://www.itead.cc/sonoff-rf-bridge-433.html) with [TasmOTA firmware](https://github.com/arendst/Sonoff-Tasmota/wiki).
Motion sensor is activated when received RF code matches for rfcode or RF key stored in Sonoff RF Bridge. Open Sonoff RF Bridge console to read out received RF codes as hexadecimal values in DATA field. Use these values in rfcode parameter or use rfkey if you have already defined RF codes in Sonoff RF Bridge. Value 'any' will activate the sensor if any RF code received. Use rfcodeon and rfcodeoff parameters if your sensor sends both on and off states.
Sensor can be [motion sensor](https://www.itead.cc/sonoff-rf-bridge-433.html), [RF button](https://www.aliexpress.com/item/86-Wall-Panel-Wireless-Remote-Transmitter-1-2-3-Channel-Sticky-RF-TX-Smart-For-Home/32793117889.html?spm=a2g0s.9042311.0.0.nUq3pZ), [Contact sensor](https://www.aliexpress.com/item/SECRUI-D026-Window-Door-Magnet-Sensor-Detector-Portable-Alarm-Sensors-Smart-Home-Detectors-Wireless-For-SECRUI/32891067687.html) or any other RF sensor.

Installation
--------------------
     npm install -g https://github.com/mientki/homebridge-mqtt-433-sensor.git

Sample HomeBridge Configuration
--------------------

        {
          "accessory": "mqtt-433-sensor",
          "name": "Sensor 1",
          "url": "mqtt://localhost",
          "topic": "tele/sonoff_rf/RESULT",
          "username": "username",
          "password": "password",
          "rfcode": "7FFFFF" or "any",
          "rfkey": "1..16" or "any",
          "ondelay": "10000", (time in ms while the sensor is active, the default is 10000)
          "rfcodeon": "7FFFFF",
          "rfcodeoff": "8FFFFF",
          "accessoryservicetype": "MotionSensor" or "StatelessProgrammableSwitch" or "ContactSensor" or "SmokeSensor" or "LeakSensor"
        }

Supported sensors (accessory service type)
--------------------
- Motion sensor
- Contact sensor (windows, doors, contact sensor, blinds, opening garage door)
- Smoke sensor
- Leak sensor
- Stateless programmable switch

Release notes
--------------------
Version 0.1.7
- bugs fixed
- added smoke sensor
- added leak sensor

Version 0.1.6
- added contact sensor
- added tampered status (not yet)
- added low battery status (not yet)

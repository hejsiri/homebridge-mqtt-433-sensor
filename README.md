# homebridge-mqtt-433-sensor

This plugin is based on [homebridge-mqtt-sonoffrf-receiver](https://github.com/miskui/homebridge-mqtt-sonoffrf-receiver). Thanks for [miskui](https://github.com/miskui).

Get Motion Sensor status via MQTT in Homebridge using [Sonoff RF Bridge 433](https://www.itead.cc/sonoff-rf-bridge-433.html) with [TasmOTA firmware](https://github.com/arendst/Sonoff-Tasmota/wiki).
Motion sensor is activated when received RF code matches for rfcode or RF key stored in Sonoff RF Bridge. Open Sonoff RF Bridge console to read out received RF codes as hexadecimal values in DATA field. Use these values in rfcode parameter or use rfkey if you have already defined RF codes in Sonoff RF Bridge. Value 'any' will activate the sensor if any RF code received. Use rfcodeon and rfcodeoff parameters if your sensor sends both on and off states.
Sensor can be [motion sensor](https://www.itead.cc/sonoff-rf-bridge-433.html), [RF button](https://www.aliexpress.com/item/86-Wall-Panel-Wireless-Remote-Transmitter-1-2-3-Channel-Sticky-RF-TX-Smart-For-Home/32793117889.html?spm=a2g0s.9042311.0.0.nUq3pZ), [Contact sensor](https://www.aliexpress.com/item/SECRUI-D026-Window-Door-Magnet-Sensor-Detector-Portable-Alarm-Sensors-Smart-Home-Detectors-Wireless-For-SECRUI/32891067687.html) or any other RF sensor.

Default configuration times:
- ondelay 10000 ms
- ondelaylowbattery 30000 ms

Installation
--------------------
     npm install -g https://github.com/mientki/homebridge-mqtt-433-sensor.git

Sample HomeBridge Configuration
--------------------

        {
            "accessory": "mqtt-433-sensor",
            "url": "mqtt://localhost",
            "topic": "tele/rf-bridge/RESULT",
            "username": "username",
            "password": "password",
            "rfcodeon": "2E1A11",
            "rfcodeoff": "2E1A12",
            "rfcodelowbattery": "2E1A14",
            "accessoryservicetype": "ContactSensor",
            "name": "Contact Sensor"
        },
        {
            "accessory": "mqtt-433-sensor",
            "url": "mqtt://localhost",
            "topic": "tele/rf-bridge/RESULT",
            "username": "username",
            "password": "password",
            "rfcode": "2E1A21",
            "ondelay": "30000",
            "rfcodelowbattery": "2E1A22",
            "accessoryservicetype": "MotionSensor",
            "name": "Motion Sensor"
        },
        {
            "accessory": "mqtt-433-sensor",
            "url": "mqtt://localhost",
            "topic": "tele/rf-bridge/RESULT",
            "username": "username",
            "password": "password",
            "rfcode": "2E1A21",
            "ondelay": "10000",
            "rfcodelowbattery": "2E1A22",
            "accessoryservicetype": "LeakSensor",
            "name": "Leak Sensor"
        },
        {
            "accessory": "mqtt-433-sensor",
            "url": "mqtt://localhost",
            "topic": "tele/rf-bridge/RESULT",
            "username": "username",
            "password": "password",
            "rfcode": "2E1A21",
            "ondelay": "60000",
            "rfcodelowbattery": "2E1A22",
            "accessoryservicetype": "SmokeSensor",
            "name": "Smoke Sensor"
        },
        {
            "accessory": "mqtt-433-sensor",
            "url": "mqtt://localhost",
            "topic": "tele/rf-bridge/RESULT",
            "username": "username",
            "password": "password",
            "rfcode": "2E1A21",
            "ondelay": "10000",
            "rfcodelowbattery": "2E1A22",
            "accessoryservicetype": "StatelessProgrammableSwitch",
            "name": "RF Button"
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
Version 0.1.11
- bugs fixed
- added Low battery status

Version 0.1.7
- bugs fixed
- added smoke sensor
- added leak sensor

Version 0.1.6
- added contact sensor

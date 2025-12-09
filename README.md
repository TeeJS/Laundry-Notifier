# Laundry-Notifier
![project image](https://github.com/TeeJS/Laundry-Notifier/blob/main/images/PXL_20251209_004040392.jpg)
a Home Assistant project to provide laundry notifications

ESPHome device that sets a laundry user that in conjunction with a power sensor on the washer and vibration sensor on the dryer sends out Discord messages when the laundry is done. 

##  Features
uses sensors to monitor the laundry machines (I use power for the washer and vibration for the drier).  Sets a "user" based on button presses and sends a @ mention to them - although I'm sure you could configure it to use your messaging platform of choice!

##  Components and Parts List
This project requires several components, including an ESPHome controller, sensors for the washer and dryer

A **full, detailed Bill of Materials (BOM)**, including specific product links and cost estimates, can be found here:

[**View the Complete BOM**](docs/BOM.md)

##  Setup and Installation

### 1. 3D Model Printing (Hardware)
The case is largley based on the ESP32 case by Grunt at:  https://www.printables.com/model/351248-esp32-wroom-32d-dupont-case/files  
I created it in TinkerCAD, you can copy it here: https://www.tinkercad.com/things/4x3nxkDhDTt-laundry-monitor-esphome-103 if you'd like to make your own modifications.  I'm sure most of the world is a better designer than me :)
I left the ESP32 modular as I plan on adding a mount for the temperature sensor and possibly a motion sesnor in the future

main base with screen and button mounts: [**download the main base with screen and button mounts**](3d-models/main%20base%20with%20screen%20and%20button%20mounts%20v1.03.stl)  
main lid: [**download the main lid**](3d-models/main%20lid%20v1.03.stl)  
ESP32 base: [**download the ESP32 base**](3d-models/ESP32%20base%20v1.03.stl)  
ESP32 carrier: [**download the ESP32 carrier**](3d-models/ESP32%20carrier%20v1.03.stl)  
SP32 lid: [**download the ESP32 lid**](3d-models/main%20lid%20v1.03.stl)  
breadboard dummy (if you want to change mounting location): [**download the breadboard dummy**](3d-models/breadboard%20dummy.stl)  


### 2. ESPHome Configuration (Firmware)
The ESPHome displays the local humidity & temp from the sensor, local weather (from OpenWeathermap) and users. The complete file can be found here:
[**View the YAML file**](docs/esphome.yaml)  

You'll need to set up the normal networkng stuff, as well as your own weather entity id in place of: weather.your_house_ID. Setting up OpenWeathermap is beyond the scope of this project - more deatils at: https://www.home-assistant.io/integrations/openweathermap/  
It wouldn't be hard to strip the temperature or weather out if wanted - I'm sure your AI of choice could help.

### 2. ESPHome Configuration (WIRING)
Here is the high level overview of the connections:  
| Component | Interface | ESP32 GPIO Pin | Function |
| :--- | :--- | :--- | :--- |
| **OLED Display** (SSD1306) | I2C (SDA) | **GPIO 21** | Data Line |
| **OLED Display** (SSD1306) | I2C (SCL) | **GPIO 22** | Clock Line |
| **SHT3xD** Temp/Humidity Sensor | I2C (SDA) | **GPIO 21** | Data Line (Shared with Display) |
| **SHT3xD** Temp/Humidity Sensor | I2C (SCL) | **GPIO 22** | Clock Line (Shared with Display) |
| **User Button T.J.** | GPIO (Input) | **GPIO 25** | Input |
| **User Button John** | GPIO (Input) | **GPIO 26** | Input |
| **User Button Paul** | GPIO (Input) | **GPIO 27** | Input |
| **User Button Ringo** | GPIO (Input) | **GPIO 14** | Input |

See more at [**ESP32 Wiring**](docs/esp32_wiring.md)

### 4. Home Assistant Configuration (Automation/Integration)
Home Assistant uses two automations:  
laundry_washer_done.yaml [**yaml source for washer**](docs/laundry_washer_done.yaml)  
laundry_dryer_done.yaml [**yaml source for dryer**](docs/laundry_washer_done.yaml)  
they assume you already have Discord (or your preferred messaging method) set up.  That's beyond the sope of this project, but more details at: https://www.home-assistant.io/integrations/discord/.  For both you'll need to set your own DISCORD_CHANNEL_ID and @DISCORD_USER_IDs as well as your sensor entity IDs.    
it also uses a binary sensor to make the vibration sensor a bit more reliable. it's state config (use your sensor entity id) is available here: [**yaml source for dryer binary sensor**](docs/dryer_running_state.yaml)

##  Licensing and Attribution
This repository contains two distinct types of content, each governed by a separate license:

1. Software and Configuration
All configuration files (.yaml), automation scripts, and documentation files (.md, .txt) are licensed under the MIT License.

This allows you maximum flexibility for reuse. You can view the full details in the root LICENSE file.

2. 3D Model Attribution (CC BY 4.0)
The 3D model files (found in the /3d-models directory) are licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

The license for these derivative files is CC BY 4.0 because the case design is largely based on an existing work, which requires attribution:

Original Work: "ESP32 WROOM 32D Dupont Case" by Grunt

Source: https://www.printables.com/model/351248-esp32-wroom-32d-dupont-case/files

##  Contributing

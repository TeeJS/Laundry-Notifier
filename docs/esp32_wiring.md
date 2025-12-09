here's the basic wiring structure again:

| Component | Interface | ESP32 GPIO Pin | Function |
| :--- | :--- | :--- | :--- |
| **OLED Display** (SSD1306) | I2C (SDA) | **GPIO 21** | Data Line |
| **OLED Display** (SSD1306) | I2C (SCL) | **GPIO 22** | Clock Line |
| **SHT3xD** Temp/Humidity Sensor | I2C (SDA) | **GPIO 21** | Data Line (Shared with Display) |
| **SHT3xD** Temp/Humidity Sensor | I2C (SCL) | **GPIO 22** | Clock Line (Shared with Display) |
| **User Button T.J.** | GPIO (Input) | **GPIO 25** | Input (Configured with **internal pull-up** and **inverted** logic) |
| **User Button John** | GPIO (Input) | **GPIO 26** | Input (Configured with **internal pull-up** and **inverted** logic) |
| **User Button Paul** | GPIO (Input) | **GPIO 27** | Input (Configured with **internal pull-up** and **inverted** logic) |
| **User Button Ringo** | GPIO (Input) | **GPIO 14** | Input (Configured with **internal pull-up** and **inverted** logic) |

What I did:  
I labeled one of the breadboards with rows: V (voltage), G (ground), A (SDA), and L (SDL)  
![labeled breadboard](https://github.com/TeeJS/Laundry-Notifier/blob/main/images/breadboard-s1.jpeg)  

I then connected the ESP32 pins: 3V3 to V, GND to G, 21 to A and 22 to L
![ESP32 connections](https://github.com/TeeJS/Laundry-Notifier/blob/main/images/esp-s1.jpg)  

I then connected the display to the corresponding connections in the breadboard  
![Display connections](https://github.com/TeeJS/Laundry-Notifier/blob/main/images/s2.jpg)    

and repeated the process (in the next row of the breadboard) for the temperature sensor  
![Display connections](https://github.com/TeeJS/Laundry-Notifier/blob/main/images/s3-sensor.jpg)    



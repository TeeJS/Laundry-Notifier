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
[![labeled breadboard](images/breadboard-1.jpeg)]

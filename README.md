# Temperature and Humidity Sensor to HTML

## 1. Description

The setup allows periodic readings from a DHT11 temperature and humidity sensor using an Arduino Uno development board and an Ethernet shield. Sensor readings (temperature and humidity) as well as computed values (heat indexes) could be accessed via a minimalist webpage hosted on a SD card. The webpage refreshes sensor data using AJAX and XML

Difficulty level: intermediate.

## 2. Parts

* 1 x Arduino Uno R3;
* 1 x Arduino Ethernet shield (W5100);
* 1 x DHT11;
* 1 x micro-SD card;
* Breadboard + wires.

## 3. Schematics

![Temperature and Humidity Sensor to HTML schem!](/res/schem.jpg "Temperature and Humidity Sensor to HTML schem")

## 4. Assembly (breadboard)

![Temperature and Humidity Sensor to HTML bboard!](/res/bboard.jpg "Temperature and Humidity Sensor to HTML bboard")

## 5. Code

The code implements a minimalist web server. It hosts a single web page (stored and loaded from the SD card) used to display useful data (sensor readings + computed values). The webpage data is updated using AJAX; an XML file containing the values to display is periodically sent from the Arduino to the client web browser.

* /src/index.htm – to be placed in the mini-SD card
* /src/htmlDHT11.ino – to be uploaded to Arduino

Note. ATmega328P-PU (Arduino Uno’s microcontroller) has 1KB SRAM memory for variables. htmlDHT11.ino includes several libraries that diminishes even more the available SRAM memory. Some recommended techniques to avoid SRAM memory saturation:
* store static strings (i.e. debugging messages) in flash memory. The size of this type of memory is 32KB for ATmega328P-PU; it’s purpose is to be used as program memory. This is the technique used in the htmlDHT11.ino sketch (usage of “F()” in some Serial.println statements);
* use conditional compiling;
* customize required libraries (strip-off whatever is not necessary).

## 6. Demo

Youtube link:  [Temperature and Humidity Sensor to HTML (Arduino Uno)](https://www.youtube.com/watch?v=GDF9GhkeBVM&t=7s)

## 7. Additional resources

* Libraries:
    * Adafruit Unified Sensor Driver:
    https://github.com/adafruit/Adafruit_Sensor
    * DHT-sensor-library:
    https://github.com/adafruit/DHT-sensor-library
    * SPI, Ethernet and SD standard libraries (included with the Arduino IDE)

* References:
    * DHT11 datasheet: https://cdn-learn.adafruit.com/downloads/pdf/dht.pdf
    * Arduino Ethernet shield (WT5100) datasheet:
    http://www.mouser.com/catalog/specsheets/A000056_DATASHEET.pdf
    * Arduino Ethernet Shield Web Server Tutorial:
    https://startingelectronics.org/tutorials/arduino/ethernet-shield-web-server-tutorial/
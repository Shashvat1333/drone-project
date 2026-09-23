DRONE WRINING DIAGRAMS
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
DRONE
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="660" height="627" alt="image" src="https://github.com/user-attachments/assets/f042e141-72d1-46f3-8e5f-3206d105e355" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

| Component | Component Wire / Pin | Flight Controller / ESC Pad | Function / Notes |
|---|---|---|---|
| XING-E Pro 2207 Motors (x4) | 3 Motor Power Wires (per motor) | ESC Motor Pads (corners of 4-in-1 ESC) | Solder the three wires from each motor directly to the ESC pads |
| SpeedyBee 4-in-1 ESC | ESC Ribbon Cable | SpeedyBee FC Ribbon Cable Port | Plugs directly into the flight controller to bridge power and data |
| Flywoo Molicell 6S Battery | XT60 Main Power Lead | ESC XT60 Power Pads | Main power supply for the entire stack |
| BN-880 GPS & Compass | TX | RX4 (Flight Controller) | GPS data transmit to FC receive |
| BN-880 GPS & Compass | RX | TX4 (Flight Controller) | GPS data receive to FC transmit |
| BN-880 GPS & Compass | SDA | SDA (Flight Controller) | Compass I2C data line |
| BN-880 GPS & Compass | SCL | SCL (Flight Controller) | Compass I2C clock line |
| BN-880 GPS & Compass | 5V / VCC | 4.5V or 5V (Flight Controller) | Power input for GPS |
| BN-880 GPS & Compass | GND | GND (Flight Controller) | Ground reference |
| DIYmalls LoRa ESP32 Board | TX | RX2 (Flight Controller) | Telemetry data transmit to FC receive |
| DIYmalls LoRa ESP32 Board | RX | TX2 (Flight Controller) | Telemetry data receive to FC transmit |
| DIYmalls LoRa ESP32 Board | 5V (or VIN) | 5V (Flight Controller) | Power input |
| DIYmalls LoRa ESP32 Board | GND | GND (Flight Controller) | Ground reference |

------------------------------------------------------------------------------------------------------------------------------------------------------------------
CONTROLLER
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="756" height="545" alt="image" src="https://github.com/user-attachments/assets/3891e9ce-8518-4966-8ca0-d34253f10c69" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Here is the updated controller wiring chart with both KY-023 joysticks powered by the 5V pin and the NRF24L01 module powered by the 3.3V pin:

| Component | Component Pin / Wire | LoRa Board Pin / Header | Function / Notes |
| --- | --- | --- | --- |
| LiPo Battery (3.7V) | Red (+) Wire | JST 1.25mm Connector (Bottom)

 | Main power supply via onboard connector

 |
| LiPo Battery (3.7V) | Black (-) Wire | JST 1.25mm Connector (Bottom)

 | Ground reference via onboard connector

 |
| Left Joystick (KY-023) | +5V / VCC | 5V Pin (Bottom Row)

 | Powered by 5V rail

 |
| Left Joystick (KY-023) | GND | GND Port (Shared splice)

 | Shared ground reference

 |
| Left Joystick (KY-023) | VRX (X-axis) | GPIO 3 (Top Row)

 | Analog X-axis signal

 |
| Left Joystick (KY-023) | VRY (Y-axis) | GPIO 4 (Top Row)

 | Analog Y-axis signal

 |
| Left Joystick (KY-023) | SW (Switch) | GPIO 5 (Top Row)

 | Joystick click button input

 |
| Right Joystick (KY-023) | +5V / VCC | 5V Pin (Bottom Row)

 | Powered by 5V rail

 |
| Right Joystick (KY-023) | GND | GND Port (Shared splice)

 | Shared ground reference

 |
| Right Joystick (KY-023) | VRX (X-axis) | GPIO 6 (Top Row)

 | Analog X-axis signal

 |
| Right Joystick (KY-023) | VRY (Y-axis) | GPIO 7 (Top Row)

 | Analog Y-axis signal

 |
| Right Joystick (KY-023) | SW (Switch) | GPIO 1 (Top Row)

 | Joystick click button input

 |
| Left Push Button | Pin 1 | GPIO 2 (Top Row)

 | Digital input for custom action button

 |
| Left Push Button | Pin 2 | GND (Shared ground splice)

 | Pulls pin LOW when pressed

 |
| Right Push Button | Pin 1 | GPIO 38 (Top Row)

 | Digital input for custom action button

 |
| Right Push Button | Pin 2 | GND (Shared ground splice)

 | Pulls pin LOW when pressed

 |
| NRF24L01+ Module | VCC | 3V3 Pin (Top Row, with 10µF capacitor across VCC/GND)

 | 3.3V Power input

 |
| NRF24L01+ Module | GND | GND Port (Shared splice)

 | Ground reference

 |
| NRF24L01+ Module | CE | GPIO 47 (Bottom Row)

 | Chip Enable control pin

 |
| NRF24L01+ Module | CSN | GPIO 48 (Bottom Row)

 | Chip Select Not (SPI CS)

 |
| NRF24L01+ Module | SCK | GPIO 9 (SPI Clock) | SPI Serial Clock

 |
| NRF24L01+ Module | MOSI | GPIO 10 (SPI MOSI) | SPI Master Out Slave In

 |
| NRF24L01+ Module | MISO | GPIO 11 (SPI MISO) | SPI Master In Slave Out

 |
| Left Push Button | Pin 2 | GND (Shared ground splice) | Pulls pin LOW when pressed |
| Right Push Button | Pin 1 | GPIO 38 (Top Row) | Digital input for custom action button |
| Right Push Button | Pin 2 | GND (Shared ground splice) | Pulls pin LOW when pressed |

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

DRONE WRINING DIAGRAMS
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
DRONE
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="660" height="627" alt="image" src="https://github.com/user-attachments/assets/f042e141-72d1-46f3-8e5f-3206d105e355" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Drone-Side Wiring Chart (Final)

| Component | Component Wire / Pin | Flight Controller / ESC Pad | Function / Notes |
|---|---|---|---|
| XING-E Pro 2207 Motors (x4) | 3 Motor Power Wires (per motor) | ESC Motor Pads (corners of 4-in-1 ESC) | Solder any order — wire order doesn't matter, fix spin direction in INAV Motors tab if needed |
| SpeedyBee 4-in-1 ESC | ESC Ribbon Cable | SpeedyBee FC Ribbon Cable Port | Plugs directly into the flight controller to bridge power and data |
| Flywoo Molicell 6S Battery | XT60 Main Power Lead | ESC XT60 Power Pads | Main power supply for the entire stack |
| BN-880 GPS & Compass | **T** (TX) | **R3** (Flight Controller) | GPS data transmit to FC receive — UART3 |
| BN-880 GPS & Compass | **R** (RX) | **T3** (Flight Controller) | GPS data receive to FC transmit |
| BN-880 GPS & Compass | **D** (SDA) | SDA (Flight Controller) | Compass I2C data line |
| BN-880 GPS & Compass | **C** (SCL) | SCL (Flight Controller) | Compass I2C clock line |
| BN-880 GPS & Compass | **V** (VCC) | 4.5V or 5V (Flight Controller) | Power input for GPS |
| BN-880 GPS & Compass | **G** (GND) | GND (Flight Controller) | Ground reference |
| DIYmalls LoRa ESP32 Board | TX | **R2** (Flight Controller) | MSP data transmit to FC receive |
| DIYmalls LoRa ESP32 Board | RX | **T2** (Flight Controller) | Optional — telemetry back from FC (not required for MSP_SET_RAW_RC) |
| DIYmalls LoRa ESP32 Board | 5V (or VIN) | 5V (Flight Controller) | Power input — confirmed via multimeter, 3.3V rail reads correctly |
| DIYmalls LoRa ESP32 Board | GND | GND (Flight Controller) | Ground reference — must be common with FC |
| NRF24L01+PA+LNA | VCC | 3V3 (DIYmalls ESP32 board) | See capacitor note below |
| NRF24L01+PA+LNA | GND | GND (DIYmalls ESP32 board, shared) | |
| NRF24L01+PA+LNA | CE | GPIO 47 (DIYmalls ESP32 board) | |
| NRF24L01+PA+LNA | CSN | GPIO 48 (DIYmalls ESP32 board) | SPI chip select |
| NRF24L01+PA+LNA | SCK | GPIO 33 (DIYmalls ESP32 board) | SPI clock |
| NRF24L01+PA+LNA | MOSI | GPIO 35 (DIYmalls ESP32 board) | SPI data in |
| NRF24L01+PA+LNA | MISO | GPIO 34 (DIYmalls ESP32 board) | SPI data out |
| NRF24L01+PA+LNA | IRQ | Not connected | Unused, code polls instead |
| Decoupling Capacitor (10µF) | + | NRF24 VCC pin | Solder directly at the NRF24 module, as close as possible |
| Decoupling Capacitor (10µF) | − | NRF24 GND pin | Solder directly at the NRF24 module, as close as possible |

------------------------------------------------------------------------------------------------------------------------------------------------------------------
CONTROLLER
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="756" height="545" alt="image" src="https://github.com/user-attachments/assets/3891e9ce-8518-4966-8ca0-d34253f10c69" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

Here is the updated controller wiring chart with both KY-023 joysticks powered by the 5V pin and the NRF24L01 module powered by the 3.3V pin:

# Heltec ESP32 LoRa V3 Remote Controller Wiring Reference

# Remote Controller — Final Wiring Chart

| Component | Component Pin | Board Pin / GPIO | Notes |
|---|---|---|---|
| USB Type-C | — | Type-C port | Power source |
| Left Joystick (KY-023) | VCC | 5V (Bottom Row) | USB-powered only |
| Left Joystick (KY-023) | GND | GND (shared) | |
| Left Joystick (KY-023) | VRX | GPIO 3 | Analog X |
| Left Joystick (KY-023) | VRY | GPIO 4 | Analog Y |
| Left Joystick (KY-023) | SW | GPIO 5 | Click button |
| Right Joystick (KY-023) | VCC | 5V (Bottom Row, shared) | USB-powered only |
| Right Joystick (KY-023) | GND | GND (shared) | |
| Right Joystick (KY-023) | VRX | GPIO 6 | Analog X |
| Right Joystick (KY-023) | VRY | GPIO 7 | Analog Y |
| Right Joystick (KY-023) | SW | GPIO 1 | Click button |
| Left Push Button | Pin 1 | GPIO 2 | Arm/disarm |
| Left Push Button | Pin 2 | GND (shared) | |
| Right Push Button | Pin 1 | GPIO 38 | RTH trigger |
| Right Push Button | Pin 2 | GND (shared) | |
| NRF24L01+PA+LNA | VCC | 3V3 | See capacitor note below |
| NRF24L01+PA+LNA | GND | GND (shared) | |
| NRF24L01+PA+LNA | CE | GPIO 47 | |
| NRF24L01+PA+LNA | CSN | GPIO 48 | SPI chip select |
| NRF24L01+PA+LNA | SCK | GPIO 33 | SPI clock |
| NRF24L01+PA+LNA | MOSI | GPIO 35 | SPI data in |
| NRF24L01+PA+LNA | MISO | GPIO 34 | SPI data out |
| NRF24L01+PA+LNA | IRQ | Not connected | Unused, code polls instead |
| Decoupling Capacitor (10µF electrolytic) | + (long leg) | NRF24 VCC pin | Solder as close to NRF24 module as possible |
| Decoupling Capacitor (10µF electrolytic) | − (short leg / stripe side) | NRF24 GND pin | Solder as close to NRF24 module as possible |

**Capacitor note**: solder it directly across the NRF24's own VCC/GND pins, right at the module — not back near the ESP32. If electrolytic, long leg/unmarked side = +VCC, striped side = −GND.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

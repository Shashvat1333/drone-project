# Drone Project

A fully custom quadcopter drone and handheld transmitter, built from scratch with a self-designed LoRa radio link instead of an off-the-shelf RC system.

![Drone Render](https://github.com/user-attachments/assets/7fb53470-5427-4511-a9d5-9a98a5afb5a7)

## Table of Contents
- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [CAD Model & Assembly](#cad-model--assembly)
- [Schematic & Wiring](#schematic--wiring)
- [Firmware](#firmware)
- [Getting Started](#getting-started)
- [Bill of Materials (BOM)](#bill-of-materials-bom)
- [License](#license)

## Overview

I am designing and building a fully custom quadcopter drone and handheld transmitter as a hardware engineering project. The goal is to combine mechanical design, electronics, 3D printing, and embedded systems to create a long-endurance flying platform controlled by a radio system I built myself, rather than an off-the-shelf drone or transmitter.

This project involves selecting and validating components for both the drone and controller, designing custom frames and enclosures in CAD, building a LoRa-based radio link for control and telemetry, wiring the full electrical systems, and preparing everything for manufacturing and assembly.

### Project Goals

- Build a quadcopter capable of 30+ minutes of flight time, prioritizing endurance over racing performance.
- Design and manufacture a custom 3D-printed frame and handheld controller enclosure.
- Build a fully custom transmitter/receiver system using LoRa instead of a commercial radio.
- Implement GPS-based Return-to-Home functionality.
- Learn about flight control systems, RF communication, power systems, and mechanical design under real-world constraints (weight, cost, vibration, torque).
- Create a documented engineering process from initial planning through final assembly.

### Key Technologies

**Mechanical Design**
- CAD modeling (frame, arms, landing legs, controller enclosure)
- 3D printing — PETG filament (Bambu A1 Mini)

**Electronics**
- SpeedyBee F405 V4 flight controller / 4-in-1 ESC stack
- iFlight XING-E Pro 2207 1800KV motors
- BN-880 GPS/compass module
- DIYmalls ESP32 LoRa V3 (SX1262) — drone-side radio
- Heltec WiFi LoRa 32 (SX1262) — controller-side radio/microcontroller
- 6S1P Li-ion battery pack (Flywoo Explorer Molicel P30B 18650)

**Programming / Firmware**
- Embedded C++ (Arduino framework, ESP32/LoRa)
- Flight controller firmware configuration (iNav-compatible)

---

## Repository Structure
```
drone-project/
├── CAD/ # .step files for drone frame, arms, controller enclosure
├── Firmware/ # Custom ESP32 LoRa transmitter/receiver firmware
├── Wiring Diagrams.md # Full wiring reference (drone + controller)
├── Images & Demo/ # Renders, build photos, flight test video
├── BOM.md # Full bill of materials
├── Journal.md # Build log / engineering journal
├── LICENSE.md
└── README.md
```

---

## CAD Model & Assembly

The drone frame, arms, landing legs, and handheld controller enclosure were all custom-designed in CAD, with dimensions driven by the physical footprint of the SpeedyBee stack, motors, and battery pack. Parts were printed in PETG for a balance of strength and heat resistance around the motor mounts.

All production-ready parts and full assemblies are stored in the [CAD](https://github.com/Shashvat1333/drone-project/tree/main/CAD) folder as `.step` files.

**Build demo:**

https://github.com/user-attachments/assets/ad44ab19-e9d0-4f68-9096-000306742742

---

## Schematic & Wiring

The drone side connects the flight controller to the ESC stack, motors, GPS/compass module, and the LoRa telemetry radio. The controller side connects a second LoRa radio to dual joysticks and push buttons for manual flight input.

Full pin-by-pin wiring specifications for both the drone and the handheld controller are documented in [Wiring Diagrams.md](Wiring%20Diagrams.md).

### Drone Wiring

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

### Controller Wiring

| Component | Component Pin / Wire | LoRa Board Pin / Header | Function / Notes |
|---|---|---|---|
| LiPo Battery (3.7V) | Red (+) Wire | JST 1.25mm Connector (Bottom) | Main power supply via onboard connector |
| LiPo Battery (3.7V) | Black (–) Wire | JST 1.25mm Connector (Bottom) | Ground reference via onboard connector |
| Left Joystick (KY-023) | +5V / VCC | 3V3 (Shared power rail/splice) | Shared power input |
| Left Joystick (KY-023) | GND | GND Port (Shared splice) | Shared ground reference |
| Left Joystick (KY-023) | VRX (X-axis) | GPIO 3 (Top Row) | Analog X-axis signal |
| Left Joystick (KY-023) | VRY (Y-axis) | GPIO 4 (Top Row) | Analog Y-axis signal |
| Left Joystick (KY-023) | SW (Switch) | GPIO 5 (Top Row) | Joystick click button input |
| Right Joystick (KY-023) | +5V / VCC | 3V3 (Shared power rail/splice) | Shared power input |
| Right Joystick (KY-023) | GND | GND Port (Shared splice) | Shared ground reference |
| Right Joystick (KY-023) | VRX (X-axis) | GPIO 6 (Top Row) | Analog X-axis signal |
| Right Joystick (KY-023) | VRY (Y-axis) | GPIO 7 (Top Row) | Analog Y-axis signal |
| Right Joystick (KY-023) | SW (Switch) | GPIO 1 (Top Row) | Joystick click button input |
| Left Push Button | Pin 1 | GPIO 2 (Top Row) | Digital input for custom action button |
| Left Push Button | Pin 2 | GND (Shared ground splice) | Pulls pin LOW when pressed |
| Right Push Button | Pin 1 | GPIO 38 (Top Row) | Digital input for custom action button |
| Right Push Button | Pin 2 | GND (Shared ground splice) | Pulls pin LOW when pressed |

---

## Firmware

The flight controller runs iNav-compatible firmware, configured (not custom-coded) for stabilization, GPS Return-to-Home, and ESC/motor output.

The LoRa radio link between the drone and the handheld controller is fully custom, written in embedded C++ using the Arduino framework. It reads joystick and button input on the controller side, transmits it over LoRa, and the drone-side ESP32 relays it into the flight controller as RC/telemetry data.

- **Source code:** [Firmware](https://github.com/Shashvat1333/drone-project/tree/main/FIRMWARE)
- **Boards used:** DIYmalls ESP32 LoRa V3 (SX1262) — drone side; Heltec WiFi LoRa 32 (SX1262) — controller side
- **Flight controller:** SpeedyBee F405 V4, configured via iNav

---

## Getting Started

To build and run this project yourself:

1. **Print the parts** — Slice the `.step` files from the [CAD](https://github.com/Shashvat1333/drone-project/tree/main/CAD) folder (built and tested in PETG).
2. **Assemble the frame** — Mount the motors, ESC stack, flight controller, GPS module, and battery according to the CAD model.
3. **Wire the electronics** — Follow [Wiring Diagrams.md](Wiring%20Diagrams.md) for both the drone and controller wiring.
4. **Flash the firmware** — Upload the custom LoRa firmware to both the drone-side and controller-side ESP32 boards from the [Firmware](https://github.com/Shashvat1333/drone-project/tree/main/FIRMWARE) folder using the Arduino IDE.
5. **Configure the flight controller** — Load iNav-compatible firmware onto the SpeedyBee F405 V4 and configure PID tuning, GPS, and Return-to-Home settings.
6. **Test and fly** — Power on the drone and controller, confirm the LoRa link is transmitting, and test flight in a safe, open area.

---

## Bill of Materials (BOM)

Full itemized parts list and pricing available in [BOM.md](https://github.com/Shashvat1333/drone-project/blob/main/BOM.md).

---

## License

This project is licensed under the terms specified in [LICENSE.md](https://github.com/Shashvat1333/drone-project/blob/main/LICENSE.md).

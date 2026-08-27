# Drone-project

## Overview

I am designing and building a **fully custom quadcopter drone and handheld transmitter** as a hardware engineering project. The goal of this project is to combine **mechanical design, electronics, 3D printing, and embedded systems** to create a long-endurance flying platform controlled by a radio system I built myself, rather than an off-the-shelf drone or transmitter.

This project involves selecting and validating components for both the drone and controller, designing custom frames and enclosures in CAD, building a LoRa-based radio link for control and telemetry, wiring the full electrical systems, and preparing everything for manufacturing and assembly.

## Project Goals

The main goals of this project are:
- Build a quadcopter capable of 30+ minutes of flight time, prioritizing endurance over racing performance.
- Design and manufacture a custom 3D-printed frame and handheld controller enclosure.
- Build a fully custom transmitter/receiver system using LoRa instead of a commercial radio.
- Implement GPS-based Return-to-Home functionality.
- Learn about flight control systems, RF communication, power systems, and mechanical design under real-world constraints (weight, cost, vibration, torque).
- Create a documented engineering process from initial planning through final assembly.

## Technologies and Tools


### Mechanical Design
- CAD modeling (frame, arms, landing legs, controller enclosure)
- 3D printing
- PETG filament (Bambu A1 Mini)

### Electronics
- SpeedyBee F405 V4 flight controller / 4-in-1 ESC stack
- iFlight XING-E Pro 2207 1800KV motors
- BN-880 GPS/compass module
- DIYmalls ESP32 LoRa V3 (SX1262) — drone-side radio
- Heltec WiFi LoRa 32 (SX1262) — controller-side radio/microcontroller
- 6S1P Li-ion battery pack (Flywoo Explorer Molicel P30B 18650)

### Programming / Firmware
- Embedded C++ (Arduino framework, ESP32/LoRa)
- Flight controller firmware configuration (iNav-compatible)

### Documentation
- GitHub
- JOURNAL.md — full day-by-day build log with decisions and lessons learned


<img width="1784" height="773" alt="image" src="https://github.com/user-attachments/assets/7fb53470-5427-4511-a9d5-9a98a5afb5a7" />

https://private-user-images.githubusercontent.com/176981627/632711271-ad44ab19-e9d0-4f68-9096-000306742742.mp4?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3ODc4NTc3OTEsIm5iZiI6MTc4Nzg1NzQ5MSwicGF0aCI6Ii8xNzY5ODE2MjcvNjMyNzExMjcxLWFkNDRhYjE5LWU5ZDAtNGY2OC05MDk2LTAwMDMwNjc0Mjc0Mi5tcDQ_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwODI3JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDgyN1QxOTA0NTFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1hMTlhN2M3ZDIwMDQwZmViNTFkYTY3MWZiMzkzMGYwN2YwMjhiMmQ3ZmZkMDMzNGZjMDkyODBmYTIwMWNkYzM3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9dmlkZW8lMkZtcDQifQ.23sNOeX46yJHNKeD97PojE8nK35K4VUXyUVNzrACNrQ

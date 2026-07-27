Drone Project Journal
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 1**: July 27, 2026


Time spent: **4 hours**


**What I worked on**

Today I began planning my custom quadcopter drone project. Before choosing any parts, I focused on understanding how the entire system works, including both the drone and a custom-built transmitter.

I read through a beginner drone building guide to understand the main components of a quadcopter, including the frame, motors, propellers, ESCs, flight controller, receiver, GPS module, battery, and power distribution board (PDB). Instead of following the guide exactly, I used it as a reference while deciding what would best fit my own project requirements.

I established the main goals for the project: using a carbon fiber frame, keeping the total weight under 650g, not including an onboard camera, supporting GPS-based Return-to-Home functionality, and designing a fully custom handheld transmitter instead of purchasing a commercial one.

I also mapped out how the major components communicate with each other. I learned that the flight controller acts as the brain of the drone, receiving pilot commands from the receiver and position data from the GPS module before sending motor speed commands to the ESCs, which drive the four brushless motors.


**What I learned**

Today I learned that most drone GPS modules already include a built-in compass (magnetometer). While the GPS provides the drone's position, the compass provides its heading, allowing navigation features such as Return-to-Home to work correctly.

I also learned the purpose of a power distribution board (PDB). The PDB distributes power from the battery to all four ESCs, and many models also include a built-in 5V voltage regulator for powering the flight controller, receiver, and GPS module. Using a PDB with an integrated regulator simplifies the electrical system and reduces the number of required components.

I learned that additional resistors and capacitors generally do not need to be selected separately because they are already integrated into modern flight controllers, ESCs, and PDBs. However, adding a capacitor across the battery input can help reduce electrical noise caused by rapid motor speed changes.

I also researched electrical protection and learned that drones typically do not use traditional fuses because motor current changes too quickly during normal flight. Instead, builders use a smoke stopper during the first power-on to safely detect wiring mistakes before applying full battery power.

For the custom transmitter, I initially considered using an ESP32 with either ESP-NOW or Wi-Fi communication. After researching the available range and reliability, I learned that these methods provide much shorter range and less reliable failsafe protection than dedicated RC communication systems.

I then learned about the standard combination used by many DIY radio builders: EdgeTX firmware together with an ExpressLRS (ELRS) radio module. I also learned that EdgeTX automatically reads joystick (gimbal) inputs, meaning the main work is wiring the hardware correctly and configuring it through the firmware rather than writing custom software.


**Decisions made**

Decided to build the drone using a carbon fiber frame with a target weight below 650g.

Decided not to include an onboard camera.

Decided to use a GPS and compass module for Return-to-Home functionality.

Decided to use a PDB with a built-in 5V voltage regulator.

Decided to use a smoke stopper instead of a traditional fuse during initial power-up.

Decided against using an ESP32-to-ESP32 radio link because of its limited range and failsafe capabilities.

Decided to build the transmitter using EdgeTX firmware with an ExpressLRS radio module.

Decided to use an iNav-compatible flight controller to support GPS navigation and Return-to-Home.


**Next steps**

Research and select the frame, motors, ESCs, flight controller, receiver, GPS module, battery, and PDB.

Research the transmitter hardware, including an EdgeTX-compatible mainboard, gimbals, switches, display, and ELRS module.

Create a complete bill of materials with estimated pricing.

Begin designing the custom transmitter enclosure.

Plan the wiring layout for both the drone and the transmitter.


<img width="982" height="607" alt="image" src="https://github.com/user-attachments/assets/cc2f2c09-b0ef-45d8-a1c0-13ab3c76b10c" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------


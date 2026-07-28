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

**Day 2**: July 28, 2026


Time spent: **4 hours**


**What I worked on**

Today I finalized the overall architecture and hardware selection for both my custom quadcopter drone and the custom handheld controller. After researching different options, I selected the major components that best matched my project goals and created a complete system plan before beginning the CAD stage.

For the drone, I finalized the carbon fiber frame design approach, selected the SpeedyBee F405 V4 flight stack, iFlight XING-E Pro 2207 1800KV motors, Gemfan Hurricane 51433 propellers, the Tattu R-Line 6S battery, and the BN-880 GPS module with its built-in compass. I also confirmed that the drone will not include an FPV camera, allowing me to reduce weight and simplify the overall design.

For the custom controller, I selected the ESP32-C3 Super Mini as the main microcontroller, the HC-12 wireless module for long-range communication, KY-023 joystick modules for control input, a rechargeable LiPo battery, and a TP4056 USB-C charging module. 


**What I learned**

Today I learned how the controller's charging circuit should be wired using the TP4056 module. The battery connects directly to the charging module, while the module powers the ESP32 through its output pins, allowing the controller to be recharged safely using USB-C.

I also learned that adding electrolytic capacitors to the power system helps reduce voltage spikes and electrical noise, improving overall system reliability. In addition to the main low-ESR capacitor used on the drone, I decided to include a capacitor kit for future testing and filtering if needed.

I gained a better understanding of how the complete drone and controller systems fit together, including the electrical connections, communication between components, and overall project layout.


**Decisions made**

Finalized the main hardware for both the drone and custom controller.

Confirmed the drone will use a custom carbon fiber frame manufactured through PCBWay.

Decided to use the ESP32-C3 Super Mini and HC-12 module for the custom controller.

Finalized the power and charging layout for the handheld controller.

Estimated the total project cost to be approximately **$400–500 CAD**, including electronics, batteries, shipping, and custom frame manufacturing.


**Next steps**

Begin designing the carbon fiber drone frame in CAD.

Create the custom handheld controller enclosure.

Build the complete wiring diagrams for both the drone and controller.


<img width="838" height="601" alt="image" src="https://github.com/user-attachments/assets/02613f79-4e75-4b9f-90ce-186a90ccc83f" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

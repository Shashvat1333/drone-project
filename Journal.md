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

**Day 3**: July 29, 2026


Time spent: **3 hours**


**What I worked on**

Today I continued planning my custom drone project by refining both the handheld controller and the drone frame design.

For the controller, I decided to switch from using a separate ESP32 and radio module to the **Heltec WiFi LoRa 32 (SX1262)** development board. This combines the microcontroller and LoRa radio into a single board, making the controller more compact and reducing the amount of wiring required. I also finalized the controller's power system by selecting a 3.7V 320mAh LiPo battery with a 1.25mm JST connector, which plugs directly into the Heltec board and can be recharged through its built-in USB-C charging circuit.

I also began designing the drone frame. While planning the frame, I considered switching from a custom carbon fiber frame to a PLA+ printed frame because it would be less expensive, faster to manufacture, and still meet my project's weight requirements.

Finally, I reviewed the motor mounting system. I confirmed that the iFlight XING2 motors use M3 mounting screws and determined that, with 4mm-thick frame arms, 8mm M3 screws and 3.2mm mounting holes will provide the correct fit. I also planned the arm dimensions, deciding that the arms should be approximately 10–15mm wide to provide sufficient strength while keeping the frame lightweight. To mount the flight controller safely, I selected an M3 nylon standoff kit to isolate the electronics from the conductive frame.


**What I learned**

Today I learned that the Heltec WiFi LoRa 32 board simplifies the controller design by combining the ESP32 and LoRa radio onto a single board while also providing built-in USB-C battery charging.

I also learned that the board's antenna can be carefully bent to fit inside the controller enclosure as long as it is bent with a smooth curve rather than a sharp crease.

While working on the frame, I learned more about selecting the correct mounting hardware by matching the motor screw length to the frame thickness and ensuring the frame arms are wide enough to provide adequate strength without adding unnecessary weight.


**Decisions made**

Switched to the Heltec WiFi LoRa 32 (SX1262) for both the transmitter and receiver.

Selected a 3.7V 320mAh LiPo battery to power the controller.

Considered switching from a carbon fiber frame to a PLA+ printed frame.

Confirmed the motor mounting hardware will use M3 × 8mm screws with 3.2mm mounting holes.

Selected M3 nylon standoffs to mount the flight controller and ESC safely.


**Next steps**

Continue designing the drone frame in CAD.

Finalize whether the frame will be manufactured from carbon fiber or PLA+.

Design the custom handheld controller enclosure around the Heltec board.

Review the complete hardware list.


<img width="1123" height="757" alt="image" src="https://github.com/user-attachments/assets/f3af8485-7e17-4bdf-942a-35cbce62da08" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 4**: July 30, 2026


Time spent: **4 hours**


**What I worked on**

Today I finalized the frame material and dimensions for my drone, and fully mapped out how my custom LoRa-based transmitter/receiver system will handle both flight control and telemetry. I also worked out the mechanical details for mounting the modular arms and small components like the GPS and LoRa board, and finalized my parts list with pricing.

I compared PLA+ against carbon fiber and PETG for the frame material, and after weighing flex, crash durability, and cost, settled on PETG as the frame material. I then worked through arm and base plate dimensions in CAD to make sure the frame would hold up to 6S motor torque without excessive flex.

I also planned out how my DIYmalls ESP32 LoRa V3 (SX1262) boards will function as both the transmitter and receiver, handling stick control commands going to the drone and telemetry (like battery voltage) coming back from it over the same radio link.


**What I learned**

I learned that 3D-printed plastic frames, even in tougher filaments, flex more than CNC-cut carbon fiber under high motor torque, which can cause gyro vibration issues and reduce crash durability. I looked into carbon fiber CNC/waterjet cutting services (SendCutSend, CNC Madness, uMake) as an alternative but decided the cost and complexity weren't worth it compared to a properly reinforced PETG frame.

I learned that the SX1262 chip is a half-duplex transceiver, meaning a single LoRa module on each end (drone and controller) can send control commands and receive telemetry using the same radio, rather than needing separate transmit/receive hardware.

I learned that since I'm using the SpeedyBee F405 V4 stack, the flight controller already has a built-in voltage sensor — so I don't need to build my own voltage divider circuit. Instead, I just need to route that data out over a UART serial connection to my ESP32 LoRa board, using two wires (one for outgoing control data, one for incoming telemetry).

I learned that a low-ESR capacitor (35V/1000uF) is still needed on the main battery power pads to protect against voltage spikes from the motors/ESC, separate from the LoRa board's power supply.

I learned that heavy-duty foam tape works as a practical, simpler alternative to a custom 3D-printed mount for small components like the GPS module and LoRa board, since foam is viscoelastic and absorbs high-frequency motor vibration effectively, unlike thin electrical tape.

I learned that for attaching modular, separately-printed arms to the frame, M3 brass heat-set inserts paired with steel bolts are more reliable than standard nuts/bolts or nylon bolts, since they create a strong reusable threaded connection without loose hardware falling into the frame.


**Decisions made**

Decided on foam tape as the mounting method for the GPS module and LoRa board rather than a custom printed bracket.

Decided on M3 x 5mm x 4mm brass heat-set inserts with steel M3 bolts for attaching modular arms.


**Next steps**

Finalize CAD design for the modular arms with brass insert mounting points built in.

Design the enclosure/top plate with correct wall thickness and small vent holes for heat dissipation.


<img width="440" height="312" alt="image" src="https://github.com/user-attachments/assets/802e6889-57c3-4058-825b-e380f908e8df" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

**Day 5**: July 31, 2026


Time spent: **3 hours**


**What I worked on**

Today I made several major changes to my custom drone build by stepping back and reviewing the overall design. My main goal was to improve efficiency, increase flight time, and reduce the total project cost without sacrificing reliability. After comparing different components, I realized that some of my original hardware choices were designed more for high-performance racing than for the long-endurance drone I want to build.

I updated several of the main components in my parts list. I switched from the **iFlight XING2 2207 1855KV** motors to the **iFlight XING-E Pro 2207 1800KV** motors because they are more efficient and provide smoother throttle response for cruising. I decided to keep the **SpeedyBee F405 V4 30×30 flight controller and ESC stack** since it already meets all of my project requirements and is compatible with the rest of my electronics.

The biggest change I made was to the battery system. My original plan was to use a **Tattu R-Line 1550mAh 4S LiPo**, but after estimating the expected flight time, I realized it would only provide around 4–6 minutes of flight. Since my goal is to achieve at least 30 minutes of flight time, I switched to the **Flywoo Explorer Lionpack BAK P45D 21700 4S1P 4500mAh Li-ion battery**. This battery uses high-capacity 21700 Li-ion cells, which store much more energy than a traditional LiPo pack while still operating at the same 14.8V (4S) voltage and using the same XT60 connector. Because of this, I can use it with my existing electronics without needing any adapters or wiring changes. I also selected the **SkyRC B6Neo balance charger** so I can safely charge both Li-ion and LiPo batteries.

I also continued designing the drone frame in CAD and reached approximately **50% completion**. During the design process, I finalized the dimensions of the drone arms, deciding on **7mm thickness and 10mm width** with internal infill to improve strength while minimizing unnecessary weight.

Finally, I confirmed that my **Bambu A1 Mini** 3D printer and **Elegoo PETG** filament will work well together for manufacturing the frame. After reviewing the printer and material specifications, I determined that no hardware upgrades or modifications are needed before I begin printing.


**What I learned**

Today I learned that selecting components based on the overall mission of the drone is more important than simply choosing the highest-performance parts. Motors and batteries designed for racing are not always the best choice for long-endurance flight.

I also learned that Li-ion batteries provide a much higher energy density than traditional LiPo batteries, making them a much better option for increasing flight time. Since the new battery uses the same voltage and connector as my original design, I can upgrade the battery without changing the rest of the electrical system.

While continuing the CAD design, I learned more about balancing frame strength and weight. Increasing the arm thickness while using internal infill allows the frame to remain strong without making it unnecessarily heavy.

I also confirmed that my printer and filament are already capable of producing the frame, allowing me to move into manufacturing without purchasing additional equipment.


**Decisions made**

Switched to the **iFlight XING-E Pro 2207 1800KV** motors for improved efficiency.

Kept the **SpeedyBee F405 V4 30×30 flight controller and ESC stack**.

Replaced the **Tattu R-Line 1550mAh 4S LiPo** with the **Flywoo Explorer Lionpack BAK P45D 21700 4S1P 4500mAh Li-ion battery**.

Selected the **SkyRC B6Neo balance charger**.

Finalized the drone arm dimensions as **7mm thick × 10mm wide** with internal infill.

Confirmed that the **Bambu A1 Mini** printer and **Elegoo PETG** filament will be used to manufacture the frame.


**Next steps**

Continue designing the remaining sections of the drone frame in CAD.

Continue refining the design based on the prototype before moving to final assembly.


<img width="593" height="402" alt="image" src="https://github.com/user-attachments/assets/ca55ea8e-d262-4111-99bd-9256f730bad2" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 6**: August 1, 2026


Time spent: **2 hours 46 minutes**


**What I worked on**

Today I focused entirely on the CAD design of my drone project and made significant progress. I completed the design of the drone frame, bringing that portion of the project to completion. I also continued working on the custom handheld controller and brought its design close to completion.

To better visualize how the final drone will be assembled, I created a complete CAD assembly of the frame and added proxy models of the M3 screws. Seeing all of the hardware assembled together allowed me to evaluate how the individual parts interact and how the finished drone will look once built.

I also designed the landing legs for the frame, completing the structural layout and providing the drone with the necessary ground clearance for takeoff and landing.


**What I learned**

Today I learned that building a complete CAD assembly is an effective way to identify design issues that are difficult to notice when working on individual parts separately. By viewing the entire assembly with the mounting hardware installed, I was able to find and correct several clearance, alignment, and mounting issues before manufacturing.

I also gained a better understanding of how small adjustments to individual components can improve the fit and overall assembly of the final drone.


**Decisions made**

Completed the CAD design of the drone frame.

Added proxy M3 screws to create a complete assembly for design verification.

Designed the landing legs for the frame.

Corrected several clearance and alignment issues discovered during assembly.

Continued refining the custom controller, bringing it close to completion.


**Next steps**

Finish the remaining controller CAD design.

Perform a final review of the complete drone assembly before manufacturing.


<img width="943" height="556" alt="image" src="https://github.com/user-attachments/assets/bb1dec53-7862-4401-9cbd-db6d3d007779" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 7**: August 2, 2026


Time spent: **3 hours**


**What I worked on**

Today I finished the CAD design for my custom handheld controller, completing the mechanical design of both the drone and its controller. After finishing the individual parts, I created a complete CAD assembly of the controller to verify that everything fit together correctly before manufacturing.

Building the full assembly allowed me to inspect the controller as a complete product rather than as separate components. During this process, I found a few missing parts that I had forgotten to include and noticed several small design issues that were not obvious while working on the individual models. After identifying these problems, I updated the design so the controller assembly was complete and ready for manufacturing.

I also began creating the electrical wiring diagrams using Cirkit Designer. I completed the full wiring diagram for the drone, mapping the connections between the flight controller, 4-in-1 ESC, motors, GPS module, LoRa receiver, battery, and other electronics. Creating the wiring diagram helped verify that all of the required electrical connections had been accounted for before beginning the physical assembly.


**What I learned**

Today I learned that creating a complete CAD assembly is one of the best ways to verify a design before manufacturing. Viewing every component together made it much easier to identify missing parts, incorrect fits, and small design mistakes that were difficult to notice while designing individual components.

I also learned that building the wiring diagram before assembling the electronics makes it much easier to understand the overall electrical system and identify any missing connections before soldering begins.


**Decisions made**

Completed the CAD design of the custom handheld controller.

Created a complete controller assembly for design verification.

Corrected several missing parts and minor design issues discovered during the assembly process.

Completed the drone's wiring diagram using Cirkit Designer.

Decided to perform one final review of the parts list before applying for funding and ordering the components.


**Next steps**

Complete the controller wiring diagram.

Review the complete bill of materials one final time.

Apply for project funding.

Order the components and begin the manufacturing phase once funding is approved.

<img width="667" height="441" alt="image" src="https://github.com/user-attachments/assets/9c9cfdc7-2ece-49cd-9658-10750085abae" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 8**: August 5, 2026

Time spent: **3 hours**

Built out proxy parts for the drone assembly today, including the ESC, motors, propellers, and flight controller. Having accurate models instead of placeholder shapes made it much easier to see what the final product would actually look like when put together. Found several screw hole sizing issues throughout the frame, some too large and some too small for the actual hardware, and went through and fixed each one. Also ran into a specific problem with the FC and ESC stack: the screws I'd planned to use were too large to properly attach the 4-in-1 ESC and flight controller, so I'm switching to a smaller size from my M3 kit once funding comes through. Made a few structural changes too, adding material in some spots for stability and trimming it elsewhere to save weight.
Next: order the smaller screws once funded, keep refining the frame, move toward finalizing before manufacturing.

<img width="1784" height="773" alt="image" src="https://github.com/user-attachments/assets/36b0be59-9906-4ecb-97e2-a7e3b60bee9c" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 9**: August 6, 2026

Time spent: **3 hours**

Made a big change to the battery setup today. Was originally planning to use the Flywoo Explorer Lionpack BAK P45D 4S1P 4500mAh pack, but switched to the Flywoo Explorer Molicel P30B 18650 6S1P 3000mAh instead to get better flight times and efficiency. Going from 4S to 6S bumps up the system voltage, which lets the motors spin more efficiently under load while pulling fewer amps for the same output, so better performance and endurance overall. Finished the full Bill of Materials today too, landing on just over $700 CAD for the complete build. Had to redo my wiring diagram in Cirkit after realizing I never saved the last version, but got through it and finished both the drone and controller diagrams. Also finished the demo video for the drone, spent some extra time making it look realistic by having two propellers spin clockwise and the other two counterclockwise to match how a real quadcopter actually flies. Did a full review of everything so far and didn't find any issues, so the design's in a solid finished state.
Next: apply for funding, then move into printing custom parts and ordering the rest of the components.

https://github.com/user-attachments/assets/ad44ab19-e9d0-4f68-9096-000306742742

-------------------------------------------------------------------------------------------------------------------------------------------------------------------



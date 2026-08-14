Drone Project Journal
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 1**: July 27, 2026

Time spent: **4 hours**

Started planning my custom quadcopter today, both the drone itself and a custom transmitter to go with it. Read through a beginner drone guide to understand the main components like the frame, motors, ESCs, flight controller, GPS, and PDB, then used it as a reference rather than following it exactly. Set my main goals as a carbon fiber frame under 650g, no onboard camera, GPS based Return to Home, and a fully custom handheld transmitter instead of buying one. Learned GPS modules usually come with a built in compass for heading, and that a PDB with a built in 5V regulator simplifies the whole electrical system. Also learned drones typically skip traditional fuses since motor current changes too fast, using a smoke stopper instead during first power on. Looked at ESP32 with ESP-NOW or WiFi for the transmitter but the range and failsafe reliability weren't good enough, so decided on EdgeTX firmware with an ExpressLRS radio module instead.
Next: research and select the frame, motors, ESCs, flight controller, receiver, GPS, battery, and PDB, then start the bill of materials.

<img width="982" height="607" alt="image" src="https://github.com/user-attachments/assets/cc2f2c09-b0ef-45d8-a1c0-13ab3c76b10c" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 2**: July 28, 2026

Time spent: **4 hours**

Finalized the main hardware for both the drone and the custom controller. Picked the SpeedyBee F405 V4 flight stack, iFlight XING-E Pro 2207 1800KV motors, Gemfan Hurricane 51433 props, a Tattu R-Line 6S battery, and the BN-880 GPS with built in compass, no FPV camera to keep weight down. For the controller, went with an ESP32-C3 Super Mini, HC-12 wireless module, KY-023 joysticks, a rechargeable LiPo, and a TP4056 USB-C charging module. Learned how the TP4056 charging circuit should be wired, with the battery going into the module and the module powering the ESP32. Also learned adding electrolytic capacitors helps cut down voltage spikes and noise. Estimated total project cost around $400 to 500 CAD.
Next: start designing the carbon fiber frame in CAD, design the controller enclosure, build out the wiring diagrams.

<img width="838" height="601" alt="image" src="https://github.com/user-attachments/assets/02613f79-4e75-4b9f-90ce-186a90ccc83f" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 3**: July 29, 2026

Time spent: **3 hours**

Switched the controller design from a separate ESP32 and radio module to the Heltec WiFi LoRa 32 (SX1262) board, which combines both into one and cuts down on wiring. Picked a 3.7V 320mAh LiPo with a 1.25mm JST connector that plugs right into the Heltec board and charges through its built in USB-C. Started on the drone frame and considered switching from carbon fiber to PLA+ since it's cheaper and faster to make while still meeting the weight target. Confirmed the iFlight XING2 motors use M3 screws and worked out that 8mm M3 screws with 3.2mm holes fit a 4mm thick arm properly. Planned arm width at 10 to 15mm for strength without adding much weight, and picked M3 nylon standoffs to isolate the flight controller from the frame.
Next: keep designing the frame, decide between carbon fiber and PLA+, design the controller enclosure around the Heltec board.

<img width="1123" height="757" alt="image" src="https://github.com/user-attachments/assets/f3af8485-7e17-4bdf-942a-35cbce62da08" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 4**: July 30, 2026

Time spent: **4 hours**

Compared PLA+, carbon fiber, and PETG for the frame and landed on PETG after weighing flex, crash durability, and cost. Worked through arm and base plate dimensions in CAD to handle 6S motor torque without too much flex. Learned 3D printed frames flex more than CNC cut carbon fiber under high torque, which can cause gyro vibration issues, but decided the cost of CNC cutting wasn't worth it over a properly reinforced PETG frame. Mapped out how the DIYmalls ESP32 LoRa boards will handle both control commands and telemetry over the same radio link, learned the SX1262 chip is half duplex so one module can do both jobs. Also learned the SpeedyBee stack already has a built in voltage sensor, so I just need to route that over UART to the LoRa board. Decided to use foam tape to mount the GPS and LoRa board since it absorbs vibration well, and picked M3 brass heat set inserts with steel bolts for attaching the modular arms.
Next: finalize the CAD for the modular arms with the insert mounting points built in, design the enclosure with proper wall thickness and vent holes.

<img width="440" height="312" alt="image" src="https://github.com/user-attachments/assets/802e6889-57c3-4058-825b-e380f908e8df" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 5**: July 31, 2026

Time spent: **3 hours**

Stepped back and reviewed the whole build to improve efficiency and flight time without hurting reliability. Realized some of my original parts were picked more for racing than long endurance flight. Switched to the iFlight XING-E Pro 2207 1800KV motors for better efficiency and kept the SpeedyBee F405 V4 stack since it already covers what I need. Biggest change was the battery, my original Tattu R-Line 1550mAh 4S LiPo would've only given 4 to 6 minutes of flight time, so I switched to the Flywoo Explorer Lionpack BAK P45D 21700 4S1P 4500mAh Li-ion battery, which runs at the same voltage and uses the same XT60 connector so no wiring changes needed. Picked up a SkyRC B6Neo charger to handle both Li-ion and LiPo safely. Got the frame CAD to about 50% done and settled on 7mm thick, 10mm wide arms with internal infill. Also confirmed my Bambu A1 Mini and Elegoo PETG filament will work fine for printing the frame without any upgrades needed.
Next: keep working through the rest of the frame CAD, refine based on the prototype before final assembly.

<img width="593" height="402" alt="image" src="https://github.com/user-attachments/assets/ca55ea8e-d262-4111-99bd-9256f730bad2" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 6**: August 1, 2026

Time spent: **2 hours 46 minutes**

Finished the drone frame CAD and got the controller design close to done. Built a full CAD assembly of the frame with proxy M3 screws to see how everything fits together as a whole instead of piece by piece, which made it a lot easier to catch clearance and alignment issues before manufacturing. Also designed the landing legs to give the drone proper ground clearance.
Next: finish the remaining controller CAD, do a final review of the full drone assembly before manufacturing.

<img width="943" height="556" alt="image" src="https://github.com/user-attachments/assets/bb1dec53-7862-4401-9cbd-db6d3d007779" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 7**: August 2, 2026

Time spent: **3 hours**

Finished the CAD for the handheld controller, wrapping up the mechanical design for both the drone and controller. Built a full assembly of the controller and found a few missing parts and small design issues that weren't obvious when working on individual pieces, fixed those before calling it ready for manufacturing. Also started the wiring diagrams in Cirkit Designer and finished the full drone diagram, mapping out the flight controller, 4-in-1 ESC, motors, GPS, LoRa receiver, battery, and everything else.
Next: finish the controller wiring diagram, review the full parts list one more time, apply for funding, then order components once approved.

<img width="667" height="441" alt="image" src="https://github.com/user-attachments/assets/9c9cfdc7-2ece-49cd-9658-10750085abae" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 8**: August 5, 2026

Time spent: **3 hours**

Built out proxy parts for the drone assembly today including the ESC, motors, propellers, and flight controller. Having accurate models instead of placeholder shapes made it a lot easier to see what the final product will actually look like put together. Found several screw hole sizing issues throughout the frame, some too large and some too small for the actual hardware, and went through and fixed each one. Also ran into a specific problem with the FC and ESC stack where the screws I'd planned to use were too big to attach the 4-in-1 ESC and flight controller together properly, so I'm switching to a smaller size from my M3 kit once funding comes through. Made a few structural changes too, adding material in some spots for stability and trimming it elsewhere to save weight.
Next: order the smaller screws once funded, keep refining the frame, move toward finalizing before manufacturing.

<img width="1784" height="773" alt="image" src="https://github.com/user-attachments/assets/36b0be59-9906-4ecb-97e2-a7e3b60bee9c" />

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Day 9**: August 6, 2026

Time spent: **3 hours**

Made a big change to the battery setup today. Was originally planning to use the Flywoo Explorer Lionpack BAK P45D 4S1P 4500mAh pack, but switched to the Flywoo Explorer Molicel P30B 18650 6S1P 3000mAh instead to get better flight times and efficiency. Going from 4S to 6S bumps up the system voltage, which lets the motors spin more efficiently under load while pulling fewer amps for the same output, so better performance and endurance overall. Finished the full Bill of Materials today too, landing on just over $700 CAD for the complete build. Had to redo my wiring diagram in Cirkit after realizing I never saved the last version, but got through it and finished both the drone and controller diagrams. Also finished the demo video for the drone, spent some extra time making it look realistic by having two propellers spin clockwise and the other two counterclockwise to match how a real quadcopter actually flies. Did a full review of everything so far and didn't find any issues, so the design's in a solid finished state.
Next: apply for funding, then move into printing custom parts and ordering the rest of the components.

https://github.com/user-attachments/assets/ad44ab19-e9d0-4f68-9096-000306742742

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Universal-USB-to-Serial-programmer-for-Arduino
Using this programmer any Serial communicating device can be programmed. I made this for my minimal Arduino nano board (Atmega328)

![mini_thumb](https://user-images.githubusercontent.com/97245507/224406360-c0154d70-9b06-443f-95af-1427576ab1c5.png)

In the previous tutorial I made my own minimal Arduino board which is fully compatible and cheap. But to program that board we need an external universal programmer which can communicate serially to program the microcontroller on minimal board. By keeping that in mind I designed this universal programmer which can program any USB to serial interfacing board. I want to keep it low cost and fully functional.

![mini_IMG_5228](https://user-images.githubusercontent.com/97245507/224406395-5dee3191-9d1c-49e1-84bc-118f7d24d7e6.png)

It is built on CH340C USB to serial programmer IC which comes in 16 pin SOP. There are many different versions of the chip available but this one has internal 12MHz oscillator. So, a direct communication can be achieved between microcontroller and programmer with minimal external components.

<img width="970" alt="ice_screenshot_20230310-212630" src="https://user-images.githubusercontent.com/97245507/224406448-e65989bf-cf97-44fa-8671-dbd7c7d79a84.png">

JLCPCB is a global PCB prototype and assembly service provider, offering affordable and high-quality PCB solutions to customers around the world. With over 10 years of experience, delivering a range of services including PCB design, fabrication, assembly, and more. Their advanced facilities and cutting-edge technology enable them to provide fast turnaround times, with a 24-hour online customer service team available to assist you every step of the way.

Components required:

<img width="625" alt="ice_screenshot_20230308-233006" src="https://user-images.githubusercontent.com/97245507/224406479-389dda38-e84e-42d7-bbf5-d192f9aae30e.png">

USB type C
Ch340C USB to Serial programmer
16Mhz crystal
28 pin DIP IC holder
100nf Capacitors
10k, 1k resistor
SMD LEDs
Custom PCB from JLCPCB

Circuit diagram:

I made the circuit diagram in EasyEDA keeping all the design consideration in mind. This universal programmer is a dual programmer. Either you can use DIP ic directly on the board and flash it easily. Or you can plug to any microcontroller board via the programming headers.

<img width="763" alt="ice_screenshot_20230308-232850" src="https://user-images.githubusercontent.com/97245507/224406509-3785ae63-464e-4103-858d-74f7aaa8f331.png">

RX and TX LEDs are in the circuit which blinks on a successful code flash. This is a type of indicator to the flash. USB type C is the best solution nowadays because it give better compatibility and rigidness to the design.

![mini_IMG_5229](https://user-images.githubusercontent.com/97245507/224406548-6a94e38a-73d0-4e21-ba8d-4a43d279e5f8.png)

The serial programming method uses 5 wires including RX, TX, Reset, VCC and GND. Rx (Receiver) of programmer goes to the (TX)Transmitter of MCU with a 1k resistor between them. Tx of programmer goes to RX of MCU with 1k resistor. DTR of programmer goes to RESET of MCU with 100nf capacitor in between. VCC to the 5v and GND is common to all. For the power handing I am using 5v linear power regulator(AMS1117) IC.

Gerber files and PCB design:

![My Video1](https://user-images.githubusercontent.com/97245507/224406571-3e76b9e5-137f-44b4-818d-0ecee26770e7.gif)

Then I converted the PCB and exported the Gerber files, if you want to use the same designs then download all the required files from here. You can directly order the PCB by uploading these Gerber files to JLCPCB quote now section.

<img width="1608" alt="pogf" src="https://user-images.githubusercontent.com/97245507/224406605-b8509d3b-b4d0-4fd5-af07-b1ef15861e1d.png">

I want to keep it small with new design that’s why this hexagon shape is adopted. I choose black color with FR4 material and HASL finishing. If you don’t want to assemble the PCB by hand then JLCPCB also offers a SMT assembly service staring from just $2. Sign-up now using this link and get free coupons of worth $54.

CH340C Software and installation:

Because I am using Alternative of real serial programmer which is cheap but compatible. So, we have to download the supporting drivers for this. Which can recognise the port and successfully built a communication between the Arduino IDE and programmer.

<img width="218" alt="ice_screenshot_20230310-213249" src="https://user-images.githubusercontent.com/97245507/224406629-c832e57d-dbee-4079-ad82-11be378731e8.png">

You can download the drivers directly from here and install them in your computer. To verify the installation, go the device manager and see the Port section in your windows.

Troubleshooting guide:

<img width="503" alt="ice_screenshot_20230310-212817" src="https://user-images.githubusercontent.com/97245507/224406645-122f33b4-99a6-4d27-994a-9d783ea7155b.png">

Sometimes it becomes very annoying and your programmer is not communicating either with MCU or Arduino IDE. The problem may lie in the PCB or schematics. But my schematics and PCB are well tested and certified. You can use these designs if there is any problem then troubleshoot from here: Arduino ch340g troubleshooting, fixing errors and drivers.

Programming Arduino:

![My Video2](https://user-images.githubusercontent.com/97245507/224406670-b9d7950e-8262-4735-b59d-7834fed0e2f7.gif)

I tested this programmer with the IC and directly with the microcontroller unit. In both cases results are good. Just plug the microcontroller via programming headers and we are good to go and program. A very thanks to JLCPCB for the PCB, check the new PCB offers and order your first PCB in just $2.

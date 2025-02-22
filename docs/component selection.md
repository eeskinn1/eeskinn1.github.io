---
title: Component Selection
---

## Voltage Regulator Selection

|       Solution 1       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![LM2576HVS-3.3](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/LM2576HVS-3.3.jpg?raw=true) <br> [LM2576HVS-3.3](https://www.digikey.com/en/products/detail/umw/LM2576HVS-3-3/16705917) <br> - $8.45| - High Voltage Input <br> - 3 Amp output <br> - Easier to solder size | - Lower Efficiency (75% @ 3.3V) |

|       Solution 2       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![LM2674M-3.3](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/LM2674M-3.3.jpg?raw=true) <br> [LM2674M-3.3](https://www.digikey.com/en/products/detail/texas-instruments/LM2674M-3-3-NOPB/287129) <br> - $3.97 | - 86% efficiency @ 3.3V <br> - Cheapest <br> - Easy to hand solder design  | - 500mA output  |

|       Solution 3       |     Pro       |     Con       |
|------------------------|---------------|---------------|
| ![LM2676S-3.3](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/LM2676S-3.3.jpg?raw=true) <br> [LM2676S-3.3](https://www.digikey.com/en/products/detail/texas-instruments/LM2676S-3-3-NOPB/363809) <br> - $5.72| - 86% efficiency @ 3.3V <br> - 3A Output | - Lower input Voltage |

The LM2676S-3.3, Solution 3 is the optimal choice because it provides a high 3A output while maintaining 86% efficiency, reducing
heat generation and power loss. Its 260 kHz switching frequency allows for smaller inductors and capacitors, making the design more
compact and responsive to load changes compared to the lower-frequency LM2576HVS-3.3. While the LM2674M-3.3 is efficient, its 500mA limit is too low for my needs.

## Comparator Selection <!-- <img src="  " width="500"> -->

|       Solution 1       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|<img src="https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Component%20Selection/LM393DT.jpg?raw=true" width="200"> <br> [LM393DT](https://www.digikey.com/en/products/detail/stmicroelectronics/LM393DT/591695) <br> - $0.20 | - SPI communication <br> - 8 channels in case more are needed later <br> - Inexpensive | -  More Microcontroller Pins|

|       Solution 2       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|<img src="https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Component%20Selection/TLV7022DGKR.jpg?raw=true" width="200"> <br> [TLV7022DGKR](https://www.digikey.com/en/products/detail/texas-instruments/TLV7022DGKR/12165131) <br> - $0.84 | - Programmable gain amplifier <br> - Very Precise (16 bit) | - Expensive <br> - I²C interface|

|       Solution 3       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![ADS7830IPWR](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/ADS7828EB.jpg?raw=true) <br> [ADS7830IPWR](https://www.digikey.com/en/products/detail/texas-instruments/ADS7830IPWR/1689491) <br> - $2.99 | - I2C Interface <br> - Any I2C setting <br> - Many inputs | - Low Voltage range <br> |

The ADS7830 is the best choice because it features an I²C interface, which minimizes the number of microcontroller pins required. Its 8-bit resolution aligns well with my 8-bit microcontroller, ensuring efficient data handling without unnecessary overhead. Additionally, its low power consumption makes it ideal for applications where energy efficiency is important. While other ADCs may offer higher resolution, the ADS7830 balances performance, simplicity, and compatibility at a cost-effective price.

## Shift Register Selection

|       Solution 1       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![74HC165](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/SN74HC165DR.jpg?raw=true) <br> [74HC165](https://www.digikey.com/en/products/detail/texas-instruments/SN74HC165DR/377068) <br> - $0.22 | - 8 bit <br> - High speed <br> - 3 PIC pins| - 5V Output Drive |

|       Solution 2       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![CD4021](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/CD4021BQDRQ1.jpg?raw=true) <br> [CD4021](https://www.digikey.com/en/products/detail/texas-instruments/CD4021BQDRQ1/2295638) <br> - $0.56 | - 3 PIC pins <br> - Inexpensive  | -  Less Precise <br> - Slower than 74HC165|

|       Solution 3       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![MC74HC165A](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/MC74HC165ADR2G-Q.jpg?raw=true) <br> [MC74HC165A](https://www.digikey.com/en/products/detail/onsemi/MC74HC165ADR2G-Q/23329450) <br> - $0.99 | - Faster Clock <br> - 3 Pins | - More expensive <br> - Less Common |

The 74HC165 is a great choice because it allows 8 digital inputs to be read using only three microcontroller (PIC) pins, significantly reducing GPIO usage. It operates at high speed, making it well-suited for applications requiring fast data transfer. Additionally, at just $0.22, it is a very cost-effective solution for expanding digital inputs.

## Sensor Selection

|       Solution 1       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![IR sensor](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/HiletgoIR.png?raw=true) <br> [HiLetgo Infrared Emitter and Receiver](https://www.amazon.com/HiLetgo-Infrared-Emitter-Receiver-Emission/dp/B00M1PN5TK/ref=sr_1_4?sr=8-4) <br> - $0.55 per pair | - High Accuracy <br> - Fast Response Time <br> - Inexpensive | - Requires Alignment |

|       Solution 2       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![A1308KUA-1-T](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/A1308KUA-1-T.jpg?raw=true) <br> [A1308KUA-1-T](https://www.digikey.com/en/products/detail/allegro-microsystems/A1308KUA-1-T/6821585) <br> - $1.26 | - Accurate <br> - Easier | - Ball must be magnetized <br> - Interference from Coil|

|       Solution 3       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![HC-SR04](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/HC-SR04.jpg?raw=true) <br> [HC-SR04](https://www.digikey.com/en/products/detail/osepp-electronics-ltd/HC-SR04/11198533) <br> - $5.95 | - Easy to set up  <br> - Not Light dependent| - Expensive <br> - Slow |

The HiLetgo Infrared Emitter and Receiver is an excellent choice due to its high accuracy in detecting objects, making it ideal for precise ball-tracking applications. It also has a fast response time, ensuring real-time detection without significant delays. Additionally, at $0.55 per pair, it is cost-effective for implementing multiple detection points within budget. However, it requires proper alignment between the emitter and receiver, which may add complexity to installation and calibration.

## Microcontroller Selection

The class of microcontrollers that we will be using is an 8-bit Microchip PIC microcontroller
which has many forms and pin counts. This brand of microcontroller is appealing because of
prior experience with this component. My responsibilities in this project is the sensing capabilities. So I will be using a series of 8 pairs of Infrared receivers and emitters to sense the passing of a metal ball prior to the activation of an electromagnetic coil causing the ball to accelerate. Because there is no digital sensor in our plans I am required to add a PISO Register Shift Chip in my components. So the infrared sensor will go to an ADC then to the chosen shift register then to my PIC microcontroller.

| PIC Info                                      | Answer | 
| --------------------------------------------- | ------ | 
| Model                                         | PIC18F27Q10      |
| Product Page URL                              | [MicroChip Product Page](https://www.microchip.com/en-us/product/pic18f27q10)       |
| Datasheet URL(s)                              | [Product Datasheet](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/DataSheets/PIC18F27-47Q10-Micorcontroller-Data-Sheet-DS40002043.pdf)      |
| Application Notes URL(s)                      | [5-Bit Digital-to-Analog Converter](https://www.microchip.com/en-us/application-notes/tb3238) - [Writing C-Code for PIC18F](https://www.microchip.com/en-us/application-notes/tb3261)  - [SPI Using MSSP on PIC18](https://www.microchip.com/en-us/application-notes/tb3265) - [Using EUSART on PIC18](https://www.microchip.com/en-us/application-notes/tb3282)   |
| Vendor link                                   | [Digikey](https://www.digikey.com/en/products/detail/microchip-technology/PIC18F27Q10-E-SO/12807408?0=%2Fmicrocontrollers&s=N4IgjCBcoGwJxVAYygMwIYBsDOBTANCAPZQDaIALAAxwDMdIAuoQA4AuUIAymwE4CWAOwDmIAL6EwAJjgRoIFJAw4CxMuBgBWAOzaEzEO048BI8YQC0FRArRY8hEpHJSpmgBwwmEkBa-zFPgBXVSdyWm8fKXUABQBJAGEwdwAxKW0ARTAqbyA)      |
| Code Examples                                 | [EUSART Receive Control Commands](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-eusart-commands-fs/tree/1.0.2) - [EUSART Send Formatted Messages Using printf](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-eusart-printf-bare/tree/1.0.3) - [Receiving Data as an SPI Device](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-spi-client-receive-bare/tree/1.0.0) - [Sensor Data Acquisition using 10-bit ADCC](https://github.com/microchip-pic-avr-examples/pic18f47q10-adcc-sensor-data-acquisition-mplab/tree/1.0.1)      |
| External Resources URL(s)                     | [PIC Forum](https://www.reddit.com/r/pic_programming/)      |
| Unit cost                                     | $1.60      |
| Absolute Maximum Current for entire IC        | 350mA      |
| Supply Voltage Range                          |  1.8V / 3.3 - 5V / 5.5V / ~5.5V      |
| Maximum GPIO current <br> (per pin)           | 25mA      |
| Required Programming Hardware, Cost, URL      | Programming: [PG164100](https://www.digikey.com/en/products/detail/microchip-technology/PG164100/9562532) - $15.30      |
| Works with MPLabX?                            | Yes      |
| Works with Microchip Code Configurator?       | Yes (See Below)      |

| Module | # Available | Needed |
| ---------- | ----------- | ------ |
| GPIO       | 36x           | 6x      |
| ADC        | 35x           | 0x      |
| UART       | 2x           | 2x      |
| SPI        | 2x           | 2x      |
| I2C        | 2x           | 2x      |
| PWM        | 2x           | 0x      |
| ICSP       | 1x           | 1x      |
| Clock      | 2x           | 2x      |

![MPlabtest](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/MPlabtest.png?raw=true)

The PIC18F47Q10 provides ample pins for this configuration, and my MCC setup shows that each peripheral is allocated to dedicated pins with no overlapping assignments. Additionally, by matching the peripheral requirements with the microcontroller’s available pins, we ensure communication and programming while maintaining flexibility for extra GPIO if needed. Overall,  my MCC configuration indicate that there are enough pins for all intended functions and no apparent errors in the pin assignments.

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

## Analog Digital Converter Selection

|       Solution 1       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![MCP3008](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/MCP3008.jpg?raw=true) <br> [MCP3008](https://www.digikey.com/en/products/detail/microchip-technology/MCP3008T-I-SL/319424) <br> - $2.90 | - SPI communication <br> - 8 channels in case more are needed later <br> - Inexpensive | -  More Microcontroller Pins|

|       Solution 2       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![ADS1115IDGST](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/ADS1115IDGST.jpg?raw=true) <br> [ADS1115IDGST](https://www.digikey.com/en/products/detail/texas-instruments/ADS1115IDGST/2123298) <br> - $6.29 | - Programmable gain amplifier <br> - Very Precise (16 bit) <br> -  | - Expensive <br> - I²C interface|

|       Solution 3       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![ADS7828EB](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/ADS7828EB.jpg?raw=true) <br> [ADS7828EB](https://www.digikey.com/en/products/detail/texas-instruments/ADS7828EB-2K5/1689484) <br> - $6.52 | - 12-bit resolution <br> -  <br> -  | - external reference voltage <br> -  I²C Bus Congestion|

## Shift Register Selection

|       Solution 1       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![74HC165](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/SN74HC165DR.jpg?raw=true) <br> [74HC165](https://www.digikey.com/en/products/detail/texas-instruments/SN74HC165DR/377068) <br> - $0.22 | - 8 digital inputs <br> - High speed <br> - 3 PIC pins| - 5V Output Drive |

|       Solution 2       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![CD4021](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/CD4021BQDRQ1.jpg?raw=true) <br> [CD4021](https://www.digikey.com/en/products/detail/texas-instruments/CD4021BQDRQ1/2295638) <br> - $0.56 | - 3 PIC pins <br> - Inexpensive  | -  Less Precise <br> - Slower than 74HC165|

|       Solution 3       |     Pro       |     Con       |
|------------------------|---------------|---------------|
|![MC74HC165A](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/MC74HC165ADR2G-Q.jpg?raw=true) <br> [MC74HC165A](https://www.digikey.com/en/products/detail/onsemi/MC74HC165ADR2G-Q/23329450) <br> - $0.99 | - Faster Clock <br> - 3 Pins | - More expensive <br> - Less Common |


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


## Microcontroller Selection

The class of microcontrollers that we will be using is an 8-bit Microchip PIC microcontroller
which has many forms and pin counts. This brand of microcontroller is appealing because of
prior experience with this component. My responsibilities in this project is the sensing capabilities. So I will be using a series of 8 pairs of Infrared receivers and emitters to sense the passing of a metal ball prior to the activation of an electromagnet causing the ball to accelerate. Because there is no digital sensor in our plans I am required to add a PISO Register Shift Chip in my components. On the topic of pin selection and quantification, I will need:

- 4x Uart Pins
- 4x GPIO Pins
- 2x Clock Pins
- 2x SPI Pins
- 1x ADC Pin
- 1x Vcc Pin
- 2x Vss Pin
Total is 16 Pins





| PIC Info                                      | Answer | Help                                                                                                      |
| --------------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------- |
| Model                                         | PIC18F27Q10      | Include the entire part number (leave off any letters at the end that specify the package type)           |
| Product Page URL                              | [MicroChip Product Page](https://www.microchip.com/en-us/product/pic18f27q10)       | Do not paste links directly into the table.  Use a [link](#)                                              |
| Datasheet URL(s)                              | [Product Datasheet](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/DataSheets/PIC18F27-47Q10-Micorcontroller-Data-Sheet-DS40002043.pdf)      | Do not paste links directly into the table.  Use a [link](#)                                              |
| Application Notes URL(s)                      | [5-Bit Digital-to-Analog Converter](https://www.microchip.com/en-us/application-notes/tb3238) - [Writing C-Code for PIC18F](https://www.microchip.com/en-us/application-notes/tb3261)  - [SPI Using MSSP on PIC18](https://www.microchip.com/en-us/application-notes/tb3265) - [Using EUSART on PIC18](https://www.microchip.com/en-us/application-notes/tb3282)   | Do not paste links directly into the table.  Use a [link](#)                                              |
| Vendor link                                   | [Digikey](https://www.digikey.com/en/products/detail/microchip-technology/PIC18F27Q10-E-SO/12807408?0=%2Fmicrocontrollers&s=N4IgjCBcoGwJxVAYygMwIYBsDOBTANCAPZQDaIALAAxwDMdIAuoQA4AuUIAymwE4CWAOwDmIAL6EwAJjgRoIFJAw4CxMuBgBWAOzaEzEO048BI8YQC0FRArRY8hEpHJSpmgBwwmEkBa-zFPgBXVSdyWm8fKXUABQBJAGEwdwAxKW0ARTAqbyA)      | Digikey, Jameco, etc.  Do not paste links directly into the table.  Use a [link](#)                       |
| Code Examples                                 | [EUSART Receive Control Commands](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-eusart-commands-fs/tree/1.0.2) - [EUSART Send Formatted Messages Using printf](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-eusart-printf-bare/tree/1.0.3) - [Receiving Data as an SPI Device](https://github.com/microchip-pic-avr-examples/pic18f47q10-cnano-spi-client-receive-bare/tree/1.0.0) - [Sensor Data Acquisition using 10-bit ADCC](https://github.com/microchip-pic-avr-examples/pic18f47q10-adcc-sensor-data-acquisition-mplab/tree/1.0.1)      | url(s) for libraries on github or other sites related to the microcontroller and your planned peripherals |
| External Resources URL(s)                     | [PIC Forum](https://www.reddit.com/r/pic_programming/)      | Search on Google and YouTube for other resources for each specific microcontroller.                       |
| Unit cost                                     | $1.60      | Find in the Microchip online store, or Digikey                                                            |
| Absolute Maximum Current for entire IC        | 350mA      | Find in the microcontroller datasheet                                                                     |
| Supply Voltage Range                          |  1.8V / 3.3 - 5V / 5.5V / ~5.5V      | Min / Nominal / Max / Absolute Max, as found in datasheet                                                 |
| Maximum GPIO current <br> (per pin)           | 25mA      | as found in datasheet                                                                                     |
| Supports External Interrupts?                 | ?      | as found in datasheet                                                                                     |
| Required Programming Hardware, Cost, URL      | Programming: [PG164100](https://www.digikey.com/en/products/detail/microchip-technology/PG164100/9562532) - $15.30      | found on the microcontroller's product page                                                               |
| Works with MPLabX?                            | Yes      | Required.  See [Microchip Development Tools](https://www.microchip.com/development-tools)                 |
| Works with Microchip Code Configurator?       | Yes (See Below)      | Can be validated in MPLabX.  Screenshot required.                                                         |


| Module | # Available | Needed | Associated Pins (or * for any) |
| ---------- | ----------- | ------ | ------------------------------ |
| GPIO       | ?           | ?      | ?                              |
| ADC        | ?           | ?      | ?                              |
| UART       | ?           | ?      | ?                              |
| SPI        | ?           | ?      | ?                              |
| I2C        | ?           | ?      | ?                              |
| PWM        | ?           | ?      | ?                              |
| ICSP       | ?           | 1      | ?                              |
| ...        | ...         | ...    | ...                            |


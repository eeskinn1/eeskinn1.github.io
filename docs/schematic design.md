---
title: Schematic Design and Power Budget
---

## Schematic

The schematic design satisfies user needs and product requirements by enabling real-time detection and response to object movement using a compact and efficient hardware layout. Infrared sensors interface with a shift register, allowing simultaneous sampling of multiple sensor inputs while conserving microcontroller I/O pins. The PIC18F27Q10 processes this data rapidly via SPI and triggers an LED indicator when a ball is detected, providing immediate user feedback. Additionally, UART communication is implemented to relay sensor events to external systems, ensuring seamless integration with other modules such as data loggers or wireless controllers. The system is optimized for low power consumption and modularity, supporting easy hardware scaling and reliable long-term operation—all essential for meeting the functional and performance expectations of the project.

If I were to make a 2.0 version I would change the inductor I used. The one I used was only rated for 100mA which was obviously not enough. So I had to order a different one that could handle up to 4.7A and it didn't fit in the same footprint despite my research saying otherwise. But I was able to solder it in using extra resistor legs as sudo traces. Also I had an issue with my voltage regulator where the on state was only active with the pin pulled high. And I wired the output of the voltage regulator to the on off pin. So I had to wire a voltage divider to that pin with two 10k to make 4.5V from the 9V out of the 4x2 connector. I had a similar issues with my comparators where I mistakenly tied the reference pins to ground thinking that it would operate the same with the high low from the IR sensors. With the same fix I put a voltage divider bringing 3.3V down to 1.65V for all 4 of the reference voltage pins. Also I rushed my design when it comes to extra silkscreen information and markers. I would have marked each sensor board header. I would have labeled all my breakout headers with the pins from the microcontroller. I would have changed a bunch of layout stuff so the sensor headers were all at the bottom or edge to minimize the amount of wires going in and out. I also would have considered 90 degree headers for the sensor boards and the sensor headers on my main board it could have made it easier to see and mess with small part on my board wile having sensors plugged in.

### Pictures of Populated PCB

![Front](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/IMG_2443.HEIC?raw=true)

![Schematic](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/IMG_2444.HEIC?raw=true)

### PIC Microcontroller Schematic

![Schematic](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Schematic%20Design/PICSystem.png?raw=true)

### Infrared Sensor Schematic

![Schematic](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Schematic%20Design/InfraredSystem.png?raw=true)

## PCB Design

### PIC Microcontroller PCB Layout

![PCB Layout](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Schematic%20Design/PICSystem1.png?raw=true)

![PCB Layout](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Schematic%20Design/PICSystem2.png?raw=true)

### Infrared Sensor PCB Layout

![PCB Layout](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Schematic%20Design/InfraredSystem1.png?raw=true)

![PCB Layout](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Schematic%20Design/InfraredSystem2.png?raw=true)

## Files

[Click here to access PDF and Zip Files](https://github.com/eeskinn1/eeskinn1.github.io/tree/main/Assets/Schematic%20Design)

Schematic made in Altium Designer.

## Power Budget

<img src="https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Component%20Selection/SensorPowerBudget.png?raw=true">

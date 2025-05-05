---
title: Block Diagram
---

## Sensor Block Diagram

![Block Diagram](https://github.com/eeskinn1/eeskinn1.github.io/blob/main/Assets/Skinner310.drawio.png?raw=true)

Originally I was going to use an Analog to Digital Converter (ADC) to convert the analog voltage from the sensor to a digital value. However, I found that the ADC was overkill for what I needed it to do. I went for a simple and common comparator because it would be easier to implement, and have less points of possible failure. The biggest concern for me was implementing the shift register. I had never worked with one in the past. It ended up working well and being very responsive.

&copy; 2025 Evan Skinner. All rights reserved.

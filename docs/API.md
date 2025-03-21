---
title: Sensor API
tags:
- tag1
- tag2
---

## Message Structure

Start Byte (2 uint8_t) <br>
Sender Address (uint8_t)<br>
Receiver Address (uint8_t)<br>
Message Type (uint8_t)<br>
Message (1-56 uint8_t)<br>
Stop Byte (2 uint8_t)<br>

## Team Definitions

### Team Bytes

| Type |  Byte  |
| -----------| ----------- |
| Start | AZ  |
| Stop | YB |

### Team Addresses

| Name |  Address  |
| -----------| ----------- |
| Noah Brent | N  |
|Evan Skinner| E |
|Kirk Volin| K |
|Hunter Hassebroek| H |
| Broadcast | X |

## Recieved Messages

### Message Type 14 (Master Reset)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Master Reset  |
|Variable Type| char  |
|Min| RST |
|Max| RST |
|Example| RST |

## Sent Messages

### Message Type 1 (Start Communication)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Com Ready |
|Variable Type| uint8_t  |
|Min| 0 |
|Max| 1 |
|Example| 1 |

### Message Type 2 (Ball Speed)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Sensor Location |
|Variable Type| uint8_t  |
|Min| 0  |
|Max| 100 |
|Example| 2  |

### Message Type 3 (Error)

|  |  Byte 1  |  Byte 2  |
| -----------| ----------- |----------- |
|Message|  Error  | Sensor Error |
|Variable Type| uint8_t | uint8_t |
|Min| 0  | 0 |
|Max| 5  | 3 |
|Example| 1 (Reset)| 3 (Sensor 4 Error) |

Error Types:
0: Incorrect / No Start Bit
1: Incorrect / No Address Bit
2: Incorrect / No Message Type
3: Incorrect / No Stop Bit
4: Incorrect Data Value in Valid Message
5: Bytes per Message Overflow

## Code Handling

### Message Handling

1. Identify the start of a message and begin copying it to an array for retransmission.

2. When the Receiver Byte is identified, determine if it is addressed to me or broadcast:

    2a. If not mine, finish copying to the retransmission array and retransmit.

    2b. If mine, proceed to step 3.

    2c. If broadcast, copy to the retransmit array, retransmit, and continue to step 3.

1. Identify the Message Type.

2. Process the message and extract relevant sensor data.

3. Discard the message after processing.

4. Transmit the collected sensor data based on the message type.

5. When a new message is received, restart from step one.

Each step includes error checking to validate the message. If a message fails validation, an error code and the sender's address will be transmitted. If characters are received outside of valid start and stop bits, they are ignored and discarded.

### Error/Message Transmission Handling

1. Whenever an event triggers data transmission (e.g., periodic sensor readings, error detection, or reset), begin constructing the message in an array.

2. Start by adding the start bytes and the Sensor Subsystem address to a temporary array.

3. Include the receiving address, which will typically be MQTT, HMI, or broadcast.

4. Append the message type byte, following the defined messaging protocol.

5. Add the sensor data and terminate the message with stop bytes.

6. If a transmission is already in progress, wait for completion, apply a delay, then send.

7. If no transmission is ongoing, send the message immediately.

8. Clear the temporary sending array after transmission.

A group transmission schedule may be implemented to enhance message reliability and minimize data loss.

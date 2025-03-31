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

### Message Type 14 - (Master System Reset)

- Broadcast message from remote user on MQTT to trigger reset on the system. 
- If RST is sent to the MQTT SUB, it will trigger this static message to reset all subsystems.

|  |  Byte 1: Sender     |  Byte 2: Receiver | Byte 3: Data Type | Byte 4: Data  |
| -----------| ----------- | --| --| -- |
|Variable Name| MQTT_ID  | BROADCAST_ID| masterReset | resetState |
|Variable Type| char  | char | char| uint8_t |
|Min| K  | X | R | 1|
|Max| K  | X | R |1|
|Example| K | X | R | 1|

## Sent Messages

### Message Type 1 (Start Communication)

|  |  Byte 1: Sender     |  Byte 2: Receiver | Byte 3: Data Type | Byte 4: Data  |
| -----------| ----------- | --| --| -- |
|Variable Name| SENSOR_ID  | Broadcast_ID| Uart_state | Uart_ready |
|Variable Type| char  | char | char| uint8_t |
|Min| E  | X | R | 1|
|Max| E  | X | R |1|
|Example| E | X | R | 1|

### Message Type 2 (Ball Speed)

|  |  Byte 1: Sender     |  Byte 2: Receiver | Byte 3: Data Type | Byte 4-: Data  |
| -----------| ----------- | --| --| -- |
|Variable Name| SENSOR_ID  | HMI_ID| Sensor_data | Ball_speed |
|Variable Type| char  | char | char| uint8_t |
|Min| E  | H | S | 00|
|Max| E  | H | S |99|
|Example| E | H | S | 52|

### Message Type 3 (Error)

|  |  Byte 1: Sender     |  Byte 2: Receiver | Byte 3: Data Type | Byte 4: Data  |
| -----------| ----------- | --| --| -- |
|Variable Name| SENSOR_ID  | MQTT_ID| Uart_state | Uart_ready |
|Variable Type| char  | char | char| uint8_t |
|Min| E  | K | F | 1|
|Max| E  | K | F |1|
|Example| E | K | F | 1|

Error Types:
0: Incorrect / No Start Bit <br>
1: Incorrect / No Address Bit<br>
2: Incorrect / No Message Type<br>
3: Incorrect / No Stop Bit<br>
4: Incorrect Data Value in Valid Message<br>
5: Bytes per Message Overflow<br>

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

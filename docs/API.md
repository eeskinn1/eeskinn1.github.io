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

### Message Type 5 - (Master System Reset)

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

### Message Type 1 (Sensor State)

|  | Message Byte 1-2 <br> Message Prefix | Byte 3 <br> Sender ID | Byte 4 <br> Receiver ID | Byte 5 <br> Data Type | Byte 6 <br> Data Value| Byte 7 <br> Data Value | Byte 8-9 End Message |
| -----------| --- |----------- | --| --| -- | -- | -- |
|Variable Name| Message Start |SENSOR_ID  | HMI_ID| Sensor_data | Sensor_State | Sensor_Location | End Message |
|Variable Type| char |char  | char | char| char | char | char |
|Min| AZ |E  | H | S | 0| 1 | YB |
|Max| AZ |E  | H | S | 1 | 4 | YB |
|Example| AZ |E | H | S | 0 | 2 | YB |

### Message Type 2 (Error)

|  | Message Byte 1-2 <br> Message Prefix | Byte 3 <br> Sender ID | Byte 4 <br> Receiver ID | Byte 5 <br> Data Type | Byte 6 <br> Data Value| Byte 7-8 End Message |
| -----------| --- |----------- | --| --| -- | -- |
|Variable Name| Message Start |SENSOR_ID  | BROADCAST_ID| Error | Error_type | End Message |
|Variable Type| char |char  | char | char| uint8_t | char |
|Min| AZ |E  | X | F | 0| YB |
|Max| AZ |E  | X | F |5| YB |
|Example| AZ |E | X | F | 2| YB |

Error Types:
0: Incorrect / No Start Bit <br>
1: Incorrect / No Address Bit<br>
2: Incorrect / No Message Type<br>
3: Incorrect / No Stop Bit<br>
4: Incorrect Data Value in Valid Message<br>
5: Bytes per Message Overflow<br>

## Code Handling

Message Structure
All messages follow this standardized format:

Start Sequence: 2-byte header (AZ)

Addressing:

Sender identifier (1 byte)

Receiver identifier (1 byte)

Payload:

Command type (1 bytes)

Data field (variable length)

Termination: 2-byte footer (YB)

## Message Handling Workflow

### Message Reception

1. System continuously monitors for valid start sequence

2. Verify sender/receiver identifiers against authorized device list

3. Confirm message length within protocol limits

4. Check for proper termination sequence

### Message Processing

1. Messages addressed specifically to the device are processed internally

2. Broadcast messages are both processed and retransmitted

3. Messages for other devices are immediately forwarded

4. Reset commands trigger system reinitialization

5. Data messages update internal state variables

### Error Handling

Validation Failures:

1. Malformed headers/terminators

2. Unauthorized sender/receiver

3. Protocol violations

Error Reporting:

1. Automatic error code transmission

2. Includes source of problematic message

3. Maintains communication logs

### Transmission Protocol

Message Generation

1. Automatic inclusion of device identifier

2. Dynamic payload construction based on event type

3. Proper termination sequence appended

Prioritization:

1. Error messages take transmission priority

2. Sensor data transmitted on state change

Transmission Management

1. Minimum inter-message spacing enforced

2. Automatic retransmission for critical messages


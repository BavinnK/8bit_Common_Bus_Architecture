# 8-bit Common Bus Architecture (3 Registers)

This project is an implementation of a **Common Bus Configuration**, designed for a Computer Organization and Architecture course assignment. It features three independent 8-bit registers that share a single 8-bit common bus using Tri-state buffers for arbitration.

## Project Overview
In computer architecture, a common bus allows multiple components to communicate over a shared set of wires. To prevent data contention (short circuits), only one register is allowed to "talk" to the bus at a time. This design uses:
- **6x SN74LS175N** ICs to create three 8-bit registers.
- **6x SN74HC125N** ICs to provide Tri-state buffering for bus access.
- Manual control via DIP switches for data input and push-buttons for Clock/Bus Enable signals.

## System Architecture
Each 8-bit register is composed of two 4-bit D-type Flip-Flop ICs. Each register's output is connected to a Tri-state buffer. 
* **Input:** Data is set via 8-position DIP switches.
* **Storage:** Data is loaded into a register on a Clock Pulse (CP).
* **Bus Access:** A register's data is placed on the common bus only when its corresponding Buffer Output Enable (OE) is pulled low.

## Hardware Components
| Component | Part Number | Quantity |
| :--- | :--- | :--- |
| Quad D-Type Flip-Flops | SN74LS175N | 6 |
| Quad Tri-State Buffers | SN74HC125N | 6 |
| 8-Position DIP Switch | 219-8LPST | 3 |
| Push Buttons | SPST PB | 9 |
| LED Array | Standard 5mm | 24 |
| Resistors | Various (Pull-downs/Limiting) | ~60 |

## Technical Implementation Notes
A unique challenge for this project was the component availability in the Kurdistan region of Iraq. Due to limited local stock, this build utilizes a hybrid of **LS (Low-power Schottky TTL)** for the registers and **HC (High-speed CMOS)** for the buffers. 

While mixing logic families is generally avoided in high-speed production environments, this project successfully manages the voltage level and timing compatibility for a reliable educational demonstration on a breadboard.

## Project Media

### Circuit Schematic
Comprehensive wiring diagram for the registers and bus logic.
<img width="1624" height="2017" alt="Untitled" src="https://github.com/user-attachments/assets/28728f5d-46ad-4ae0-bbf9-77d9d0ce641a" />


### Logisim Simulation
Functional verification of the logic gates and bus arbitration.

<img width="1322" height="918" alt="Screenshot 2026-03-10 222123" src="https://github.com/user-attachments/assets/45cdf947-88e9-4d34-a795-c747ab49d46a" />


### Physical Breadboard
The final completed hardware implementation.
![photo_2026-03-10_22-16-54](https://github.com/user-attachments/assets/ddb1e724-854b-459d-ac1a-19aa6a13f911)


## How to Operate
1. **Set Data:** Use the DIP switches to set the binary value for a specific register.
2. **Load Register:** Press the corresponding Clock Pulse button to store the value.
3. **Enable Bus:** Press the Output Enable button for a register to see its value reflected on the common bus LEDs.
4. **Note:** Ensure only one register is enabled at a time to maintain bus integrity.

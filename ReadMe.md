# SD-Link 5V: Professional MicroSD Interface Module

![Project Status](https://img.shields.io/badge/Status-Validated-success)
![KiCad Version](https://img.shields.io/badge/KiCad-10.0-blue)
![License](https://img.shields.io/badge/License-MIT-green)

The **SD-Link 5V** is a robust, high-performance interface module designed to bridge 5V logic systems (such as Arduino Uno, Mega, or legacy industrial MCUs) with 3.3V MicroSD cards. Unlike standard "level-shifting" breakouts that use passive resistors, this board utilizes active buffering and dedicated power regulation to ensure high-speed data integrity.

##  Key Features

- **Active Level Shifting:** Uses high-speed logic buffers to translate SPI signals (MOSI, MISO, SCK, CS) without signal degradation.
- **Dedicated Regulation:** Integrated **TLV70033 LDO** providing a stable 3.3V rail at up to 600mA.
- **ESD Protection:** Data lines are protected by a **USBLC6-2SC6** array, shielding internal components from static discharge during card insertion.
- **Professional PCB Design:** - Dual-layer copper ground planes for EMI reduction.
  - Teardrop junctions for mechanical trace-to-pad reliability.
  - 2x M2 Plated Mounting Holes (GND connected).
  - Modern typography using **IBM Plex Sans** for clear silk labeling.

##  Hardware Specifications

| Parameter | Specification |
| :--- | :--- |
| **Input Voltage (VCC)** | 5.0V DC |
| **Logic Level** | 5.0V CMOS/TTL |
| **Output Voltage** | 3.3V (Regulated) |
| **Max Output Current** | 600mA |
| **Interface** | SPI (Mode 0) |
| **Dimensions** | 40mm x 30mm |

##  Pinout Diagram

| Pin | Label | Function | Connection (Arduino Uno) |
| :---: | :--- | :--- | :--- |
| 1 | **GND** | System Ground | GND |
| 2 | **VCC** | 5V Power Input | 5V |
| 3 | **CS** | Chip Select (Active Low) | D10 |
| 4 | **MOSI** | Master Out Slave In | D11 |
| 5 | **MISO** | Master In Slave Out | D12 |
| 6 | **SCK** | Serial Clock | D13 |

##  Project Structure

- `/Hardware`: KiCad 10.0 project files (schematic, PCB layout).
- `/Production`: Gerber files, Drill files, and Pick-and-Place (CPL) files.
- `/Docs`: Validation reports and Integration Guide (PDF).

##  Software Example

This module is compatible with the standard Arduino `SD.h` library.

```cpp
#include <SPI.h>
#include <SD.h>

const int chipSelect = 10;

void setup() {
  Serial.begin(9600);
  if (!SD.begin(chipSelect)) {
    Serial.println("SD-Link: Connection Failed.");
    return;
  }
  Serial.println("SD-Link: Initialized Successfully.");
}

void loop() {
  // Your data logging code here
}
# LINTTL3 Library for Arduino

Library for controlling the LINTTL3 module, which converts TTL/UART signals to LIN and vice versa. The module uses the TJA1021 chip and supports data transfer rates up to 20 kbit/s.

## Installation

1. Download the archive with the library.
2. Unzip the archive into the `libraries` folder of your Arduino IDE.
3. Restart the Arduino IDE.

## Module Connection

The LINTTL3 module has 8 pins:

* **Side 1:**
  - RX: Data reception from the LIN bus.
  - SLP: Sleep mode control.
  - TX: Data transmission to the LIN bus.
  - GND: Ground.
* **Side 2:**
  - +12V: Module power supply (12V/24V).
  - INH: Control of external voltage regulator (used in master mode).
  - LIN: LIN bus.
  - GND: Ground.

### Connection to Arduino:

* **RX**: Connect to the RX pin on the Arduino (or any other pin for software UART).
* **TX**: Connect to the TX pin on the Arduino (or any other pin for software UART).
* **SLP**: Connect to any digital Arduino pin to control sleep mode.
* **INH**: Connect to any digital Arduino pin to control master mode.
* **GND**: Connect to GND on the Arduino.
* **+12V**: Connect to a 12V/24V power source.

## Usage

Basic functions
void begin(): Module initialization.

void sleep(): Puts the module into sleep mode.

void wakeUp(): Wakes the module up from sleep mode.

void sendLIN(byte data): Sends data to the LIN bus.

byte receiveLIN(): Reads data from the LIN bus.

void setMasterMode(bool isMaster): Sets master or slave mode.

### Initialization

```cpp
#include <LINTTL3.h>

// For hardware UART
LINTTL3 linModule(Serial, SLP_PIN, INH_PIN);

// For software UART (SoftwareSerial)
#include <SoftwareSerial.h>
SoftwareSerial mySerial(RX_PIN, TX_PIN);
LINTTL3 linModule(mySerial, SLP_PIN, INH_PIN);

void setup() {
  linModule.begin(); // Module initialization
  linModule.setMasterMode(true); // Set master mode

}

```

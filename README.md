# POSTAL3 AVR-USB Programmer
### Screen Flash Tool

A custom-engineered hardware tool developed for screen firmware maintenance, electronic repair, and embedded debugging applications. This programmer facilitates reliable reading, writing, and flashing operations for various EEPROM, Flash, and EMMC chips utilizing standard communication protocols and board-level In-System Programming (ISP).

---

## Table of Contents

- [Key Features & Specifications](#key-features--specifications)
- [Applications](#applications)
- [Requirements](#requirements)
- [Tested Devices](#tested-devices)
- [Hardware Overview](#hardware-overview)
- [System Setup & Driver Configuration](#system-setup--driver-configuration)
- [POSTAL3 Software Configuration & Validation](#postal3-software-configuration--validation)
- [Pinout Mapping (EMMC & JTAG)](#pinout-mapping-emmc--jtag)
- [Safety & Electrical Notes](#safety--electrical-notes)
- [Versioning](#versioning)
- [Repository Structure](#repository-structure)
- [License](#license)

---

## Key Features & Specifications

* **Supported Chip Families:** Designed to support `25CXX`, `93CXX`, `24CXX`, `45DXX`, `25EXX`, `EMMC`, `JTAG`, and `I2C` protocols.

* **Board-Level ISP:** Enables firmware flashing via exposed test pads or auxiliary interface routing present on some board designs, bypassing chip desoldering where ISP test points or routing pads are available on the target board.

* **USB Connectivity:** Integrated with the **CP210x USB-to-UART Bridge** / **USB XPRESS - X2** for stable serial data transmission.  
*(Note: USB XPRESS - X2 refers to the internal USB interface implementation used in this hardware revision and is not a standalone external chipset).*

* **Hardware Modularity:**
  * Optimized power delivery circuit with regulated voltage rails for stable operation.
  * Custom onboard jumpers for VGA & HDMI sockets to dynamically route `SDA` and `SCL` configurations based on the target board's pin layout.
  * Manual routing options for VGA pin configurations (switching between `4-11-5` and `12-15-5`) and HDMI configurations (switching between `16-15-17` and `2-14-17`) to accommodate varying manufacturer designs.

---

## Applications

* **Maintenance & Electronics Repair:** Flashing, upgrading, or recovering firmware on televisions, monitors, receivers, and control boards.

* **Embedded Systems Debugging:** Accessing board-level interfaces (via standard interfaces such as I2C and JTAG where exposed) for diagnostic purposes and firmware analysis.

---

## Requirements

* **Operating System:** Windows 7/10/11 or Linux (with native USB-serial support).
* **Drivers:** CP210x USB driver installed and configured.
* **Hardware Interface:** USB 2.0 or higher host port.
* **Firmware/OS Settings:** USB serial (COM port) enumeration support enabled in operating system or BIOS (if required by platform).
* **Target Device:** Target board with accessible ISP/test points (when applicable).

---

## Tested Devices

The hardware functionality and communication stability have been validated on:

* Various SPI Flash chips (up to 16MB capacity) under typical read, write, and verify operations.
* Common TV and monitor mainboards with accessible ISP points.

---

## Hardware Overview

### Schematic Diagram

![Schematic](images/0.jpg)

---

### Final Programmer Assembly

![Programmer](images/2.png)

---

### Programmer Adapters

![Adapters](images/3.png)

---

## System Setup & Driver Configuration

### Driver Installation Steps

When connecting the programmer to the USB port for the first time only:

### Step 1

![Step 1](images/4.png)

### Step 2

![Step 2](images/5.png)

### Step 3

![Step 3](images/6.png)

### Step 4

![Step 4](images/7.png)

### Step 5

![Step 5](images/8.png)

### Step 6

![Step 6](images/9.png)

### Step 7

![Step 7](images/10.png)

---

### Driver Installation Verification

The device has been successfully recognized on Windows.

![Driver Verification](images/11.png)

---

## POSTAL3 Software Configuration & Validation

### POSTAL3 Software Interface

Overview of the POSTAL3 software environment and configuration interface.

![POSTAL3 Interface](images/12.png)

---

### Basic POSTAL3 Settings

Basic software configuration required for stable communication.

![Settings](images/13.png)

![Settings](images/14.png)

![Settings](images/15.png)

---

### USB Driver Configuration

USB driver configuration required for proper programmer operation.

![USB Configuration](images/16.png)

---

### Communication Verification

Verifying successful driver installation and software detection of the programmer.

![Verification](images/17.png)

---

## Flash & EEPROM Validation

### Tested Flash & EEPROM Devices

Flash and EEPROM chips tested in practical use.

![Validation](images/18.png)

![Validation](images/19.png)

![Validation](images/20.png)

---

### SPI Flash Reading Test (16MB)

Reading test from a 16MB SPI Flash chip.

![SPI Read](images/21.png)

![SPI Read](images/22.png)

---

### SPI Flash Writing Test (16MB)

Writing test to a 16MB SPI Flash chip.

![SPI Write](images/23.png)

![SPI Write](images/24.png)

---

## Pinout Mapping (EMMC & JTAG)

EMMC + JTAG pinout diagram used for flashing TVs and receivers via board-level ISP points without removing the chip.

![Pinout](images/25.png)

---

### VGA & HDMI Jumper Routing

A jumper has been added to the VGA + HDMI sockets to support different SDA and SCL routing configurations used across various display boards.

#### VGA Routing

Supports switching between pin groups:

* `4-11-5`
* `12-15-5`

Including reverse routing compatibility.

![VGA Routing](images/26.png)

---

#### HDMI Routing

Supports switching between pin groups:

* `16-15-17`
* `2-14-17`

Including reverse routing compatibility.

![HDMI Routing](images/27.png)

---

## Additional Features

The programmer supports reading and writing flash and EEPROM chips used in display boards without removing them, using the dedicated VGA or HDMI sockets.

It also includes infrared (IR) transmit and receive functionality, allowing remote control code communication and modification.

![IR Support](images/28.png)

---

## Safety & Electrical Notes

> [!WARNING]
>
> * **Target Audience & Environment:** This tool is intended for use by qualified technicians familiar with hardware-level programming, board diagnostics, and electronic repair procedures. This device is designed for laboratory and controlled maintenance environments only.
>
> * **Voltage Levels:** Always verify target board and chip voltage compatibility (e.g., `1.8V` vs `3.3V`) before executing read/write commands. Operating at incorrect voltage levels may permanently damage the target IC or the programmer.
>
> * **Wiring Accuracy:** Double-check jumper configurations and ISP pinouts against the target hardware schematics. Improper voltage selection or wiring configuration may result in irreversible damage to the target IC or programming hardware.

---

## Included Files

* Latest USB driver package for the programmer.
* Latest POSTAL3 software version for the programmer.

---

## Versioning

* **Hardware:** v1.0 (Base PCB and layout design)
* **Software/Firmware:** POSTAL3 environment integration with stable CP210x drivers

---

## Repository Structure

* `/Drivers` — Certified stable USB drivers for CP210x and USB XPRESS.
* `/Software` — POSTAL3 interface files configured for this device layout.
* `/Schematics` — Pinout diagrams, jumper routing tables, and interface maps.
* `/images` — Hardware photos, validation screenshots, and setup documentation.

---

## License

This project is released under the MIT License and includes both hardware design and software utilities shared for educational and practical maintenance purposes.

See `LICENSE` for more information.

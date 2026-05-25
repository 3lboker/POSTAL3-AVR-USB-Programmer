# POSTAL3 AVR-USB Programmer
### Screen Flash Tool

A custom-engineered hardware tool developed for screen firmware maintenance, electronic repair, and embedded debugging applications. This programmer facilitates reliable reading, writing, and flashing operations for various EEPROM, Flash, and EMMC chips utilizing standard communication protocols and board-level In-System Programming (ISP).

## Key Features & Specifications

*   **Supported Chip Families:** Designed to support `25CXX`, `93CXX`, `24CXX`, `45DXX`, `25EXX`, `EMMC`, `JTAG`, and `I2C` protocols.
*   **Board-Level ISP:** Enables firmware flashing via exposed test pads or auxiliary interface routing present on some board designs, bypassing chip desoldering where ISP test points or routing pads are available on the target board.
*   **USB Connectivity:** Integrated with the **CP210x USB-to-UART Bridge** / **USB XPRESS - X2** for stable serial data transmission. *(Note: USB XPRESS - X2 refers to the internal USB interface implementation used in this hardware revision and is not a standalone external chipset).*
*   **Hardware Modularity:** 
    *   Optimized power delivery circuit with regulated voltage rails for stable operation.
    *   Custom onboard **Jumpers** for VGA & HDMI sockets to dynamically route `SDA` and `SCL` configurations based on the target board's pin layout.
    *   Manual routing options for VGA pin configurations (switching between 4-11-5 and 12-15-5) and HDMI configurations (switching between 16-15-17 and 2-14-17) to accommodate varying manufacturer designs.

## Applications

*   **Maintenance & Electronics Repair:** Flashing, upgrading, or recovering firmware on televisions, monitors, receivers, and control boards.
*   **Embedded Systems Debugging:** Accessing board-level interfaces (via standard interfaces such as I2C and JTAG where exposed) for diagnostic purposes and firmware analysis.

## Requirements

*   **Operating System:** Windows 7/10/11 or Linux (with native USB-serial support).
*   **Drivers:** CP210x USB driver installed and configured.
*   **Hardware Interface:** USB 2.0 or higher host port.
*   **Firmware/OS Settings:** USB serial (COM port) enumeration support enabled in operating system or BIOS (if required by platform).
*   **Target Device:** Target board with accessible ISP/test points (when applicable).

## Tested Devices

The hardware functionality and communication stability have been validated on:
*   Various SPI Flash chips (up to 16MB capacity) under typical read, write, and verify operations.
*   Common TV and monitor mainboards with accessible ISP points.

## System Setup & Driver Configuration

1. Connect the programmer to an available USB port.
2. Navigate to the `/Drivers` directory within this repository.
3. Install the appropriate CP210x/USB XPRESS driver for your operating system environment.
4. Verify the device is successfully recognized under COM/Ports in the Windows Device Manager.

> *[Insert driver installation and Device Manager screenshots here]*

## POSTAL3 Software Configuration & Validation

### Baseline Setup
To configure the POSTAL3 interface for communication with this hardware build, apply the parameters illustrated below:

> *[Insert POSTAL3 interface and communication setup screenshots here]*

### Functional Validation Screenshots
> *[Insert practical flashing/reading test verification screenshots here]*

## Pinout Mapping (EMMC & JTAG)

Below is the pinout guide for direct motherboard connections using ISP points for chips like EMMC and JTAG interfaces, bypassing chip desoldering where ISP test points or routing pads are available on the target board.

> *[Insert EMMC/JTAG pinout diagram screenshot here]*

## Safety & Electrical Notes

> [!WARNING]
> *   **Target Audience & Environment:** This tool is intended for use by qualified technicians familiar with hardware-level programming, board diagnostics, and electronic repair procedures. This device is designed for laboratory and controlled maintenance environments only.
*   **Voltage Levels:** Always verify target board and chip voltage compatibility (e.g., 1.8V vs 3.3V) before executing read/write commands. Operating at incorrect voltage levels may permanently damage the target IC or the programmer.
*   **Wiring Accuracy:** Double-check jumper configurations and ISP pinouts against the target hardware schematics. Improper voltage selection or wiring configuration may result in irreversible damage to the target IC or programming hardware.

## Versioning

*   **Hardware:** v1.0 (Base PCB and layout design)
*   **Software/Firmware:** POSTAL3 environment integration with stable CP210x drivers

## Repository Structure

*   `/Drivers`: Certified stable USB drivers for CP210x and USB XPRESS.
*   `/Software`: POSTAL3 interface files configured for this device layout.
*   `/Schematics`: Pinout diagrams, jumper routing tables, and interface maps.

## License

This project is released under the MIT License and includes both hardware design and software utilities shared for educational and practical maintenance purposes. See `LICENSE` for more information.

# 🔊 Audio Amplifier with Digital Volume Control (MAX5488 + TDA7377)

**Version:** 1.0  
**Author:** Obbialero Andrea  
**Date:** 27/01/2024  

---

## 📌 Project Overview

This project features a 4-channel stereo audio amplifier with digital volume control via SPI, fully integrated on a single PCB.

### Main Components:
- **MAX5488** – Digital potentiometer controlled via SPI  
- **TDA7377** – Power amplifier for audio output  
- Separate power supplies for logic and amplification sections

---

## 🔧 Technical Specifications

| Feature            | Value                             |
|--------------------|------------------------------------|
| Audio Channels     | 4 (stereo ×2)                      |
| Amplifier          | TDA7377                            |
| Volume Control     | Digital via SPI (MAX5488)          |
| Power Supplies     | +24V, +12V, +5V                    |
| Regulators         | XL4016 (Buck), LM7805 (Linear)     |
| Audio Inputs       | PJ-3200 Jack                       |
| Audio Outputs      | 4-pin Connectors                   |
| PCB                | Custom-designed from scratch       |

---

## 📦 Bill of Materials (BOM)

See the [complete BOM](https://github.com/Obbialero/Amplifier-V1.0/blob/main/hardware/BOM_PCB_AMPLIFIER_V1.0.csv) for all components used, including part numbers, values, and technical notes.

---

## 🔌 Block Diagram

![Block Diagram](docs/schema_a_blocchi_pcb.png)

---

## 🎚️ Digital Volume Control (SPI)

The volume is controlled via the **MAX5488**, a dual digital potentiometer that enables separate adjustment for the **right (DX)** and **left (SX)** audio channels.

This project uses an **STM32L432KC microcontroller** (low-power STM32 series from STMicroelectronics) to control the MAX5488 via **SPI**.  
However, the system is compatible with any SPI-capable microcontroller such as **Arduino**, **ESP32**, **Raspberry Pi Pico**, etc.

### 🧪 SPI Interface – Signals Used:

| Signal   | Description               |
|----------|---------------------------|
| **SCLK** | Serial Clock              |
| **DIN**  | Serial Data Input         |
| **CS#**  | Chip Select (active low)  |

The MAX5488 retains the last set value even when the SPI signal is inactive, making it ideal for embedded audio systems requiring precise and persistent software control.

---

## 🧱 Filtering and Protection

| Component         | Function                                  |
|-------------------|-------------------------------------------|
| LC Filter         | 47 µH + 100nF–1000µF on Vcc lines          |
| Schottky Diode    | VS-10BQ040-M3 on +24V line                |
| 1N4148 Diode      | Protection for digital signals            |
| Capacitors        | Bypass, placed close to power pins        |

---

## 📎 Connectors

| Component | Function                  |
|-----------|---------------------------|
| PJ-3200   | Stereo audio input        |
| U11/U13   | 4-pin audio output        |
| P11       | Power input               |

---

## 🛠️ PCB Design Recommendations

- Power traces (24V/12V): ≥2 mm width  
- Ground separation: keep PW-GND (power) and S-GND (signal) isolated  
- SPI lines: keep as short as possible to reduce noise  
- Bulk capacitors: placed near XL4016 and TDA7377

---

## 📁 Included Files

- [Gerber_PCB_AMPLIFIER_V1.0.zip](https://github.com/Obbialero/Amplifier-V1.0/raw/main/Gerber_PCB_AMPLIFIER_V1.0.zip) – Gerber files for PCB production  
- [BOM_PCB_AMPLIFIER_V1.0.csv](https://github.com/Obbialero/Amplifier-V1.0/raw/main/BOM_PCB_AMPLIFIER_V1.0.csv) – Bill of Materials  
- [PickAndPlace_PCB_amplifier_V1.0.csv](https://github.com/Obbialero/Amplifier-V1.0/raw/main/PickAndPlace_PCB_amplifier_V1.0.csv) – Pick & place coordinates for assembly  
- [PCB_amplifier_V1.0.json](https://github.com/Obbialero/Amplifier-V1.0/raw/main/pcb_amplifier_schematich/PCB_amplifier_V1.0.json) – PCB layout (JSON format)  
- [SCH_AMPLIFIER_V1.0.json](https://github.com/Obbialero/Amplifier-V1.0/raw/main/pcb_amplifier_schematich/SCH_AMPLIFIER_V1.0.json) – Electrical schematic (JSON format)  
- [PNG_AMPLIFIER/](https://github.com/Obbialero/Amplifier-V1.0/tree/main/docs/PNG_AMPLIFIER) – Folder with schematic and PCB images  

---

## 🖼️ Images and PCB Views

### 🔧 Electrical Schematic  
![Schematic_PCB_AMPLIFIER_V1.0](https://github.com/Obbialero/Amplifier-V1.0/raw/main/docs/PNG_AMPLIFIER/Schematic_PCB_AMPLIFIER_V1.0.png)

### 📐 PCB - 2D Layout  
![2D_PCB_AMPLIFIER_V1.0](https://github.com/Obbialero/Amplifier-V1.0/blob/main/docs/PNG_AMPLIFIER/2D_PCB_AMPLIFIER_V1.0.png)

### 🖥️ PCB - Assembled View  
![PCB_AMPLIFIER_V1.0](https://github.com/Obbialero/Amplifier-V1.0/blob/main/docs/PNG_AMPLIFIER/PCB_AMPLIFIER_V1.0.png)

---

## ⚠️ Warnings

⚠️ Caution: the 24V line may cause overheating.  
Use heatsinks on **XL4016** and **TDA7377** to avoid thermal shutdown.  
Ensure proper grounding and shielded audio connections.

---

## 📌 Usage Tips

- Provide a stable power supply according to TDA7377 specs  
- Always verify circuit integrity before mass production  
- Use a shielded enclosure to reduce audio interference  

---

## 📬 Contact

For questions, improvements, or issues:  
**Andrea Obbialero** – https://obbialero.github.io/

---

## 📘 License

This project is licensed under the **MIT License**.  
Free for personal, educational, and commercial use with attribution.

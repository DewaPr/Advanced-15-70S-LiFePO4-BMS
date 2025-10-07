# Advanced 15-70S LiFePO4 Battery Management System (BMS)

This repository contains the hardware design and firmware for a highly configurable Battery Management System. It's designed for LiFePO4 battery packs ranging from 15 to 70 cells in series, making it suitable for various electric vehicle applications.

![BMS Project Image](placeholder.png)
*(Tip: Replace this with a photo of your PCB or a system block diagram!)*

---

## Key Features
* **Scalable Architecture:** Supports **15S to 70S** LiFePO4 battery pack configurations.
* **Cell Monitoring:** Provides real-time monitoring of individual cell voltages and pack temperature.
* **Passive Balancing:** Implements a passive balancing algorithm to maintain pack health and extend its lifespan.
* **State Estimation:** Includes algorithms for State of Charge (SOC) and State of Health (SOH) estimation.
* **Safety Protections:** Features robust hardware and software protections for:
    * Over-Voltage
    * Under-Voltage
    * Over-Current (Discharge and Charge)
    * Over-Temperature
* **Communication:** Outputs key battery data via **CAN bus** and **UART**.

## Hardware
The BMS is built around a dedicated analog front-end (AFE) for precise measurements.

* **Microcontroller:** STM32F072CBT6
* **Analog Front-End (AFE):** SinoWealth SH367309. This IC is responsible for all high-voltage measurements, cell balancing, and hardware-level protection.
* **Current Sensor:** Low-side current shunt amplifier
* **Balancing Circuitry:** 100mA passive balancing with BJTs and bleed resistors

Schematics and PCB layout files are located in the `/hardware` directory.

## Firmware
The firmware is responsible for all logic, from data acquisition to safety monitoring.

1.  **Data Acquisition:** Periodically samples all cell voltages and temperatures via the AFE.
2.  **SOC Algorithm:** Utilizes **Coulomb Counting** with periodic voltage correction to accurately estimate the State of Charge.
3.  **Balancing Logic:** Activates balancing circuits for cells exceeding the average voltage during the charging phase.
4.  **Fault Detection:** Continuously checks for fault conditions and can trigger a protection circuit to disconnect the battery pack if necessary.

## Project Status: Complete
---
*Created by Dewa Pramudya, 2025*

---
*Created by [Your Name], [Year]*

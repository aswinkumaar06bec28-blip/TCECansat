# TCECansat

Intelligent Descent Stability and Wind Drift Estimation CanSat
Team Schlenk 2k26 | MEPCO Schlenk Engineering College (Autonomous)

This repository contains the design, firmware logic, and analytical frameworks for a high-performance CanSat designed to evolve micro-payload systems from passive data loggers to active analytical aerospace subsystems.

🛰️ Mission Overview
Traditional low-altitude aerial payloads often lack the onboard capability to evaluate aerodynamic stability and wind-induced drift during descent. The Schlenk 2k26 mission addresses this by performing real-time descent stability classification and wind drift trend estimation using sensor fusion.

Key Objectives
Real-time Classification: Categorize descent behavior into Stable, Mild Oscillation, or Turbulent states.

Stability Indexing: Implementation of the Dynamic Descent Stability Index (DDSI), a custom algorithm (0–100 scale) based on IMU variance.

Wind Drift Estimation: Utilize lateral acceleration integration to flag "High Drift Trends" without the need for GPS.

Data Integrity: Continuous 50Hz sampling of atmospheric and motion data, logged to a non-volatile CSV format on a Class 10 MicroSD card.

🛠️ System Architecture
Hardware Stack
Microcontroller: ESP32-WROOM (Selected for superior I/O stability and low power noise floor).

IMU: ICM-42688-P (6-axis MEMS) for high-resolution gyroscope data to detect oscillations as small as 2°.

Altimeter/Thermo: BMP280 for absolute pressure accuracy and mission state triggering.

Power: 3.7V 500mAh LiPo battery regulated by a 3.3V Buck Converter.

Mechanical Design
The structure is a 3D-printed PLA cylindrical enclosure designed for "Deterministic Reliability".

Dimensions: 108 mm (Height) x 64 mm (Diameter).

Energy Absorption: 40% Honeycomb Infill acts as a structural crumple zone to protect electronics upon impact.

Stability: Low Center of Gravity (CG) achieved by base-mounting the battery, creating a high "Restoring Moment" against wind tilt.

📊 Analytical Logic
Stability Classification (Sliding Window RMS)
The system collects 50 samples of Gyro-X and Gyro-Y over 1 second to calculate variance.
| State | Variance Threshold |
| :--- | :--- |
| Stable | < 5.0 |
| Oscillatory | 5.0 - 15.0 |
| Turbulent | > 15.0 |
(Source: PDR Section 7.1)

📂 Repository Structure
/Documentation: Preliminary Design Reports (PDR) and Mission Requirements.

/Hardware: Electrical schematics, PCB stack diagrams, and 3D CAD section views.

/Firmware: ESP32 source code for the 50Hz sampling loop and DDSI computation.

/Logs: Sample flight data including roll, pitch, and altitude metrics.

👥 Team: Schlenk 2k26
Vijayaraj K P – II CSE

Sundaravaradhan A – III ECE

Aswinkumaar M V – II ECE

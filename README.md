<p align="center">
  <img src="docs/logo.jpg" width="200">
</p>

# UW Baja Electrical DAQ System

Development of a modular electrical sensing and data acquisition system for the UW Baja SAE vehicle.

The goal of this project is to move from standalone electrical components toward an integrated vehicle sensing, communication, and data architecture.

---

## Project Goals

The Electrical DAQ system will provide reliable vehicle measurements for:

- Vehicle testing
- Troubleshooting
- Performance analysis
- Future telemetry
- Driver feedback

### Primary Measurements

- Engine RPM
- Wheel RPM / vehicle speed
- Temperature

### Future Expansion

- CAN communication
- Data logging
- Telemetry
- Dashboard / driver feedback
- Additional vehicle sensors

---

## System Architecture

```text
Physical Vehicle
      │
      ▼
    Sensors
      │
      ▼
Microcontroller
      │
      ▼
     CAN
      │
      ▼
DAQ / Data Logging
      │
      ├──────────► Dashboard
      │
      └──────────► Telemetry

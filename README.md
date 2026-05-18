# PSA HDi Diesel Diagnostics Knowledge Base

A structured repository focused exclusively on PSA HDi diesel engines and their variants, documenting real-world diagnostics, fault tracing, live-data analysis, ECU behavior studies, and repair case documentation.

The goal of this repository is to preserve:

- Real diagnostic procedures
- Fault-code interpretation
- Live data analysis methodology
- Sensor validation techniques
- OEM vs aftermarket behavior differences
- Root-cause analysis
- Final repair confirmation

This repository focuses exclusively on:

- PSA HDi diesel engines
- Peugeot / Citroën / DS platforms
- Ford / PSA shared diesel platforms
- Bosch EDC systems
- Siemens SID systems
- Turbo diesel diagnostics
- Common rail diesel systems
- CAN communication faults
- Pressure sensor correlation issues
- Vacuum and turbo control systems
- DPF and EGR diagnostics

---

# Repository Structure

```text
.
├── README.md
├── dw8
├── dv4
├── dv5
├── dv6
│   ├── issue_name
│   │   ├── report.md
│   │   ├── images
│   │   ├── live_data
│   │   └── servicebox_refs
│
├── dw10
│   ├── issue_name
│   │   ├── report.md
│   │   ├── images
│   │   └── logs
│
├── dw12
│   ├── 4hs_map_sensor_correlation_fault
│   │   ├── report.md
│   │   ├── live_data
│   │   ├── fault_codes
│   │   ├── images
│   │   └── servicebox_refs
│   │
│   └── future_issue
│
├── dt17
├── dt20
│
└── universal_hdi_diagnostics
    ├── pressure_sensor_testing
    ├── can_bus
    ├── vacuum_systems
    └── oscilloscope_reference
```

---

# Documentation Standard

Each issue folder should contain:

## `report.md`

Complete diagnostic report including:

- Vehicle information
- Engine model
- ECU type
- Symptoms
- Fault codes
- Live data analysis
- Diagnostic reasoning
- Tests performed
- Retests
- Root cause
- Final repair
- Lessons learned

---

## `images/`

Photos and screenshots such as:

- Engine bay
- Sensor locations
- Wiring
- Oscilloscope captures
- DiagBox screenshots
- Fault code screenshots
- ServiceBox references

---

## `logs/` or `live_data/`

Raw exported data:

- DiagBox logs
- OBD captures
- CSV live data
- CAN traces
- Pressure readings
- Voltage readings

---

## `servicebox_refs/`

Reference information:

- OEM part numbers
- Sensor references
- Wiring diagrams
- Vacuum diagrams
- Torque specifications

---

# Naming Convention

## Engine folders

Use OEM engine codes:

Examples:

- `dw10`
- `dw12`
- `dv6`
- `om646`
- `n47`

---

## Issue folders

Use descriptive lowercase names:

Examples:

- `map_sensor_correlation_fault`
- `vacuum_leak_underboost`
- `can_bus_no_communication`
- `injector_correction_issue`

---

# Example Case

## PSA / DW12 / 4HS

### Issue

Intermittent turbo underboost with:

- P023E
- P0299
- U1208

### Root Cause

Faulty OEM MAP sensor (1920LG).

### Key Diagnostic Insight

With engine OFF:

All pressure sensors should read approximately atmospheric pressure.

One sensor reported 424 mbar while the others reported approximately 1000 mbar.

The incorrect reading followed the sensor during swap testing, conclusively proving sensor failure.

### Important Lesson

Cheap aftermarket pressure sensors produced invalid calibration and caused engine start inhibition.

Only the genuine OEM sensor restored correct operation.

---

# Recommended Documentation Workflow

## 1. Record initial symptoms

Document:

- Intermittent or permanent behavior
- Engine load conditions
- Temperature conditions
- Driving conditions

---

## 2. Record all fault codes

Include:

- Active faults
- Pending faults
- Permanent faults
- Freeze-frame data

---

## 3. Capture live data

Always compare:

- Requested values
- Measured values
- Sensor coherence
- Voltage consistency

---

## 4. Validate physical plausibility

Example:

Engine OFF:

- All pressure sensors should equal atmospheric pressure.

If not:

- Sensor
- Wiring
- Reference voltage
- Ground

become primary suspects.

---

## 5. Perform controlled tests

Examples:

- Sensor swaps
- Connector tests
- Vacuum tests
- Smoke tests
- Oscilloscope analysis
- Resistance checks

---

## 6. Confirm repair

Always document:

- Final fix
- Post-repair live data
- Fault-free operation
- OEM vs aftermarket differences

---

# Supported Engine Families

## DV Series

- DV4
- DV5
- DV6

---

## DW Series

- DW8
- DW10
- DW12

---

## DT Series

- DT17
- DT20

---

# Goals of This Repository

- Build a long-term diagnostic knowledge base
- Preserve successful troubleshooting methodology
- Avoid unnecessary parts replacement
- Share real-world ECU behavior observations
- Improve root-cause analysis techniques
- Create reusable diagnostic workflows

---

# Recommended Future Additions

## ECU Families

- Bosch EDC15
- Bosch EDC16
- Bosch EDC17
- Siemens SID
- Delphi DCM
- Continental Diesel ECUs

---

## Diagnostic Topics

- Turbo systems
- DPF regeneration
- EGR systems
- CAN bus diagnostics
- LIN bus diagnostics
- Injector correction analysis
- Oscilloscope references
- Sensor validation methodology

---

# Contribution Philosophy

This repository prioritizes:

- Measured data over assumptions
- Root-cause analysis over part swapping
- Reproducible diagnostics
- OEM technical behavior understanding
- Real-world field repair information

---

# License

This repository is intended for educational and technical reference purposes.


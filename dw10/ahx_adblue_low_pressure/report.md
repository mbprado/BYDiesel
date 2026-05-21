# ---DRAFT--- DW10FD(AHX) – AD-blue low pressure error 

## Vehicle / Engine Information

- Engine: PSA / Ford DW10FD (AHX variant)
- Injection ECU:
- Turbo System: VGT diesel
- Transmission: AM6 automatic gearbox
- Diagnostic Tool: DiagBox
- Mileage: 244000 KM

---
# Previous disagnostics

The car was diagnosed for a complete ad-blue tank replacement.  

---
# Diagnostic tools

- ActiaXS in conjunction with Diagbox(PSA Oficcial scanner) was used to collect live data read, DTC, freeze frame and actuator tests.
- Analogic pressure gauge with hose
- Documentation could be accessed using Citroen Service Box and Parts-catalog.


---

# Initial Symptoms

The vehicle presented intermittent adblue alerts and mileage countdown for start denying:

- Sometimes the car worked perfectly normally, specially if it runs before reaching operation temperture
- It doen't affect car's performance.
- Prevents Start/Stop (echo)
- Faults stored in  ECU 

# Initial Fault Codes

## Engine ECU 

<img width="1581" height="693" alt="Screenshot 2026-05-21 at 15 48 14" src="https://github.com/user-attachments/assets/2cdf6b1f-c88f-4a60-9621-ba0fc46a9db6" />


### P20E8 00

> Defect in information emitted by engine ECU

Properties:

- Permanent fault
- Incorrect received value

Associated variables:

- Engine speed: 1635 rpm
- Gas pedal position: 30%
- Speed: 44Km/h
- Water temperature: 100°C
- ECU Voltage: 14.3V
- Adblue liquid pressure: 4.0 bar
- External temperature: 24C
- Adblue temperature (tank): 0
- Amount of injected Adblue: 0  

Interpretation:

The gearbox ECU was receiving inconsistent torque / engine information from the engine ECU.

At this stage, this was considered a secondary consequence rather than the primary failure.

---

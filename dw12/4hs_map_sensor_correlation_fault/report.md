# DW12BTED4 (4HS) Biturbo – MAP Sensor Fault Diagnosis Report

## Vehicle / Engine Information

- Engine: PSA / Ford DW12BTED4 (4HS variant)
- Injection ECU: Bosch EDC16CP39
- Turbo System: Sequential bi-turbo diesel
- Transmission: AM6 automatic gearbox
- Diagnostic Tool: DiagBox
- Mileage: 214000 KM

---
# Previous disagnostics

The car was diagnosed by previous professionals: a full turbo replacement required, considering the DTC pointing to turbo and obivious loss of boost.  
However with a deeper analisys, proper test and tools, this soon proved incorrect. 

---
# Diagnostic tools

- ActiaXS in conjunction with Diagbox(PSA Official scanner) was used to collect live data read, DTC, freeze frame and actuator tests.
- Documentation could be accessed using Citroen Service Box and Parts-catalog.


---

# Initial Symptoms

The vehicle presented intermittent turbo-related behavior:

- Sometimes the car worked perfectly normally
- Sometimes the engine had low power / turbo issues
- Intermittent turbo underboost behavior
- Faults stored in both engine ECU and gearbox ECU
- Constant Limb-home mode

One important observation from the beginning:

> The issue was intermittent.

This immediately raised suspicion that the issue might not be a catastrophic mechanical turbocharger failure.

A completely failed turbocharger rotor or destroyed turbo assembly would normally produce:

- Permanent lack of boost
- Constant low power
- Persistent smoke or oil consumption
- Continuous fault behavior

Instead, the vehicle alternated between normal and faulty operation.

---

# Initial Fault Codes

## Gearbox ECU (AM6)

<img width="1732" height="732" alt="Screenshot 2026-04-21 at 17 00 53" src="https://github.com/user-attachments/assets/635d9048-33e1-4346-86f0-ad3f4df1be7d" />

### U1208

> Defect in information emitted by engine ECU

Properties:

- Permanent fault
- Incorrect received value

Associated variables:

- Converter locked
- Gear engaged: 4th
- Gearbox oil temperature: 83°C
- Battery voltage: 14.10V
- Input speed: 2352 rpm
- Output speed: 2035 rpm
- Engine speed: 2350 rpm

Interpretation:

The gearbox ECU was receiving inconsistent torque / engine information from the engine ECU.

At this stage, this was considered a secondary consequence rather than the primary failure.

---

## Engine ECU (EDC16CP39)

<img width="1936" height="799" alt="Screenshot 2026-04-21 at 16 50 53" src="https://github.com/user-attachments/assets/5f69aeda-898f-4b8e-87ff-67804d11f567" />

### P023E

> Turbo pressure signal correlation fault

Properties:

- Permanent fault
- Correlation fault between the 3 pressure sensors

Associated values:

- Atmospheric pressure voltage: 1.93V
- Turbo pressure voltage: 0.98V
- Engine speed: 771 rpm

Interpretation:

The ECU continuously compares multiple pressure sensors:

- Atmospheric pressure sensor
- Intake manifold pressure sensor (MAP)
- Turbo pressure sensor

The ECU detected that one of the pressure signals was physically inconsistent with the others.

This became the first major clue.

---

### P0299

> Turbo pressure regulation – pressure below requested value

Properties:

- Permanent fault
- Turbo pressure lower than requested

Associated values:

- Turbo pressure voltage: 0.98V
- Engine speed: 2121 rpm
- Turbo pressure reference: 1952 mbar

Interpretation:

The ECU was requesting boost pressure but measured pressure did not match expected values.

At this stage, possible causes included:

- Faulty MAP / boost pressure sensor
- Wiring issue
- Vacuum control problem
- Turbo actuator problem
- Mechanical turbocharger issue

---

# Initial Diagnostic Reasoning

The following reasoning was established early:

## Why mechanical turbo failure was considered less likely

The problem was intermittent.

A mechanically destroyed turbocharger normally produces constant symptoms.

Examples:

- Broken shaft
- Failed compressor wheel
- Seized turbo

These failures do not usually disappear intermittently.

Therefore, attention shifted toward:

- Sensor inconsistency
- Turbo control logic
- Wiring
- Vacuum regulation

---

# Understanding the DW12BTED4 Biturbo System

The DW12BTED4 engine uses a sequential biturbo setup:

- Small turbo for low RPM response
- Larger turbo for higher RPM operation
- Multiple vacuum actuators
- Multiple pressure sensors
- Complex ECU pressure correlation logic

Because of this architecture:

> Incorrect sensor data can create severe turbo-related behavior even when the turbochargers themselves are mechanically healthy.

---

# Pressure Sensor Investigation

## Initial hypothesis

The pressure correlation fault (P023E) strongly suggested:

- One pressure sensor was reading incorrectly
- Or one pressure sensor circuit had wiring issues

---

# Engine OFF Diagnostic Strategy

A key diagnostic strategy was established:

## With ignition ON and engine OFF:

All pressure sensors should read approximately atmospheric pressure.

Expected:

- Atmospheric pressure ≈ 1000 mbar
- MAP pressure ≈ 1000 mbar
- Turbo pressure ≈ 1000 mbar

Because:

- Engine not running
- No boost generated
- Entire intake system is at ambient atmospheric pressure

This became the critical diagnostic test.

---

# Live Data Investigation (Engine OFF)

The following measurements were collected.

## Air Circuit Information
<img width="2042" height="1154" alt="Screenshot 2026-04-22 at 15 45 44" src="https://github.com/user-attachments/assets/d4b0ce5f-7413-4206-8198-2378028551a9" />


Values observed:

- Engine speed: 0 rpm
- Measured air flow: 0 mg/stroke
- Calculated air information: 514 mg/stroke
- EGR requested position: 100%
- EGR actual position: 0%

Interpretation:

Although not definitive by themselves, these inconsistencies reinforced suspicion that the ECU was receiving invalid air-pressure-related information.

---

# Critical Pressure Measurements (Engine OFF)

<img width="2045" height="1148" alt="Screenshot 2026-04-22 at 15 46 53" src="https://github.com/user-attachments/assets/fe086676-b817-4ead-9fe6-f6c6350fee32" />

## Values obtained

- Atmospheric pressure: 1000 mbar
- Turbo pressure indexing: 988 mbar
- Turbo2 measured pressure: 1000 mbar
- Turbo measured pressure: 424 mbar

---

# Critical Discovery

This was the decisive moment in the diagnosis.

With the engine OFF:

- Three sensors agreed with atmospheric pressure
- One sensor reported only 424 mbar

This is physically impossible.

Therefore:

> One pressure sensor was definitively faulty or producing invalid output.

This fully explained:

- P023E (sensor correlation fault)
- P0299 (underboost)
- Intermittent turbo behavior
- Gearbox U1208 secondary fault

---

# Sensor Identification

Two pressure sensors were identified in PSA ServiceBox documentation.

## Sensor references

### 1920LG

Location:

- Intake manifold
- Mounted vertically near EGR / intake housing

Function:

- MAP sensor
- Intake manifold pressure reference

---

### 1920LH

Location:

- Charge pipe / intercooler piping

Function:

- Turbo pressure monitoring

---

# Physical Sensor Identification
<img width="844" height="719" alt="image" src="https://github.com/user-attachments/assets/6ef338da-a088-44a0-afdc-5823ffba79e0" />

The engine bay was inspected.

The intake manifold MAP sensor (1920LG) was visually identified:

- Located above the oil dipstick
- Mounted vertically into intake manifold
- Positioned near EGR and throttle housing

The second pressure sensor (1920LH) was identified as the boost pressure sensor mounted on charge piping.

---

# Sensor Swap Test

A controlled sensor swap test was performed.

## Initial state

- Sensor in intake manifold (1920LG) showed incorrect low pressure
- Sensor in boost pipe (1920LH) showed normal atmospheric pressure

---

## Procedure

The two sensors were swapped between positions.

---

## Result

After swapping:

> The incorrect reading followed the sensor.

This proved conclusively:

- Wiring was NOT the issue
- ECU was NOT the issue
- Turbochargers were NOT the issue
- The sensor itself was faulty

The defective component was:

> 1920LG MAP sensor

---

# Aftermarket Sensor Test

An aftermarket replacement sensor was initially installed.

## Result

The replacement produced:

- Incorrect pressure reading of approximately 1447 mbar at atmospheric conditions
- ECU interpreted this as runaway diesel / uncontrolled boost condition
- Engine starting was inhibited for safety reasons

This demonstrated:

- The ECU is extremely sensitive to pressure sensor calibration
- Cheap aftermarket sensors may not have correct scaling or calibration curves

---

# OEM Sensor Installation
<img width="700" height="525" alt="e9e8ac8f13b2e631c078715039484430" src="https://github.com/user-attachments/assets/9a408798-34ae-4863-b2b8-18cb0900aebb" />

A genuine original sensor was then ordered and installed.

Although significantly more expensive (approximately 3x the price of aftermarket), installation immediately resolved the issue.

---

# Final Results

After installing the genuine OEM sensor:

- Both turbo pressure sensors showed coherent readings
- Atmospheric pressure values matched correctly
- Pressure correlation faults disappeared
- All fault codes were cleared successfully
- Engine operated normally
- Turbo system function restored completely
- No further underboost symptoms
- No additional gearbox communication faults

---

# Final Diagnosis

## Root Cause

Faulty intake manifold MAP sensor (1920LG).

The sensor intermittently produced incorrect pressure readings.

This caused:

- Pressure correlation mismatch
- Incorrect turbo control calculations
- False underboost detection
- Secondary gearbox torque information faults

---

# Key Lessons Learned

## 1. Engine OFF pressure comparison is extremely valuable

On turbo diesel systems:

- All pressure sensors should match atmospheric pressure with engine OFF.

This simple test quickly identified the faulty signal.

---

## 2. Intermittent turbo faults are not always turbocharger failures

Intermittent behavior strongly suggested:

- Sensor issue
- Wiring issue
- Control issue

rather than catastrophic mechanical turbo damage. Replacing the turbocharger in this case wouldn't solve the problem.

---

## 3. OEM sensors matter on PSA diesel systems

The aftermarket sensor produced invalid scaling and dangerous behavior.

Using the genuine sensor immediately resolved the issue.

---

## 4. P023E correlation faults should not be ignored

This fault was the most important diagnostic clue.

It clearly indicated:

> The ECU did not trust one of the pressure signals.

---

# Final Outcome

Vehicle fully repaired.

No turbocharger replacement required.

No vacuum system repair required.

No wiring repair required.

Final repair consisted solely of replacing the defective OEM MAP sensor (1920LG).

---

# Reference Fault Codes

| Fault Code | Description | Final Interpretation |
|---|---|---|
| P023E | Pressure sensor correlation fault | Faulty MAP sensor signal |
| P0299 | Turbo underboost | Incorrect boost calculation caused by MAP sensor |
| U1208 | Incorrect engine information to gearbox ECU | Secondary consequence of invalid engine torque calculation |

---

# Final Technical Conclusion

The entire turbo-related failure chain originated from a single defective pressure sensor.

The faulty MAP sensor intermittently reported incorrect intake pressure values, causing:

1. Pressure sensor correlation failure
2. Incorrect ECU boost calculations
3. False underboost detection
4. Torque model inconsistencies
5. Secondary gearbox communication faults

Replacing the sensor with a genuine OEM component restored normal operation immediately.


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

> Reductant Pressure Too Low

Properties:

- Permanent fault
- Reductant Pressure Too Low

Associated variables:

- Engine speed: 1635 rpm
- Gas pedal position: 30%
- Speed: 44Km/h
- Water temperature: 100°C
- ECU Voltage: 14.3V
- Adblue liquid pressure: 4.0 bar
- External temperature: 24°C
- Adblue temperature (tank): 0°C
- Amount of injected Adblue: 0  

Interpretation:

The adblue pump shoud pressurise the system.  
The pressuse shows 4 bar however, this is the minimum value the calculator sets. The real pressure is probably zero.  
Another curious observation is the adblue temperature. 0°C is surelly a bad reading.

At this stage, possible causes included:
- Fuse
- Cabling
- Pump
- Pressure sensor
- adblue controller board

---
# Initial Diagnostic Reasoning

The following reasoning was established early:

## Internal adblue tank controller components are the main suspects.

Removing the tank  from the support end letting the car reach 100°C, there was no sound of pump working

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

# Understanding the AdBlue (SCR) System on Citroën DW10 Diesel Engines

Modern Citroën diesel vehicles using the DW10 family engines commonly use an SCR (Selective Catalytic Reduction) system with AdBlue to reduce NOx emissions.

The system is tightly monitored by the ECU and uses multiple sensors and pressure checks to verify correct operation.

Because of this:

> A fault in the AdBlue delivery system can trigger engine warnings, power limitation, restart countdowns, or “Emissions Fault” messages even when the engine itself is mechanically healthy.

---

## How the AdBlue System Works

### Main Components

Typical PSA/Citroën SCR systems contain:

- AdBlue tank
- Integrated pump module
- Pressure regulator
- Internal filters
- Heater elements
- Injector (dosing valve)
- NOx sensors
- Temperature sensors
- SCR catalyst
- ECU monitoring logic

The system stores AdBlue (32.5% urea solution) and injects a controlled amount into the exhaust stream.

Inside the hot exhaust:

- AdBlue decomposes into ammonia
- Ammonia reacts inside the SCR catalyst
- NOx emissions are converted into nitrogen and water vapor

---

## Pressure Generation Inside the System

The AdBlue pump module pressurizes the reductant line before injection occurs.

Typical operation:

1. ECU wakes the SCR system
2. Pump builds pressure in the reductant circuit
3. Pressure sensor confirms target pressure
4. Injector dosing begins
5. ECU continuously monitors pressure stability

If the ECU cannot achieve or maintain the expected pressure:

- Injection is stopped
- SCR efficiency drops
- Faults are stored
- Restart inhibition countdown may begin

---

## What “Reductant Pressure Too Low” Means

This fault means:

> The SCR system failed to reach or maintain the required AdBlue pressure requested by the ECU.

The ECU compares:

- Requested pressure
- Measured pressure
- Pump current consumption
- Pressure decay behavior
- Injection response

If the measured pressure stays below specification for too long, the ECU logs a pressure-related fault.

---

## Reliable Causes of “Reductant Pressure Too Low”

### 1. Weak or Failed AdBlue Pump

One of the most common causes.

The internal electric pump may:

- Wear out
- Seize
- Lose output pressure
- Fail intermittently when hot

Result:

- Pressure builds too slowly
- Pressure never reaches target
- ECU detects insufficient reductant pressure

---

### 2. Crystallized AdBlue Deposits

AdBlue crystallizes when exposed to air or after leaks.

Crystals can block:

- Internal filters
- Pump passages
- Injector lines
- Dosing injector

Result:

- Restricted flow
- Unstable pressure
- Pressure drop during injection

This is extremely common on PSA systems.

---

### 3. Internal Tank Module Failure

Many Citroën/PSA vehicles use an integrated tank assembly where:

- Pump
- Pressure sensor
- Heater
- Electronics
- Filters

are combined into a single module.

Failures inside the module can cause:

- Incorrect pressure readings
- Inability to regulate pressure
- Intermittent operation

In many cases PSA service procedures replace the entire tank assembly.

---

### 4. Pressure Sensor Fault

The ECU depends heavily on pressure correlation logic.

A faulty pressure sensor may report:

- Pressure lower than actual
- Slow pressure response
- Implausible readings

Result:

- ECU believes pressure is insufficient
- SCR system enters fault mode

Even if the pump is functioning mechanically.

---

### 5. Air Leaks in the Reductant Circuit

Leaks in hoses, connectors, or injector fittings can prevent pressure retention.

Symptoms may include:

- Pressure builds briefly then drops
- Frequent pump cycling
- Pressure decay faults

Crystallized white residue around fittings is a common clue.

---

### 6. Frozen AdBlue / Heater Problems

AdBlue freezes around -11°C.

SCR systems include heaters in:

- Tank
- Lines
- Pump module

If heaters fail in cold weather:

- Fluid cannot circulate correctly
- Pressure generation becomes impossible

The ECU may then log low pressure faults.

---

### 7. Electrical Supply or Wiring Problems

Low voltage or damaged wiring can affect:

- Pump speed
- Sensor readings
- Heater operation

Common causes include:

- Corroded connectors
- Water ingress
- Harness damage near the tank

---

## Important Diagnostic Considerations

On PSA/Citroën systems:

> “Reductant Pressure Too Low” does NOT automatically mean the injector is clogged or the pump is completely dead.

The ECU validates multiple correlated values.

A fault can originate from:

- Sensor inaccuracies
- Pressure instability
- Flow restrictions
- Electrical faults
- Internal module logic problems

---

## Common Symptoms Seen Together

Vehicles may show:

- “Engine Fault: Repair Needed”
- “Emissions Fault”
- UREA warning
- Check engine light
- Reduced power
- Engine restart countdown
- Impossible engine restart after countdown reaches zero

---

# Practical Diagnostic Approach

Reliable diagnosis usually includes:

1. Reading manufacturer-level fault codes
2. Monitoring live reductant pressure
3. Checking pump activation
4. Inspecting for crystallization
5. Verifying electrical supply
6. Checking pressure retention after shutdown
7. Inspecting injector and lines for leaks

---

# Live Data Investigation (Engine at operational temperature)

The following measurements were collected.


## DeNOx Circuit information:

<img width="1594" height="670" alt="Screenshot 2026-05-21 at 12 15 07" src="https://github.com/user-attachments/assets/19cdb8fa-0866-47a4-8d3d-cd6079305ad5" />

## Observed Values

- Engine speed: 821 rpm
- Water temperature: 100°C
- Heating pipe percentage: 0%
- AdBlue pressure: 4.00 bar *(sensor minimum display value)*
- AdBlue reductant status: Stopped/empty
- Thermal aging: 28%
- SCR catalyst temperature: 240°C
- Amount to be injected: 0 mg/s
- System flush state: Idle
- AdBlue inside catalyst: 0 g

---

## System Interpretation

### Engine State

#### Engine Speed: 821 rpm

The engine is operating at idle speed.

No abnormality is implied from this value alone.


### Coolant Temperature: 100°C

The engine is fully warmed up.

This confirms:

- Normal operating temperature
- SCR activation conditions are possible
- The ECU is no longer in cold-start mode


## AdBlue Heating System

### Heating Pipe Percentage: 0%

This generally indicates:

- The ECU does not currently require AdBlue heating
- Fluid temperature is already above freezing threshold

This is normal under warm conditions.


## SCR Catalyst Temperature

### SCR Catalyst Temperature: 240°C

This temperature is now inside the normal operational range where SCR dosing should typically occur.

At approximately 240°C:

- The catalyst is active
- NOx reduction efficiency becomes effective
- The ECU would normally be capable of commanding AdBlue injection

This makes the following values much more important diagnostically:

- Injection quantity
- Reductant status
- Pressure behavior


## AdBlue Pressure

### Measured Pressure: 4.00 bar

Important characteristic of this system:

> The diagnostic sensor display has a lower reporting limit of 4 bar.

This means:

- Any real pressure between 0 and 4 bar will still appear as 4.00 bar
- 4.00 bar does **not** confirm adequate pressure
- Actual pressure may effectively be near zero

This is extremely important for interpretation.


## Reductant Status

### "Stopped/empty"

At 240°C catalyst temperature, this status becomes more suspicious.

Because the SCR system is now within normal dosing temperature range:

> The ECU would normally be expected to enter active dosing operation under suitable load conditions.

Possible interpretations include:

- SCR dosing disabled by fault logic
- Pressure not reaching operational threshold
- System unable to prime correctly
- ECU inhibiting injection due to pressure plausibility failure

The wording "empty" still does not necessarily mean the tank itself is empty.

On PSA systems, it may also indicate:

- No active metering state
- Dosing interruption
- Injection disabled condition


## Injection Quantity

### Amount to be Injected: 0 mg/s

At idle, 0 mg/s can still occasionally occur.

However:

- With fully warm coolant
- Active catalyst temperature
- Normal running condition

the ECU would generally be expected to request dosing during loaded driving conditions.

If this value remains permanently at 0 mg/s even during acceleration or road load:

> That strongly suggests the SCR system is inhibited.

## AdBlue Stored Inside Catalyst

### 0 g

This indicates:

- No ammonia loading currently calculated
- No recent dosing activity detected

Combined with:

- 240°C catalyst temperature
- Possible ineffective pressure
- "Stopped/empty" status

this supports the possibility that injection is not occurring at all.


## System Flush State

### Idle

Normal state.

The system is not currently:

- Priming
- Purging
- Cleaning
- Performing shutdown flush

## Thermal Aging: 28%

Indicates moderate catalyst aging.

Not considered severe.

This value alone would not normally disable SCR operation.

---

# Overall Interpretation

## Most Likely Interpretation

These values suggest:

- The SCR system is thermally ready to operate
- But injection appears inactive
- Pressure reading may be misleading due to 4 bar minimum display limit
- Actual reductant pressure may be insufficient for dosing

This combination is consistent with:

- Weak pump output
- Failed pressure generation
- Pressure sensor interpretation limits
- Internal tank module failure
- Restricted reductant flow

## Important Diagnostic Observation

Because the pressure display cannot show below 4 bar:

> A displayed value of 4.00 bar cannot be trusted as proof of correct pressure.

The real system pressure may still be:

- Extremely low
- Unstable
- Insufficient for injection

This can easily produce:

- "Reductant Pressure Too Low"
- Injection inhibition
- Permanent 0 mg/s dosing

even while diagnostics misleadingly display 4.00 bar.

---

# What Confirmed the Fault

The strongest confirmation is:

## During loaded driving:

- Injection request remains at 0 mg/s
- Pressure never rises above 4 bar
- Reductant status remains stopped
- SCR faults return repeatedly

That would strongly support:

- Pump/module failure
- Pressure generation failure
- Internal reductant circuit restriction
- Pressure sensor missreading

rather than a temperature-related inhibition.

---

# Removing the tank and identifying the components

<img width="1598" height="1307" alt="image" src="https://github.com/user-attachments/assets/80320938-a316-4bb4-af04-a0e663b7d112" />

<img width="4032" height="3024" alt="IMG_2829" src="https://github.com/user-attachments/assets/6387a445-d64a-4322-916f-8206c514edce" />







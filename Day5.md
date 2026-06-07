# Substation Concepts and Internship Notes

## Feeder vs Incomer

One of the most important concepts in a substation is understanding the difference between an **incomer** and a **feeder**.

### Incomer

An incomer is a circuit that **brings power into a busbar**.

#### Example

```text
110 kV Grid
     ↓
Power Transformer
     ↓
33 kV Busbar
```

The transformer-side breaker connected to the 33 kV bus is called the **incomer breaker** because power is entering the busbar.

### Feeder

A feeder is a circuit that **takes power from the busbar to the load or another substation**.

#### Example

```text
33 kV Busbar
   ├── Feeder 1 → Town A
   ├── Feeder 2 → Town B
   └── Feeder 3 → Industry
```

These outgoing circuits are called **feeders**.

### Simple Rule

* Power entering the busbar → **Incomer**
* Power leaving the busbar → **Feeder**

---

# Numerical Relay vs Auxiliary Relay vs Master Trip Relay

## Numerical Protection Relay

A numerical relay is the **brain of the protection system**.

### Functions

* Measures current and voltage from CTs and PTs
* Detects faults
* Makes trip decisions
* Records fault data and events

### Examples

* ABB Relion Series
* Siemens SIPROTEC
* GE Multilin

### Types

* Overcurrent Relay
* Differential Relay
* Distance Relay

---

## Auxiliary Relay

An auxiliary relay does **not detect faults directly**.

### Functions

* Signal multiplication
* Interlocking
* Alarm operation
* Logic implementation

### Operation

```text
Protection Relay
       ↓
Auxiliary Relay
       ↓
Trip Circuit
```

---

## Master Trip Relay

A master trip relay is a special type of auxiliary relay.

### Functions

* Receives trip commands from protection relays
* Trips all required breakers simultaneously
* Provides lockout functionality

### Example

```text
Transformer Differential Relay
          ↓
Master Trip Relay (86)
          ↓
HV Breaker Trip
LV Breaker Trip
Alarm
Lockout
```

In severe transformer faults, the master trip relay trips both HV and LV breakers.

---

# Auto Reclosing

Auto reclosing is used because many transmission line faults are temporary.

## Common Temporary Faults

* Bird contact
* Lightning
* Tree branch contact
* Flashover

## Working Principle

```text
Fault Occurs
      ↓
Breaker Trips
      ↓
Preset Time Delay
      ↓
Breaker Closes Automatically
      ↓
Fault Cleared? → Supply Restored
Fault Persists? → Breaker Trips Permanently
```

This process is known as **auto reclosing**.

---

## Example: Kunnamkulam and Malaparamba

### Observations

* Fault occurred on a 220 kV line
* Malaparamba experienced a trip
* Kunnamkulam had auto-reclose enabled

### Possible Sequence

```text
Fault on Line
      ↓
Both Ends Detect Fault
      ↓
Breakers Trip
      ↓
Auto Reclose Operates
      ↓
Fault Clears
      ↓
Line Restored
```

This is common in EHV transmission systems.

---

# Earth Truck / Feeder Earthing Truck

An earthing truck is used for safely grounding a feeder during maintenance.

## Procedure

```text
Open Breaker
      ↓
Open Isolator
      ↓
Insert Earthing Truck
      ↓
Feeder Safely Grounded
```

## Protection Provided

* Induced voltage protection
* Accidental energization protection
* Back-feed protection

---

# Trivector Meter

A trivector meter measures:

1. Active Energy (kWh)
2. Reactive Energy (kVARh)
3. Apparent Energy (kVAh)

Hence the name **Tri-vector Meter**.

## Applications

* Energy accounting
* Billing
* Substation metering

---

# BDV (Breakdown Voltage) of Transformer Oil

The "DB value" discussed in substations usually refers to **BDV (Breakdown Voltage)**.

Transformer oil is tested using a **BDV Tester**.

## Healthy Oil

* High breakdown voltage
* Good insulation strength

## Poor Oil

* Moisture contamination
* Dirt contamination
* Ageing effects

## Typical BDV Values

| BDV Value   | Condition          |
| ----------- | ------------------ |
| Above 60 kV | Excellent          |
| 40–60 kV    | Acceptable         |
| Below 40 kV | Requires treatment |

---

# One-and-Half Breaker Scheme

Widely used in 220 kV and higher voltage substations.

## Arrangement

```text
CB1 ---- Circuit 1 ---- CB2 ---- Circuit 2 ---- CB3
```

Three breakers protect two circuits.

## Advantages

* High reliability
* Maintenance without interruption
* Breaker failure does not disconnect both circuits

## Disadvantages

* High installation cost
* Complex protection and control

---

# Why Different Breakers Are Used

## 11 kV and 33 kV Systems

### VCB (Vacuum Circuit Breaker)

#### Advantages

* Simple construction
* Low maintenance
* No SF₆ gas handling
* Suitable for medium-voltage applications

---

## 110 kV and Above

### SF₆ Circuit Breakers

### GIS Breakers

#### Advantages

* Excellent arc extinction
* Suitable for high fault currents
* Compact design
* High reliability

---

# Equipment and Systems Observed During Internship

During the substation internship, exposure was gained to:

## Power Equipment

* Power Transformers
* Auto Transformers
* Circuit Breakers
* Isolators
* Busbars
* Current Transformers (CT)
* Potential Transformers (PT)
* Lightning Arresters

## Protection Systems

* Numerical Relays
* Auxiliary Relays
* Master Trip Relays
* Auto Reclosing Systems
* Differential Protection

## GIS and Switchyard Systems

* GIS (Gas Insulated Switchgear)
* AIS (Air Insulated Switchgear)
* Busbar Arrangements
* One-and-Half Breaker Schemes

## Metering and Monitoring

* Trivector Meters
* Bay Control Units (BCU)
* SCADA Systems
* Substation Automation Systems (SAS)

## Maintenance and Testing

* Megger Testing
* Cable Fault Finding
* Transformer Oil BDV Testing
* Thermal Imaging

## Safety Systems

* Fire Protection Systems
* Deluge Valve Systems
* Earthing Systems
* Earthing Trucks
* Battery Banks
* PPE and Safety Equipment

```

This document serves as a concise reference for important substation concepts observed during practical training and internship activities.
```

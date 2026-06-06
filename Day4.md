# KSEB 220 kV Substation Internship - Day 4 Log
**Location:** Control & Relay Panel (CRP) Room  
**Focus Areas:** Substation Metering, Auxiliary Systems, Protection Relays, and Real-World Teleprotection Troubleshooting.

---

## 📋 Morning Session: Substation Theory & Core Systems

### 1. Efficiency and Losses in Power Equipment
Electrical equipment efficiency is calculated using the standard formula:

$$\eta = \left( \frac{\text{Output Power}}{\text{Input Power}} \right) \times 100$$

#### Transformer Losses
* **Core (Iron) Losses:** Occur continuously in the magnetic core.
    * *Hysteresis Loss:* Caused by repeated magnetic reversal; minimized by using high-permeability silicon steel.
    * *Eddy Current Loss:* Caused by induced circulating currents; minimized by using laminated core sheets.
* **Copper (Winding) Losses:** Variable losses occurring in conductors due to winding resistance. Represented by the formula:
    $$P_{cu} = I^2R$$

#### Typical Equipment Efficiencies
| Equipment | Typical Efficiency | Notes |
| :--- | :--- | :--- |
| **Power Transformer** | 98.0% – 99.5% | Highly efficient; minimal moving parts |
| **Generator** | ~97.0% | Notes indicate a mere 3% loss profile |
| **Induction Motor** | 80.0% – 95.0% | Losses due to friction and windage |
| **Industrial/Ceiling Fan**| ~80.0% | Dominated by mechanical & winding resistance |
| **Automobile Engine** | 30.0% – 50.0% | Heavy thermal energy dissipation |

---

### 2. Hydro Turbine Classification
Hydro turbines are selected based on the available water head (height) and discharge volume:
* **Pelton Wheel:** High Head | Low Flow Rate (Impulse turbine)
* **Francis Turbine:** Medium Head | Medium Flow Rate (Reaction turbine; most common)
* **Kaplan Turbine:** Low Head | High Flow Rate (Propeller-type reaction turbine)

> 💡 **Quick Memory Rule:** > * *Pelton* $\rightarrow$ High Head
> * *Francis* $\rightarrow$ Medium Head
> * *Kaplan* $\rightarrow$ Low Head

---

### 3. Current Transformers (CT) & Metering Infrastructure
In a 220 kV environment, currents are too massive for direct instrumentation. Current Transformers scale down these values to standard safe thresholds (typically 1A or 5A).

#### CT Ratio Example (400/200/5A)
* **Primary Rating:** 400A or 200A (selectable via tap changing).
* **Secondary Rating:** 5A.
* **Application:** If the primary line carries 400A, the CT secondary outputs 5A to feed the Ammeter, Energy Meter, Protection Relays, and SCADA transducers.

#### Types of Energy Meters
* **Mechanical / Electromechanical:** Older induction disc type meters.
* **Static Meter:** Solid-state electronic meters with high accuracy.
* **TOD (Time of Day) Meter:** Records power consumption based on specific time zones to implement differential tariff rates.
* **Bidirectional Meter:** Measures both *Import* (drawn from grid) and *Export* (fed into grid) energy; vital for solar integrations.
* **Smart Meter:** Equipped with real-time automated remote communication, load monitoring, and anti-tamper capabilities.

---

### 4. Power Factor, Maximum Demand & TOD Tariff

#### Energy Metrics
* **kWh (Active Energy):** The actual useful work done by the system.
* **kVAh (Apparent Energy):** Total energy supplied, including reactive components ($kVAh \ge kWh$).
* **kVArh (Reactive Energy):** Energy circulating due to inductive or capacitive loads.
* **Target:** Maintain a power factor close to unity ($kVAh \approx kWh$). If the power factor drops due to inductive lag, $kVAh > kWh$, triggering utility penalties.

#### Maximum Demand (MD)
* Calculated based on a **15-minute integration window**.
* The meter continuously records the average load over 15 minutes. The highest recorded average during the month sets the billed Maximum Demand peak.

#### KSEB Time of Day (TOD) Zones
* **06:00 to 18:00 (Day):** Normal Tariff
* **18:00 to 21:00 (Peak):** Premium/Higher Tariff (Heavy system load)
* **21:00 to 06:00 (Night):** Discounted/Lower Tariff (Off-peak system load)

#### Multiplication Factor (MF)
Because meters operate on scaled down secondary values from CTs and PTs, the raw register reading must be multiplied by the overall system ratio to find actual consumption:
$$\text{Multiplication Factor (MF)} = \text{CT Ratio (CTR)} \times \text{PT Ratio (PTR)}$$

---

### 5. Control & Protection Room Architecture
* **SCADA Room:** Main server and human-machine interface (HMI) for real-time data acquisition and remote operation.
* **C&R Panel Room (Control & Relay):** Contains the protective relays, disturbance recorders, and control switches.
* **BCU Room:** Houses Bay Control Units that handle interlocking, position status monitoring, and localized control commands for each physical bay.

#### Standard Feeder Bay Layout (e.g., Bay 201)
$$\text{Incoming Line} \longrightarrow \text{Lightning Arrester (LA)} \longrightarrow \text{PT/CVT} \longrightarrow \text{CT} \longrightarrow \text{Isolator} \longrightarrow \text{Circuit Breaker (CB)} \longrightarrow \text{Busbar}$$

---

### 6. Substation DC Auxiliary Systems
Substations rely completely on independent battery systems because protection relays and circuit breaker trip coils must clear faults even during an absolute AC blackouts.

* **48V DC System:** Primarily powers communication couplers, fiber optic terminal equipment (FODP), and teleprotection links.
* **110V DC System:** Powers critical protection relay logic, breaker trip coils, and close circuits. Driven by a 55-cell battery bank backed by independent chargers and a DC Distribution Board (DCDB).

---

### 7. Core Protection & Fire Auxiliaries
* **Master Trip Relay (86 Relay):** A high-speed, multi-contact lockout relay. When a fault occurs, it trips the breaker and locks out closing circuits until it is manually inspected and reset.
* **Test Block:** Allows safe secondary current/voltage injection testing without disconnecting permanent panel wiring.
* **Fire Hydrant Pump Array:** Consists of a **Jockey Pump** (runs continuously to maintain pipeline standby pressure), a **Main Electric Pump** (starts automatically during low pressure caused by fire), and a **Diesel Engine Standby Pump** (activates if station power fails).

---

## 🔍 Afternoon Session: Real-World Case Study
### Incident Report: 220 kV Teleprotection Line Inter-trip Failure Investigation

### 1. Incident Overview
A system fault occurred on the **220 kV transmission line** connecting the **Madakkathara** and **Kunnamkulam** substations. 
* **Status at Madakkathara:** Fault successfully detected; localized breaker tripped.
* **Status at Kunnamkulam:** The corresponding line breaker **failed to trip automatically**, causing an asymmetrical line condition until backup protection stepped in.
* **Investigation Location:** Kunnamkulam C&R Panel Room.
* **Personnel Present:** Executive Engineers, Senior Protection Officers, and OEM Relay Specialists.

### 2. Relay Architecture & Redundancy
Because this is a critical 220 kV EHV (Extra High Voltage) transmission line, full protection redundancy is maintained using two independent numerical platforms:
1.  **Main 1 Protection (M1 Relay):** MiCOM Numerical Platform.
2.  **Main 2 Protection (M2 Relay):** Secondary independent numerical platform.

> 📝 **Key Discovery:** The M1 and M2 relays utilize completely **different internal protection logics** and communication pathways. This design prevents a shared firmware bug or common fiber path failure from disabling both systems simultaneously.

### 3. Engineering Diagnostics & Troubleshooting
The onsite investigation focused on the **M1 Relay Line Communication Interface**, as the local M2 system verified healthy parameters.

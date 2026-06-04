# Substation Power System Protection: Comprehensive Lecture Notes

A practical, substation-oriented guide to power system protection, mapping real-world equipment (based on KSEB 110kV Substation practices) to the KTU Power System Protection syllabus.

---

## Master Structure of the Class

The lecture covers transmission line protection, terminal equipment, communication links, and transformer protection in a logical sequence:

1. **Introduction:** Why Protection is Needed & Transmission Line Faults
2. **Line Protection:** Distance Protection, Overcurrent, & Earth Fault Protection (SEF)
3. **Instrument Transformers:** CT and PT/CVT Operations
4. **Substation Communication:** PLCC and OPGW Technologies
5. **Equipment Protection:** Transformer Protections (Buchholz, REF, Differential, Overcurrent)
6. **Auxiliary Systems:** Transformer Oil Monitoring, Cooling Systems, and Yard Equipment

---

## 1. Why Protection is Needed & Transmission Line Faults

A power system normally carries balanced load currents. However, abnormal conditions or insulation breakdowns lead to faults.

### Common Fault Types
* **Line-to-Ground (L-G) Fault:** A single-phase conductor touches the earth or a grounded structure.
* **Line-to-Line (L-L) Fault:** Two phase conductors come into physical contact with each other.
* **Three-Phase (3-$\phi$) Fault:** All three phases short-circuit together (most severe, least common).
* **Equipment Fault:** Internal insulation failure inside transformers, CTs, CVTs, or circuit breakers.

### Consequences of Uncleared Faults
If high fault currents are not cleared instantaneously by protection systems, they cause catastrophic failure:
* Conductors melt or burn out.
* Power transformers suffer severe thermal and mechanical damage.
* Circuit breakers can explode due to excessive interrupting stress.
* The entire electrical grid can lose synchronism, causing a total grid blackout.

---

## 2. Core Protection Philosophy: Distance vs. Differential

In a transmission substation, **Distance Protection** and **Differential Protection** are the two primary protection pillars. They protect completely different assets using distinct engineering principles.

| Feature | Distance Protection | Differential Protection |
| :--- | :--- | :--- |
| **Primary Asset Protected** | Long Transmission Lines (66kV, 110kV, 220kV, 400kV) | Localized Equipment (Transformers, Busbars, Generators) |
| **Operating Principle** | Impedance measurement ($Z = \frac{V}{I}$) | Current balance ($\sum I_{in} = \sum I_{out}$) |
| **Required Inputs** | Current (from CT) & Voltage (from PT/CVT) | Currents only (from CTs on all boundaries) |
| **Protection Zones** | Stepped Zones (Zone 1, 2, 3, 4) with time delays | Strictly fixed zone bounded by CT locations |
| **Speed** | Instantaneous for Zone 1; delayed for backup zones | Exceptionally fast / Instantaneous for internal faults |

---

## 3. Distance Protection (Transmission Lines)

### Operating Principle
Distance relays measure the ratio of voltage to current to determine line impedance ($Z$):

$$Z = \frac{V}{I}$$

Where:
* $V$ = Voltage input from the Capacitive Voltage Transformer (CVT)
* $I$ = Current input from the Current Transformer (CT)

Because a transmission line's resistance and reactance are uniformly distributed along its length, **Impedance is directly proportional to line length**. 

* **Higher Impedance Measured:** Fault is far away.
* **Lower Impedance Measured:** Fault is close to the substation.

> **Example:** If a 110 kV feeder length is 100 km and a fault occurs at 40 km, the relay measures the exact impedance equivalent of that 40 km stretch and sends an instantaneous trip signal.

### Types of Distance Relays

#### 1. Impedance Relay
* Measures the absolute value of impedance ($Z$).
* **Characteristics:** Circular characteristic centered at the origin on the R-X plane.
* **Limitations:** Non-directional by itself; highly affected by power swings and fault arc resistance.

#### 2. Reactance Relay
* Measures only the quadrature component ($X = Z \sin\theta$).
* **Characteristics:** Straight line parallel to the R-axis on the R-X plane.
* **Advantages:** Immune to fault arc resistance. Widely used for **Ground Fault Protection**.

#### 3. Mho Relay (Admittance Relay)
* Inherently directional relay.
* **Characteristics:** Circular characteristic passing through the origin on the R-X plane.
* **Advantages:** Highly stable during power swings; does not require an additional directional element.
* **Application:** Standard choice for EHV transmission line protection (110kV, 220kV, 400kV).

### Distance Protection Zones

Distance relays use stepped time-delay zones to provide both primary protection for their own line and backup protection for adjacent lines.


```

Substation A                                 Substation B                  Substation C
|=============================================|=============================|
[========== Zone 1: 80% (Instantaneous) ======]
[==================== Zone 2: 120% (0.3 - 0.5s) ============]
[=========================================== Zone 3: Remote Backup (1.0s) ==>

```

* **Zone 1:** Covers **80% to 90%** of the protected line. It trips **instantaneously** (no intentional time delay) to prevent tripping on faults beyond the remote busbar due to CT/CVT errors.
* **Zone 2:** Covers the remaining **10% to 20%** of the line plus roughly **20% to 50%** of the shortest adjacent line. Time delay: **0.3 to 0.5 seconds**.
* **Zone 3:** Provides remote backup for the entire adjacent line. Time delay: **1.0 second**.
* **Zone 4:** Extended reverse or long forward backup used in specific complex network configurations. Time delay: **1.5 to 2.0 seconds**.

---

## 4. Differential Protection (Equipment)

### Operating Principle
Differential protection operates on the concept of **Kirchhoff's Current Law (KCL)**. Under normal operating or external fault conditions (through-faults), the current entering the equipment equals the current leaving it.

$$I_{in} = I_{out} \implies I_{diff} = I_{in} - I_{out} = 0$$

If an internal fault occurs, current flows into the fault from both sides, causing a mismatch:

$$I_{in} \neq I_{out} \implies I_{diff} > 0 \implies \text{Trip}$$

### Types of Differential Protection

#### 1. Simple Current Differential Protection
* Compares absolute secondary currents directly.
* Mainly used for short lines, feeders, or localized generator windings.

#### 2. Percentage (Biased) Differential Protection
* To prevent false tripping caused by CT saturation during heavy external through-faults or tap-changer operations, a **restraining coil** is added.
* The relay trips only when the differential operating current exceeds a set percentage of the average restraining current:

$$I_{operating} > K \cdot I_{restraint}$$

* Standard practice for protecting **Power Transformers**.

#### 3. Busbar Differential Protection
* Monitors an entire busbar zone by summation of all incoming and outgoing currents ($\sum I = 0$).
* If a mismatch occurs, it clears the entire busbar by tripping every circuit breaker connected to that node.

#### 4. Transformer Differential Protection
* Specifically compensates for transformer phase shifts (e.g., Delta-to-Wye transformations) and mismatched CT transformation ratios using internal numerical vector matching.
* Provides rapid, high-speed clearing for winding short-circuits and inter-turn faults.

---

## 5. Other Line Protection Schemes

### Overcurrent Protection
* **Principle:** Monitors line current. If current exceeds a predetermined pickup setting, it trips the circuit breaker.
* **Setting Example:** Line rated for 400A $\rightarrow$ Relay pickup set at 500A $\rightarrow$ Fault current reaches 3000A $\rightarrow$ Instantly trips.

### Sensitive Earth Fault (SEF) Protection
* **Why it is needed:** High-resistance earth faults (e.g., a conductor falling on dry soil or branches) draw very low fault currents that normal overcurrent relays miss.
* **Operation:** Monitors the residual algebraic vector sum of the three-phase currents:

$$I_{residual} = I_R + I_Y + I_B$$

* In a healthy system, $I_{residual} \approx 0$. When a tiny ground leak occurs, the balance breaks, and the highly sensitive SEF relay trips the system.

---

## 6. Instrument Transformers

Relays cannot directly interface with high-voltage (110kV+) or high-current (1000A+) grids. Instrument transformers safely step down these values.

* **Current Transformer (CT):** Converts high primary current into a standardized low secondary current (typically **1A** or **5A**).
    * *Example:* $1000\text{ A} \rightarrow 1\text{ A}$.
* **Capacitive Voltage Transformer (CVT):** Used in Extra High Voltage (EHV) yards to step down high voltages down to a safe **110V** level for metering, protection relays, and synchronizing units. It also acts as a coupling device for communication signals.
    * *Example:* $110\text{ kV} \rightarrow 110\text{ V}$.

---

## 7. Substation Communication Networks

Protective relays at opposite ends of a transmission line must talk to each other instantaneously to execute teleprotection (e.g., Permissive Underreach/Overreach Tripping).

### Power Line Carrier Communication (PLCC)
* **Concept:** Uses the existing high-voltage copper/aluminum transmission conductors to transmit high-frequency voice and data signals.
* **Frequencies:** Power grid operates at **50 Hz**, while PLCC signals are injected at high frequencies between **50 kHz and 500 kHz**.
* **Key Components:**
    * **Wave Trap (Line Trap):** A large parallel inductor/capacitor coil connected in series with the line. It acts as a low-pass filter: lets 50 Hz power pass through to the substation but blocks ($50\text{ kHz} - 500\text{ kHz}$) communication signals from escaping into the yard.
    * **Coupling Capacitor (CVT):** Connects the communication terminal to the high-voltage line, letting high frequencies pass into the line while blocking the 50 Hz power frequency.
    * **Line Matching Unit (LMU):** Matches the impedance of the underground coaxial cable to the overhead transmission line for maximum signal power transfer.

### Optical Ground Wire (OPGW)
* **Concept:** Modern replacement for PLCC. It replaces the traditional steel shield wire at the absolute top of the transmission tower with a composite wire containing an optical fiber core.
* **Dual Functionality:** Serves as a lightning shield wire while offering high-speed, high-bandwidth fiber-optic data channels.
* **Advantages over PLCC:** Zero electromagnetic interference, massive bandwidth capacity, ultra-low latency, and absolute immunity to line noise.

---

## 8. Comprehensive Transformer Protection Suite

A complete Substation Transformer Protection Panel includes electrical, mechanical, and thermal protection schemes:


```

```
                              [Conservator Tank]
                                      |
                                (Buchholz Relay) <--- Gas & Oil Surge
                                      |
[HV Side CT] --->===============[Power Transformer]===============[LV Side CT] <--- [Differential / REF]
                                 |    |    |    |
                                [Oil / Winding Temp] <--- Thermal Monitoring

```

```

### 1. Restricted Earth Fault (REF) Protection
* **Purpose:** Standard differential relays lack the sensitivity to detect earth faults occurring close to the transformer's neutral grounding point. 
* **Operation:** Composed of a highly sensitive unit that compares the neutral CT current against the summation of the phase CT currents.
* **Zone:** Strictly restricted to the transformer winding zone itself.

### 2. Buchholz Relay
* **Placement:** Installed in the pipe connecting the main transformer tank to the conservator tank.
* **Operation:** Detects internal slow/fast mechanical faults.
    * *Minor Fault (Incipient Fault):* Internal insulation breakdown causes local sparking, decomposing the transformer oil into gas. The gas rises, accumulates in the Buchholz chamber, and drops an internal float to trigger an **Alarm**.
    * *Severe Fault (Short Circuit):* A massive internal arc creates a violent shockwave of oil moving toward the conservator. This operates a mechanical flap that instantly triggers a **Trip** command to clear the transformer.

### 3. Transformer Oil & Thermal Monitoring
Transformer oil provides vital dielectric insulation and cooling. Temperature Indicators track thermal stress:
* **Top Oil Temperature Indicator (OTI)**
* **Winding Temperature Indicator (WTI)**

#### Typical Temperature Control Stages:
* **60°C:** Cooling Fans Activate (**ONAF** stage)
* **80°C:** Forced Oil Pumps Activate (**ODAF** stage)
* **90°C:** High-Temperature **Alarm**
* **95°C:** High-Temperature **Trip** (Breaker opens to protect insulation)

### 4. Cooling Methods Matrix
* **ONAN (Oil Natural, Air Natural):** Passive design. Oil circulates internally via natural convection currents; heat dissipates via natural ambient air radiation along the radiator fins.
* **ONAF (Oil Natural, Air Forced):** External cooling fans are aimed at the radiator banks to speed up thermal transfer.
* **ODAF (Oil Directed, Air Forced):** Submerged axial pumps force hot oil through targeted winding channels while heavy fans cool the exterior radiators.

---

## 9. Switchyard Equipment

* **Circuit Breaker (CB):** The primary switching device capable of safely making, carrying, and breaking large fault currents under automated control.
* **Isolator (Disconnect Switch):** A mechanical knife switch used to isolate equipment for maintenance. **Must only be operated under no-load conditions** (after the circuit breaker is opened).
* **Ground Switch (GS):** Safely connects de-energized, isolated lines directly to the earth grid to discharge trapped capacitive charges before maintenance crews begin work.
* **Lightning Arrester (LA):** Installed at line entry points and transformer terminals. It acts as a non-linear resistor: offers high impedance to normal grid voltage, but breaks down to near-zero impedance during high-voltage lightning surges, safely diverting the surge to earth.

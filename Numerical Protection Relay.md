# Numerical Protection Relay and Protection Functions – Study Notes

## 1. What is a Numerical Protection Relay?

A **Numerical Protection Relay** is a specialized high-speed industrial computer used in modern substations to detect electrical faults and protect power system equipment.

### Working Principle

1. Receives voltage and current signals from:

   * Current Transformers (CTs)
   * Potential/Voltage Transformers (PTs or CVTs)

2. Converts analog signals into digital data using an ADC (Analog-to-Digital Converter).

3. Continuously processes the data using mathematical algorithms.

4. Detects abnormal conditions such as:

   * Short circuits
   * Earth faults
   * Overloads
   * Equipment failures

5. Sends a trip command to the circuit breaker within a few milliseconds.

### Advantages

* High speed operation
* Accurate fault detection
* Event recording capability
* Self-diagnostics
* Communication with SCADA systems
* Reduced wiring using fiber-optic communication

---

# 2. IEC 61850 Communication Protocol

### What is IEC 61850?

IEC 61850 is the international communication standard used in modern digital substations.

It enables intelligent electronic devices (IEDs), relays, and SCADA systems to communicate using fiber-optic networks.

### Benefits

* Faster communication
* Less copper wiring
* Better reliability
* Easy integration of devices
* Remote monitoring and control

---

# 3. GOOSE Messaging

### Full Form

**GOOSE = Generic Object Oriented Substation Events**

### Purpose

Used for ultra-fast transmission of protection signals between relays and breakers.

### Examples

* Trip commands
* Breaker failure signals
* Interlocking signals
* Transformer protection commands

### Characteristics

* Peer-to-peer communication
* No central controller required
* Extremely fast operation

### Communication Time

Typically:

**Less than 3–4 ms**

### What to Check

On relay software or HMI:

* GOOSE communication status
* GOOSE message logs
* Communication latency
* Message counters
* Error status

---

# 4. MMS Communication

### Full Form

**Manufacturing Message Specification (MMS)**

### Purpose

Used for slower supervisory communication between relays and SCADA systems.

### Data Transferred

* Current measurements
* Voltage measurements
* Breaker status
* Alarm information
* Event records

### Characteristics

* Client-server communication
* Slower than GOOSE
* Suitable for monitoring

---

# 5. Fiber Link Monitoring

Modern substations use fiber-optic cables instead of extensive copper wiring.

### What to Check

* Green communication LEDs
* Network health status
* Communication diagnostics

### Communication Failure

If the fiber link fails:

* Relay generates an alarm.
* HMI displays:

  * Communication Failure
  * Fiber Link Down
  * Network Alarm

---

# 6. Distance Protection (ANSI 21)

Distance protection is mainly used for:

* Transmission lines
* Long overhead lines
* High voltage interconnections

Example:

* 220 kV transmission lines entering a substation

---

## Principle of Distance Protection

Distance relay calculates the line impedance.

### Formula

Z=\frac{V}{I}

Where:

* Z = Impedance
* V = Voltage
* I = Current

---

### Why It Works

Impedance is proportional to line length.

When a fault occurs:

* Voltage decreases.
* Current increases.
* Calculated impedance decreases.

The relay estimates the fault distance based on this impedance.

---

# 7. Distance Protection Zones

To avoid unnecessary tripping, the transmission line is divided into zones.

---

## Zone 1

### Coverage

* 80% of protected line

### Time Delay

* 0 ms (instantaneous)

### Purpose

Primary protection for most faults on the line.

---

## Zone 2

### Coverage

* Remaining 20% of protected line
* Part of the next line section

### Time Delay

* 300–400 ms

### Purpose

Backup protection.

Allows downstream relays time to clear faults first.

---

## Zone 3

### Coverage

* Remote backup protection

### Time Delay

* 800–1000 ms

### Purpose

Backup for neighboring transmission lines.

---

# 8. Fault Locator Function

Modern numerical relays can determine the exact fault location.

### Example

Relay Display:

* Phase R–Earth Fault
* Fault Distance = 14.2 km

### Benefits

* Faster maintenance
* Reduced outage time
* Easy fault identification

---

# 9. Differential Protection (ANSI 87)

Differential protection is used for expensive equipment such as:

* Power transformers
* Generators
* Busbars
* Reactors

It provides extremely fast internal fault protection.

---

# 10. Principle of Differential Protection

Based on **Kirchhoff's Current Law (KCL)**.

### KCL Statement

Total current entering a system equals total current leaving it.

### Mathematical Form

I_{in}-I_{out}=0

Under healthy conditions:

Incoming current = Outgoing current

Therefore:

Differential current = 0

---

# 11. Transformer Differential Protection

CTs are installed on:

* High Voltage side (220 kV)
* Low Voltage side (110 kV / 33 kV)

The relay continuously compares both currents after proper scaling.

---

## Differential Current

The relay calculates:

I_{diff}=I_{in}-I_{out}

---

### Normal Condition

Incoming current = Outgoing current

Result:

[
I_{diff}=0
]

No trip signal.

---

### Internal Fault Condition

Examples:

* Winding short circuit
* Insulation failure
* Turn-to-turn fault
* Phase-to-phase fault

Current balance is disturbed.

Result:

[
I_{diff}>0
]

Relay detects the abnormal difference and trips immediately.

---

# 12. Differential Relay Trip Logic

### Step 1

Fault occurs inside transformer.

### Step 2

Current entering transformer becomes different from current leaving transformer.

### Step 3

Relay calculates differential current.

### Step 4

Differential current exceeds preset threshold.

### Step 5

Relay issues trip command.

### Step 6

Circuit breakers open.

### Step 7

Transformer is isolated before severe damage occurs.

---

# 13. What to Check on Relay Software

## IEC 61850 Checks

* GOOSE communication status
* MMS communication status
* Fiber link health
* Communication alarms

---

## Distance Protection Checks

* Zone 1 settings
* Zone 2 settings
* Zone 3 settings
* Reach settings
* Time delays
* Fault locator records

---

## Differential Protection Checks

* CT ratios
* HV current values
* LV current values
* Differential current (Idiff)
* Bias current
* Pickup settings
* Trip records

---

# Quick Exam Revision

### Numerical Relay

A microprocessor-based protection device that converts analog voltage/current signals into digital data and uses algorithms to detect faults and trip breakers.

### IEC 61850

Digital communication standard for substations.

### GOOSE

Ultra-fast protection messaging (< 4 ms).

### MMS

Monitoring and SCADA communication.

### Distance Protection (ANSI 21)

Uses:

Z=\frac{V}{I}

to locate transmission line faults.

### Distance Protection Zones

* Zone 1 → 80%, Instantaneous
* Zone 2 → 120%, 300–400 ms
* Zone 3 → Backup, 800–1000 ms

### Differential Protection (ANSI 87)

Based on Kirchhoff's Current Law.

Healthy Condition:

I_{in}=I_{out}

Fault Condition:

I_{diff}>0

### Main Purpose

**Detect faults quickly and isolate equipment before damage occurs, ensuring safe and reliable operation of the power system.**

# Power Transformers and Substation Auxiliary Systems

## Power Transformers

Power transformers are the most critical components in a substation. Their primary function is to step down voltage from transmission levels (e.g., 220 kV) to lower distribution levels (e.g., 110 kV or 33 kV). Due to the large power transfer involved, transformers generate significant heat and require dedicated cooling, protection, and monitoring systems for safe operation.

---

## Transformer Cooling System

### Cooling Fans

Transformer windings are immersed in insulating oil, which absorbs the heat generated during operation. The heated oil circulates through external radiators, where electrically driven cooling fans force air across the radiator surfaces to remove heat and maintain safe operating temperatures.

### Oil Conservator

The oil conservator is a cylindrical reservoir mounted above the transformer tank. Since transformer oil expands and contracts with temperature variations, the conservator provides space for these volume changes while preventing direct exposure of the main oil tank to atmospheric air.

### Silica Gel Breather

As oil levels change inside the conservator, air enters and exits the system. Moisture present in the air can reduce the insulating strength of transformer oil.

**Function:**

* Removes moisture from incoming air.
* Protects transformer insulation from contamination.

**Silica Gel Condition Indicators:**

* **Blue:** Dry and active.
* **Pink:** Moisture-saturated and requires replacement or regeneration.

---

## Transformer Protection Devices

### Buchholz Relay

The Buchholz relay is installed in the pipe connecting the main transformer tank and the conservator. It detects internal faults by monitoring gas formation inside the transformer oil.

**Operation:**

* **Minor fault:** Small gas accumulation → Alarm signal.
* **Major fault:** Large gas surge → Trips the circuit breaker and isolates the transformer.

**Purpose:**

* Early fault detection.
* Prevention of severe transformer damage.

---

# Instrument Transformers

Standard measuring instruments and protection relays cannot directly handle high-voltage and high-current transmission systems. Instrument transformers reduce these values to safe and standardized levels.

## Current Transformer (CT)

A Current Transformer (CT) is connected in series with the power line and reduces high line currents to standard values for measurement and protection.

**Typical Secondary Ratings:**

* 1 A
* 5 A

**Applications:**

* Ammeters
* Energy meters
* Protection relays

## Potential Transformer (PT) / Voltage Transformer (VT)

A Potential Transformer (PT) or Voltage Transformer (VT) is connected in parallel with the power system and reduces high voltages to standardized levels.

**Typical Secondary Voltage:**

* 110 V

**Applications:**

* Voltmeters
* Protection relays
* Monitoring systems

---

# Switching Operations and Safety

Proper switching procedures are essential to prevent equipment damage, dangerous arcing, and safety hazards.

## Interlocking Logic

Interlocking systems (mechanical, electrical, or digital) ensure that switching operations follow the correct sequence and prevent unsafe actions.

### Golden Rule

> Never operate an isolator while current is flowing through it.

**Important:**
The circuit breaker must always make or break current before any isolator operation.

---

## Line Disconnection (Opening Sequence)

1. Open the **Circuit Breaker (CB)** to interrupt current flow.
2. Open the **Isolators** on both sides of the equipment.
3. Close the **Earth Switch** to discharge any residual voltage safely.

---

## Line Energization (Closing Sequence)

1. Open the **Earth Switch**.
2. Close the **Isolators**.
3. Close the **Circuit Breaker (CB)**.

**Benefits of Interlocking Systems:**

* Prevent incorrect switching sequences.
* Improve equipment protection.
* Enhance personnel safety.

---

# DC Supply System

Protection and control systems must continue operating even during AC supply failures. For this reason, substations maintain dedicated DC power systems.

## Battery Banks

Battery banks provide uninterrupted DC power for critical substation operations.

**Common Battery Types:**

* Lead-Acid Batteries
* Nickel-Cadmium (Ni-Cd) Batteries

**Typical DC Voltages:**

* 110 V DC
* 220 V DC

**Powered Equipment:**

* Protection relays
* Control circuits
* Circuit breaker trip mechanisms
* Communication systems

---

## Battery Chargers

During normal operation, battery chargers:

* Convert AC power to DC.
* Supply control and protection circuits.
* Keep battery banks fully charged.

If the AC supply fails, batteries immediately take over without interruption, ensuring continuous operation of protection and control systems.

---

# Surge Protection System

Lightning strikes and switching operations can create high-voltage surges capable of damaging expensive substation equipment.

## Lightning Arrestors (Surge Arrestors)

Lightning arrestors are installed at transmission line entry points and near critical equipment such as transformers.

### Working Principle

#### Normal Operating Conditions

* The arrestor presents very high resistance.
* Current follows the normal power path.

#### During a Surge

* Internal zinc oxide elements become highly conductive.
* Surge current is diverted directly to the earthing system.
* Sensitive equipment is protected from overvoltage stress.

### Benefits

* Protects transformers and switchgear from insulation failure.
* Reduces equipment damage caused by lightning and switching surges.
* Improves overall substation reliability and safety.

---

## Quick Revision Summary

| Component                     | Main Function                                  |
| ----------------------------- | ---------------------------------------------- |
| Power Transformer             | Steps down transmission voltage                |
| Cooling Fans                  | Remove heat from transformer oil               |
| Oil Conservator               | Accommodates oil expansion and contraction     |
| Buchholz Relay                | Detects internal transformer faults            |
| Silica Gel Breather           | Removes moisture from incoming air             |
| Current Transformer (CT)      | Reduces current for measurement and protection |
| Potential Transformer (PT/VT) | Reduces voltage for measurement and protection |
| Circuit Breaker (CB)          | Makes and breaks load/fault current            |
| Isolator                      | Provides visible isolation after CB operation  |
| Earth Switch                  | Grounds isolated equipment safely              |
| Battery Bank                  | Provides backup DC power                       |
| Battery Charger               | Charges batteries and supplies DC loads        |
| Lightning Arrestor            | Protects equipment from surge voltages         |

### Power Transformers

Power transformers are the core components of a substation, responsible for stepping down voltage from transmission levels (e.g., **220 kV**) to distribution levels (e.g., **110 kV** or **33 kV**). Due to the large amount of power they handle, transformers generate significant heat and require several auxiliary systems for cooling, protection, and reliable operation.

#### Cooling Fans

Transformers are filled with insulating oil that absorbs heat from the windings. The heated oil circulates through external radiator fins, where large electric fans blow air across the radiators to cool the oil and maintain safe operating temperatures.

#### Oil Conservator

The oil conservator is a cylindrical tank mounted above the transformer. As transformer oil expands and contracts with temperature changes, the conservator provides additional space for the oil volume to vary without exposing the main tank to atmospheric air.

#### Buchholz Relay

The Buchholz relay is a protective device installed in the pipe connecting the main transformer tank and the conservator. Internal faults such as short circuits cause the oil to decompose and generate gas. The relay detects these gas accumulations:

* Small gas accumulation → Alarm signal
* Large gas surge → Trips the circuit breaker and disconnects the transformer

This helps prevent severe damage or transformer failure.

#### Silica Gel Breather

When the oil level in the conservator changes, air enters and leaves the conservator. Moisture in the air can reduce the insulating properties of transformer oil. A silica gel breather removes moisture from the incoming air.

* Dry silica gel: **Blue**
* Moisture-saturated silica gel: **Pink**

The silica gel must be replaced or regenerated when saturated.

---

## Instrument Transformers

Standard measuring instruments and protective relays cannot directly handle high transmission voltages and currents. Instrument transformers reduce these values to safe and standardized levels for measurement and protection purposes.

### Current Transformer (CT)

Current Transformers are connected in series with the power line. They reduce large line currents to standard values (typically **1 A** or **5 A**) for use by ammeters, energy meters, and protection relays.

### Potential Transformer (PT) / Voltage Transformer (VT)

Potential Transformers are connected in parallel with the power system. They step down high voltages to a standard value (typically **110 V**) for safe measurement and monitoring by voltmeters and protection devices.

---

## Switching Sequences

Safe substation operation requires switching equipment in a specific sequence to prevent dangerous arcing and equipment damage.

### Interlocking Logic

Interlocking systems (mechanical or digital) prevent operators from performing unsafe switching operations by enforcing the correct operating sequence.

### Golden Rule

**Never operate an isolator while current is flowing through it.**

The circuit breaker must always interrupt or establish current before any isolator operation.

### Line Disconnection (Opening Sequence)

1. Open the **Circuit Breaker (CB)** to interrupt current flow.
2. Open the **Isolators** on both sides of the equipment.
3. Close the **Earth Switch** to safely discharge any residual voltage.

### Line Energization (Closing Sequence)

1. Open the **Earth Switch**.
2. Close the **Isolators**.
3. Close the **Circuit Breaker (CB)**.

Interlocking systems prevent incorrect operation sequences and enhance personnel safety.

---

## DC Supply System

Protection and control systems must remain operational even if the main AC supply fails due to a fault.

### Battery Banks

Substations maintain dedicated battery banks, typically using lead-acid or nickel-cadmium cells, to provide reliable DC power.

Typical DC supply voltages:

* **110 V DC**
* **220 V DC**

These batteries power:

* Protection relays
* Control circuits
* Circuit breaker tripping mechanisms
* Communication systems

### Battery Chargers

During normal operation, battery chargers:

1. Convert AC power to DC.
2. Supply control and protection equipment.
3. Keep batteries fully charged.

If the AC supply fails, the batteries instantly take over without interruption, ensuring continuous protection system operation.

---

## Surge Protection

Lightning strikes and switching operations can generate high-voltage surges that may damage expensive substation equipment.

### Lightning Arrestors (Surge Arrestors)

Lightning arrestors are installed at the entry points of transmission lines before major equipment such as transformers.

#### Working Principle

**Under Normal Conditions**

* The arrestor offers very high resistance.
* Current continues through the normal power path.

**During a Surge**

* The arrestor's internal zinc oxide elements rapidly become conductive.
* The surge current is diverted directly to the earthing system.
* Sensitive equipment is protected from overvoltage damage.

By providing a low-resistance path to ground during surges, lightning arrestors safeguard transformers and other critical substation components from insulation failure and catastrophic damage.

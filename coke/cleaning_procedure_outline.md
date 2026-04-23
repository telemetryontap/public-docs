# Cleaning Procedure Outline

This document describes the automated cleaning cycle as currently configured. The entire procedure runs automatically from start to finish with **no pauses for human interaction between phases**. Once started, the system will proceed through all three phases without stopping.

---

## Equipment Involved

### Product Lines Cleaned

The following product lines are cleaned during the procedure. Each line is cleaned individually, one at a time:

1. **Half & Half** (Source 0)
2. **Alternative Milk** (Source 1)
3. **Coconut Water** (Source 2)

All other product lines (sodas, syrups, water, etc.) are excluded from the cleaning cycle.

### Cleaning Supply Solenoids

Two solenoids provide cleaning fluids. Both activate together alongside each product line during every phase:

- **Cleaning Solenoid 1** — Cleaner supply (Port: OUT_FLAVOR_PUMP_19)
- **Cleaning Solenoid 2** — Cleaning water supply (Port: OUT_FLAVOR_PUMP_20)

---

## Cleaning Cycle Sequence

### Phase 1: Flush (approx. 30 seconds total)

**Purpose:** Push cleaning solution through each product line at full pressure.

The system cleans one product line at a time. For each line:

1. Open both cleaning solenoids (cleaner + water)
2. Run the product line pump at **full speed (100%)**
3. Hold for **10 seconds**
4. Stop the pump and close both cleaning solenoids
5. Move to the next product line

With 3 product lines cleaned one at a time, this phase takes approximately **30 seconds** (10 seconds per line).

---

### Phase 2: Soak (30 seconds)

**Purpose:** Allow the cleaning solution to sit in the lines for chemical action.

- All pumps and solenoids are **off** during this phase
- No fluid is moving — the cleaning solution sits in the lines
- Duration: **30 seconds**

> **Note:** There is no pause or prompt between Flush and Soak. The system moves directly into the Soak phase as soon as Flush completes.

---

### Phase 3: Purge (approx. 30 seconds total)

**Purpose:** Push remaining cleaning solution and residue out of each product line at reduced pressure.

The system again cleans one product line at a time. For each line:

1. Open both cleaning solenoids (cleaner + water)
2. Run the product line pump at **half speed (50%)**
3. Hold for **10 seconds**
4. Stop the pump and close both cleaning solenoids
5. Move to the next product line

With 3 product lines cleaned one at a time, this phase takes approximately **30 seconds** (10 seconds per line).

> **Note:** There is no pause or prompt between Soak and Purge. The system moves directly into the Purge phase as soon as Soak completes.

---

## Total Estimated Duration

| Phase  | Duration per Line | Lines | Phase Total |
|--------|-------------------|-------|-------------|
| Flush  | 10 seconds        | 3     | 30 seconds  |
| Soak   | —                 | —     | 30 seconds  |
| Purge  | 10 seconds        | 3     | 30 seconds  |
| **Total** |                |       | **~90 seconds** |

---

## Configurable Parameters

The following timing values can be adjusted through the system interface:

| Parameter       | Current Value | Allowed Range    |
|-----------------|---------------|------------------|
| Flush duration  | 10 seconds    | 5–20 seconds     |
| Soak duration   | 30 seconds    | 0–300 seconds    |
| Purge duration  | 10 seconds    | 5–30 seconds     |

---

## Key Notes

- The cleaning cycle runs **fully automated** with no operator interaction required between phases.
- Both cleaning solenoids (cleaner and water) activate **together** for every product line during both Flush and Purge.
- Product line pumps run at **100% during Flush** and **50% during Purge**.
- Only 3 of the 23 product sources participate in the cleaning cycle. The remaining sources are excluded.

# Wiring and GPIO Mapping (Pico W)

## Scope
This document explains hardware interconnections for the Pico W project using:
- 4x4 matrix keypad
- 12 LED outputs

## Assumptions and Limits
Only a wiring **image** was provided, not the raw `diagram.json`. Therefore:
- Component types are reliable.
- Exact GPIO numbers are inferred from visible traces and may be off by pin index.
- You should replace/confirm the table below using the final `diagram.json` netlist.

## Functional Signal Groups

### 1) Keypad (8 lines)
A 4x4 matrix keypad usually exposes:
- 4 row lines (`R1..R4`)
- 4 column lines (`C1..C4`)

Typical MicroPython scanning model:
- Configure rows as outputs, columns as inputs with pull-up/down.
- Drive one row active at a time and read columns.

### 2) LED Panel (12 lines)
The panel appears to map one GPIO per LED channel:
- `LED_1..LED_8` (blue)
- `LED_A..LED_D` (red)

Each LED must include a current-limiting resistor in series.

## Proposed Logical Mapping Table
Use this as a clean software abstraction regardless of physical pin numbers.

| Function | Label | Direction | Notes |
|---|---|---|---|
| Keypad row | KP_R1 | Output | Matrix scan row 1 |
| Keypad row | KP_R2 | Output | Matrix scan row 2 |
| Keypad row | KP_R3 | Output | Matrix scan row 3 |
| Keypad row | KP_R4 | Output | Matrix scan row 4 |
| Keypad column | KP_C1 | Input | Use pull-up/down consistent with hardware |
| Keypad column | KP_C2 | Input | Use pull-up/down consistent with hardware |
| Keypad column | KP_C3 | Input | Use pull-up/down consistent with hardware |
| Keypad column | KP_C4 | Input | Use pull-up/down consistent with hardware |
| LED output | LED_1 | Output | Blue LED channel 1 |
| LED output | LED_2 | Output | Blue LED channel 2 |
| LED output | LED_3 | Output | Blue LED channel 3 |
| LED output | LED_4 | Output | Blue LED channel 4 |
| LED output | LED_5 | Output | Blue LED channel 5 |
| LED output | LED_6 | Output | Blue LED channel 6 |
| LED output | LED_7 | Output | Blue LED channel 7 |
| LED output | LED_8 | Output | Blue LED channel 8 |
| LED output | LED_A | Output | Red LED channel A |
| LED output | LED_B | Output | Red LED channel B |
| LED output | LED_C | Output | Red LED channel C |
| LED output | LED_D | Output | Red LED channel D |

## Pico W Pin Naming Guidance
Document physical mapping in one of these forms:
- **GPIO notation** (recommended in firmware): `GPIO0..GPIO28`
- **Header pin numbers** (for assembly): physical pin index on board header

When finalizing, publish a second table:

| Logical signal | GPIO | Physical pin | Net/trace source |
|---|---:|---:|---|
| KP_R1 | GPIOx | Piny | diagram.json net name |

## Electrical Notes
- GPIO max current limits apply; avoid sourcing too much current from one bank.
- Use sensible LED resistor values (220Ω–330Ω typical at 3.3V).
- Confirm keypad pull resistor orientation aligns with firmware input pull configuration.

## Wokwi Verification Steps
1. Recreate exact wiring from validated `diagram.json`.
2. Confirm each key press maps to expected symbol.
3. Validate each LED output channel independently.
4. Test simultaneous/rapid key presses and debounce behavior.

# Raspberry Pi Pico W Keypad + LED Panel Project

This repository is organized for a **Raspberry Pi Pico W (RP2040)** firmware project driven by a matrix keypad and a multi-LED output panel.

> **Important**: the original firmware source code was not included in the provided snippet (`# PASTE YOUR MICROPYTHON CODE HERE`).
> To respect the requirement **"do not change program behavior"**, this repository focuses on structure and documentation and does not alter runtime logic.

## Project Type
- **Target board**: Raspberry Pi Pico W
- **Assumed firmware stack**: **MicroPython** (based on provided code placeholder)
- **Simulation source**: Wokwi-style wiring diagram image

## Proposed Repository Structure (MicroPython)

```text
.
├── README.md
├── src/
│   └── main.py              # Place your original firmware logic here unchanged
├── lib/                     # Optional reusable MicroPython modules
└── docs/
    ├── architecture.md      # Code/module architecture and responsibilities
    └── wiring.md            # Hardware wiring and GPIO mapping
```

## Features (from provided hardware diagram)
- 4x4 matrix keypad input (keys `0-9`, `A-D`, `*`, `#`).
- 12 external LED outputs:
  - 8 blue LEDs labeled `1..8`
  - 4 red LEDs labeled `A..D`
- Series resistors on LED channels.
- Pull resistors present on keypad side (as shown in diagram).

## Hardware Components List
Based on the diagram, the project uses:
- 1 × Raspberry Pi Pico / Pico W board
- 1 × 4x4 matrix keypad (8-pin ribbon)
- 12 × LEDs (8 blue + 4 red)
- 12 × current-limiting resistors for LEDs (typically 220Ω–330Ω)
- 4 × resistors on keypad lines (likely pull-up or pull-down, typically 10kΩ)
- Hookup wires / breadboard interconnects

## GPIO Mapping
A full mapping with assumptions and validation notes is documented in:
- `docs/wiring.md`

Because only an image was provided (not `diagram.json`), pin mapping is inferred conservatively and must be validated against the real `diagram.json` before final deployment.

## Firmware Setup (MicroPython on Pico W)
1. Flash MicroPython UF2 for Pico W to the board.
2. Copy your original logic into `src/main.py` **without behavioral changes**.
3. If needed, add helper modules in `lib/`.
4. Upload files to Pico W root filesystem (typically as `/main.py` and optional `/lib/*`).

## Flashing / Upload Workflow
### Option A: Thonny
1. Connect Pico W via USB.
2. Select MicroPython (Raspberry Pi Pico).
3. Open `src/main.py`.
4. Save to device as `main.py`.

### Option B: mpremote
```bash
mpremote connect auto fs cp src/main.py :main.py
# Optional libraries:
# mpremote connect auto fs cp -r lib :lib
mpremote connect auto reset
```

## Run in Wokwi
1. Create/open a Pico W project in Wokwi.
2. Add the keypad and 12 LEDs (with resistors).
3. Reproduce wiring from `docs/wiring.md` (or import validated `diagram.json` once available).
4. Paste firmware into `main.py` in Wokwi.
5. Start simulation and test keypad-to-LED behavior.

## Run on Real Hardware
1. Build the exact same wiring (respecting resistor placement).
2. Confirm voltage domain is 3.3V logic.
3. Upload `main.py` to Pico W.
4. Open serial REPL for diagnostics if your firmware prints debug logs.

## Wi-Fi Notes (if firmware uses Wi-Fi)
Do not hardcode secrets in the repository.
- Recommended pattern:
  - `src/secrets.py` (excluded from VCS) with:
    - `WIFI_SSID = "..."`
    - `WIFI_PASSWORD = "..."`
- In code, import credentials safely and fail gracefully if file is missing.

You can add a tracked template file, e.g. `src/secrets.example.py`, without real credentials.

## Validation Checklist
- [ ] `src/main.py` matches original logic exactly.
- [ ] GPIO map checked against definitive `diagram.json`.
- [ ] LEDs never driven without current-limiting resistors.
- [ ] Keypad scan debounce timing validated on real hardware.
- [ ] Wi-Fi credentials excluded from git history.

# Firmware Architecture

## Goal
Keep original firmware behavior unchanged while documenting a maintainable structure for Pico W + MicroPython.

## Directory Layout

```text
src/
  main.py        # Original application entrypoint and control loop
lib/
  (optional)     # Reusable helpers (drivers, keypad scanner, led mapper, wifi helper)
docs/
  wiring.md
  architecture.md
```

## Module Responsibilities

### `src/main.py`
- Contains the existing business logic and state transitions.
- Handles initialization of GPIO resources.
- Runs the keypad scan loop and LED output updates.
- If used, triggers Wi-Fi setup and network behavior.

### Optional `lib/*` modules (future-safe, no logic changes required)
- `keypad.py`: matrix scan helper and key mapping constants.
- `led_panel.py`: symbolic LED channel control.
- `wifi_config.py`: safe credential loading wrapper.

> These are architectural recommendations only. Do not migrate code unless you can guarantee zero behavioral impact.

## Runtime Flow (Typical)
1. Boot Pico W and execute `main.py`.
2. Initialize keypad row/column pins.
3. Initialize LED output pins to safe default state.
4. Enter infinite loop:
   - scan keypad
   - decode pressed key
   - apply output behavior on LED channels
   - optional delay/debounce

## Non-Functional Considerations
- **Determinism**: keypad scanning interval should be fixed and predictable.
- **Safety**: default all LED lines to known state at startup.
- **Maintainability**: use symbolic names for GPIO and keys.
- **Security**: never commit real Wi-Fi credentials.

## Self-Critique and Improvement Pass

### First-pass documentation risk
- Risk: GPIO-level wiring may be inaccurate because `diagram.json` is not available.

### Improvement applied
- Added explicit assumptions and validation workflow in `docs/wiring.md`.
- Used logical-signal mapping decoupled from physical pins to avoid propagating uncertain values.

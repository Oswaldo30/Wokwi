# Firmware Architecture

## Runtime model
The firmware follows the standard Arduino-style execution pattern:
1. `setup()` initializes 12 LED GPIOs as outputs and sets all LOW.
2. `loop()` polls the keypad (`keypad.getKey()`), then applies key-to-LED actions.

## Main modules in `src/main.cpp`
- **Pin and matrix definitions**: `LEDS`, `ROWS`, `COLS`, `keys`, `ledPins`, `rowPins`, `colPins`.
- **Keypad driver instance**: `Keypad keypad = ...`.
- **Initialization**: `setup()` loops over every LED pin.
- **Behavior dispatch**: `switch (key)` maps each key to either:
  - single LED ON,
  - group ON (`9` and `*`),
  - group OFF (`0` and `#`).

## Functional behavior summary
- `1..8`: turns ON corresponding blue LED (latched ON).
- `9`: turns ON LEDs 1..8.
- `0`: turns OFF LEDs 1..8.
- `A..D`: turns ON corresponding red LED (latched ON).
- `*`: turns ON LEDs A..D.
- `#`: turns OFF LEDs A..D.

No auto-timeout/reset is implemented; state remains until another key changes it.

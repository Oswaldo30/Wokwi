# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico/Pico W project that reads a 4x4 membrane keypad and controls 12 LEDs using GPIO outputs.

> Core firmware behavior is preserved from the provided source. This repository focuses on structure and documentation.

## Repository Structure

- `src/main.cpp` - main firmware logic (Arduino-style C++)
- `include/` - reserved for headers
- `docs/wiring.md` - wiring and GPIO mapping
- `docs/architecture.md` - firmware structure and behavior
- `diagram.json` - Wokwi hardware diagram asset (placeholder/minimal snapshot)
- `CMakeLists.txt` - top-level build metadata/documentation target

## Features

- 4x4 keypad scanning via `Keypad` library
- Independent control of 12 LEDs
- Group actions:
  - `9` => ON for LEDs 1-8
  - `0` => OFF for LEDs 1-8
  - `*` => ON for LEDs A-D
  - `#` => OFF for LEDs A-D

## Components List

- 1x Raspberry Pi Pico / Pico W
- 1x 4x4 membrane keypad
- 12x LED (8 blue + 4 red)
- 12x 220 ohm resistors (LED current limiting)
- 4x 1k ohm resistors (keypad pull-up network)
- Jumper wires

## GPIO Pin Mapping

See full table in `docs/wiring.md`.

Quick map:
- Keypad rows: GP26, GP22, GP21, GP20
- Keypad cols: GP19, GP18, GP17, GP16
- LEDs: GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4, GP3, GP2, GP28, GP27

## Run in Wokwi

1. Create/open a Pico project in Wokwi.
2. Paste `src/main.cpp` into the firmware file expected by your template.
3. Load the full `diagram.json` from your original design input.
4. Start simulation and use the keypad.

## Run on Real Hardware (Pico W)

Because the firmware is written in Arduino-style C++ (`setup/loop`, `Keypad.h`), use one of these:

### Option A: Arduino-Pico core
1. Install Arduino IDE 2.x.
2. Install the RP2040 core (Earle Philhower Arduino-Pico).
3. Install `Keypad` library.
4. Select **Raspberry Pi Pico W** board.
5. Build and upload.

### Option B: Port to Pico SDK APIs
You can wrap/port this logic to native Pico SDK (`gpio_init`, etc.) while keeping behavior unchanged.

## Wi-Fi Notes

The current firmware does **not** use Wi-Fi, so no SSID/password configuration is required.
If Wi-Fi is added later, place credentials in a separate ignored config file (e.g., `secrets.h`) and never commit it.

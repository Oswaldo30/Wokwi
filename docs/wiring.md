# Wiring (Raspberry Pi Pico W)

## Overview
This project uses:
- 1x Raspberry Pi Pico / Pico W
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue for digits 1-8, 4 red for A-D)
- 12x 220 ohm resistors (series with LEDs)
- 4x 1k ohm resistors (row pull-up network to 3.3V)

## GPIO Mapping

### Keypad
| Keypad Pin | Pico GPIO | Purpose |
|---|---:|---|
| C1 | GP19 | Column input/output |
| C2 | GP18 | Column input/output |
| C3 | GP17 | Column input/output |
| C4 | GP16 | Column input/output |
| R1 | GP26 | Row input/output |
| R2 | GP22 | Row input/output |
| R3 | GP21 | Row input/output |
| R4 | GP20 | Row input/output |

### LED outputs
| Logical LED | Trigger Key | Pico GPIO |
|---|---|---:|
| LED1 | 1 | GP11 |
| LED2 | 2 | GP10 |
| LED3 | 3 | GP9 |
| LED4 | 4 | GP8 |
| LED5 | 5 | GP7 |
| LED6 | 6 | GP6 |
| LED7 | 7 | GP5 |
| LED8 | 8 | GP4 |
| LED9 | A | GP3 |
| LED10 | B | GP2 |
| LED11 | C | GP28 |
| LED12 | D | GP27 |

## Ground and power
- All LED cathodes connect to GND.
- Each LED anode connects to a dedicated GPIO through a 220 ohm resistor.
- The keypad row pull-up chain (4x 1k) is tied to 3V3, matching the supplied diagram.

## Notes and assumptions
- The supplied firmware and diagram are consistent for keypad and LED GPIO usage.
- The uploaded `diagram.json` in this repo is a minimal snapshot; in Wokwi, use the full connection list from the provided design prompt.

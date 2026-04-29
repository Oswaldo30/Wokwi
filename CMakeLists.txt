cmake_minimum_required(VERSION 3.13)

project(pico_keypad_led_controller C CXX ASM)

# This project is currently authored in Arduino-style C++ for Wokwi simulation.
# The firmware logic lives in src/main.cpp.
add_custom_target(firmware_sources ALL
  SOURCES src/main.cpp
)

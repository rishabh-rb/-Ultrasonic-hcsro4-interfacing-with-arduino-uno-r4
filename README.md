# Uno R4 WiFi Ultrasonic Sensor Project

## Overview
Simple Arduino project for the Renesas `uno_r4_wifi` board that reads distance from an ultrasonic sensor (e.g., HC-SR04) and prints values to the serial console. Main application is in `src/main.app` and configuration is in `platformio.ini`.

## Hardware
- Board: `uno_r4_wifi` (Renesas RA, 3.3V logic)
- Sensor: HC-SR04 (or compatible ultrasonic module)

Important: `uno_r4_wifi` uses 3.3V logic. Use a level shifter or a voltage divider on the sensor \`ECHO\` pin if the module is 5V.

## Wiring (example)
- `VCC` -> `5V` (or `3.3V` if your sensor supports it)
- `GND` -> `GND`
- `TRIG` -> digital pin `D2`
- `ECHO` -> digital pin `D3` (use level shifting to 3.3V)

Adjust pins in `src/main.app` if different pins are used.

## Files
- `platformio.ini` — Project configuration (environment: `uno_r4_wifi`, `monitor_speed` set to `9600`).
- `src/main.app` — Main application code that triggers the ultrasonic sensor and prints distances.

## Build and Upload
- Build:
  - `pio run -e uno_r4_wifi`
- Upload:
  - `pio run -e uno_r4_wifi -t upload`

If your board appears on a different port, update `upload_port` and `monitor_port` in `platformio.ini`.

## Serial Monitor
Open the serial monitor at 9600 baud:
- `pio device monitor -e uno_r4_wifi`
- Or specify port manually:
  - `pio device monitor -p /dev/cu.YOUR_PORT -b 9600`

## CLion Notes
Use CLion to edit files and the integrated terminal to run PlatformIO CLI commands. Optionally add External Tools or Run Configurations for common commands.

## Troubleshooting
- No serial port: list ports with `ls /dev/cu.*`.
- Permission issues: reconnect board or restart macOS; ensure user access to device.
- Incorrect distances: verify wiring and ensure proper level shifting on `ECHO`.
- Clean build: `pio run -e uno_r4_wifi -t clean` then rebuild.

## License
Add a `LICENSE` file (MIT recommended if unspecified).

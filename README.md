# Atom S3 ESPHome Bluetooth Proxy with Display

This repository contains a working ESPHome configuration for using the
**M5Stack Atom S3** as a **Bluetooth Proxy** for Home Assistant, with a
built-in **128×128 ST7789 display** used to show device status.

The goal of this project is a **stable, always-on Bluetooth proxy**
with a small, useful status screen.

---

## Features

- ESPHome Bluetooth Proxy
- ESP32-S3 (ESP-IDF framework)
- Built-in 128×128 SPI TFT display (ST7789)
- Wi-Fi signal strength (RSSI), color-coded
- ESPHome online/offline status
- Deterministic backlight control (no flicker, no white-line issues)
- Event-driven display updates (no polling loops)

---

## Hardware

- **M5Stack Atom S3**
- Built-in 128×128 SPI TFT display
- Built-in button (not currently used)
- Built-in backlight control on GPIO16

---

## Display Behavior

The display shows:

- Device role (“BT Proxy”)
- ESPHome connection status
- Wi-Fi signal strength in dBm
  - Green: strong
  - Orange: moderate
  - Red: weak

The display updates only when relevant state changes occur
(e.g., Wi-Fi RSSI or ESPHome status).

---

## Files

```text
atom-s3-esphome-bluetooth-proxy/
├── atom-s3-bluetooth-proxy.yaml
├── secrets.yaml.example
└── README.md
```
---

## ESPHome Version

This configuration was tested with:

- ESPHome 2025.12.3
- ESP-IDF framework (default ESPHome platform)

Later versions should work, but display behavior should be verified
after upgrades.

---

## Installation

1. Copy `atom-s3-bluetooth-proxy.yaml` into your ESPHome configuration directory.
2. Copy `secrets.yaml.example` to `secrets.yaml`.
3. Fill in your Wi-Fi credentials and ESPHome API/OTA secrets.
4. Adjust the device name if desired.
5. Compile and flash the firmware using ESPHome.

---

## Notes

- This configuration is designed for **long-term stability**.
- The display is intentionally simple and low-overhead.
- Bluetooth activity is validated through actual Home Assistant sensor data,
  not inferred indicators.

## Hardware Reference

- M5Stack Atom S3 documentation:  
  https://docs.m5stack.com/en/core/AtomS3

- ESPHome Bluetooth Proxy docs:  
  https://esphome.io/components/bluetooth_proxy.html

- ESPHome ST7789 display component:  
  https://esphome.io/components/display/st7789v.html

---

## License

MIT

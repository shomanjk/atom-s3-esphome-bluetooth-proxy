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
- Safe mode and factory reset via Home Assistant **and** the built-in button
- Optional MAC suffix on the device name for multiple units (`substitutions`)

---

## Hardware

- **M5Stack Atom S3** (128×128 LCD variant; not Atom S3 **Lite**)
- Built-in 128×128 SPI TFT display
- Built-in button on **GPIO41** (same stack as the [M5 pin map](https://docs.m5stack.com/en/core/AtomS3); other SKUs may differ)
- Built-in backlight control on GPIO16

### Button behavior

- **Double-click** the physical button → same as the **Safe mode boot** button (next reboot enters [safe mode](https://esphome.io/components/safe_mode/)).
- **Hold ~8 seconds** → same as **Factory reset** (clears provisioning; use with care).
- Those actions are also available as entities in Home Assistant when the device is online.

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
- The display rotation option is included (commented) in the YAML for users
  who mount the Atom S3 in a different orientation.


---

## Files

```text
atom-s3-esphome-bluetooth-proxy/
├── atom-s3-bluetooth-proxy.yaml
├── secrets.yaml.example
├── .gitignore
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

1. Copy [`atom-s3-bluetooth-proxy.yaml`](atom-s3-bluetooth-proxy.yaml) into your ESPHome configuration directory.
2. Copy [`secrets.yaml.example`](secrets.yaml.example) to `secrets.yaml`.
3. Fill in your Wi-Fi credentials and ESPHome API/OTA secrets.
4. Optional: edit the `substitutions` block at the top of the YAML (device name, friendly name, `name_add_mac_suffix` for several proxies on one network, fallback AP SSID, RSSI color thresholds).
5. Compile and flash the firmware using ESPHome.

---

## Notes

- This configuration is designed for **long-term stability**.
- The display is intentionally simple and low-overhead.
- Bluetooth proxy operation is validated through Home Assistant device behavior,
  not inferred indicators.

## Hardware Reference

- M5Stack Atom S3 documentation:  
  https://docs.m5stack.com/en/core/AtomS3

- ESPHome Bluetooth Proxy docs:  
  https://esphome.io/components/bluetooth_proxy.html

- ESPHome ST7789 display component:  
  https://esphome.io/components/display/st7789v.html

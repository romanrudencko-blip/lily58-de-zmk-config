# ZMK Keyboard Configuration

This is a personal ZMK firmware configuration repository for the **Lily58 keyboard** with support for OLED displays and German locale.
I am not done with the keyboard map itself, it will be updated in the future. Customize to your liking with the very helpful [Keymap Editor by nickcoutsos](https://nickcoutsos.github.io/keymap-editor/)

## Overview

This configuration uses [ZMK Firmware](https://zmk.dev/), a modern open-source keyboard firmware, to power a split wireless Lily58 keyboard setup. The build is optimized for German keyboard layouts and includes advanced features like OLED status displays via the nice!OLED module.

## Hardware

- **Keyboard**: Lily58 (split ergo keyboard)
- **Controllers**: Nice!Nano v2 (both halves)
- **Displays**: Nice!OLED modules for real-time status feedback
- **Encoder**: Optional support for rotary encoders (currently disabled)

## Features

### Locale Support

This configuration leverages the **[ZMK Locales Project](https://github.com/joelspadin/zmk-locales)** to provide German (DE) keyboard support:

- German key bindings (QWERTZ layout)
- Special character support (ä, ö, ü, ß, etc.)
- Proper German modifier and symbol mappings (sends German keycodes, no need to switch keyboard layout!)
- Located at: `<locale/keys_de.h>` (from the zmk-locales project)

**ZMK Locales Repository**: https://github.com/joelspadin/zmk-locales

### OLED Display Module

The **[Nice!OLED Module](https://github.com/mctechnology17/zmk-nice-oled)** provides OLED display support for real-time keyboard status:

- Status display showing active layers
- Bluetooth connection status
- Battery level indicator
- Shield configuration: `nice_oled` (used alongside `lily58_left` and `lily58_right`)
- Configuration flag: `CONFIG_ZMK_DISPLAY=y`

**OLED Module Repository**: https://github.com/mctechnology17/zmk-nice-oled

### Key Features

- **Custom Behaviors**: Hold-tap behaviors for efficient modifier usage

  - `HMR` / `HML`: Home row modifiers (right/left)
  - `HMShiftR` / `HMShiftL`: Shift-specific modifiers
  - `longPress`: Custom long-press behavior
  - `underscoreDBTap`: Tap-dance for underscore/hyphen

- **Three-Layer Keymap**:

  - **Default Layer**: QWERTZ layout with German characters
  - **Lower Layer**: Function keys, Bluetooth controls, and symbols
  - **Raise Layer**: Navigation, numbers, and operators

- **Wireless Connectivity**: Bluetooth support via Nice!Nano controllers

## Directory Structure

```
.
├── config/                      # Main keyboard configuration
│   ├── lily58.keymap           # Keymap definition
│   ├── lily58.conf             # Device configuration
│   ├── keys_de.h               # German key definitions (custom overrides)
│   └── west.yml                # Zephyr module manifest
├── boards/                      # Custom board definitions
├── zephyr/                      # Zephyr module configuration
├── build.yaml                  # GitHub Actions build matrix
└── README.md                   # This file
```

## Configuration Files

### `lily58.conf`

Enables the OLED display and custom status screen configuration for the Lily58 keyboard.

### `lily58.keymap`

Contains the complete keymap with three layers and custom behaviors optimized for German typing.

### `west.yml`

Defines module dependencies including:

- **ZMK Firmware**: Main keyboard firmware
- **ZMK Locales**: German locale support
- **ZMK Nice!OLED**: OLED display driver

### `keys_de.h`

Custom German key definitions and mappings.

## Build & Deployment

This configuration uses GitHub Actions for automated builds. The build matrix in `build.yaml` specifies:

- **Board**: `nice_nano_v2`
- **Shields**: `lily58_left nice_oled` and `lily58_right nice_oled`

## Getting Started

1. **Clone this repository** to your ZMK workspace
2. **Ensure all dependencies** from `west.yml` are installed
3. **Build the firmware** using ZMK build tools
4. **Flash to your keyboard** using your microcontroller's bootloader

## Documentation & Resources

- **ZMK Documentation**: https://zmk.dev/
- **ZMK Keymap Editor**: https://nickcoutsos.github.io/keymap-editor/
- **ZMK Locales Documentation**: https://github.com/joelspadin/zmk-locales#readme
- **Nice!OLED Documentation**: https://github.com/mctechnology17/zmk-nice-oled#readme
- **Lily58 Keyboard**: https://github.com/kata0510/Lily58

## License

This configuration is provided as-is. Refer to individual module licenses for usage terms.

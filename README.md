# uwe5622 Linux Driver

Linux kernel drivers for the Unisoc/Spreadtrum uwe5622 wireless connectivity chipset.

## Overview

This repository provides out-of-tree kernel drivers for the uwe5622 wireless chipset, commonly found on ARM-based single-board computers from Allwinner and Rockchip platforms (e.g., Orange Pi Zero 2, Orange Pi 3 LTS, Orange Pi 4).

The uwe5622 is a combo chipset that provides:
- **WiFi** (802.11b/g/n, 2.4 GHz)
- **Bluetooth** (BLE + Classic)
- **GNSS** (GPS/GLONASS/BeiDou/Galileo)

## Project Structure

```
uwe5622/
├── unisocwcn/      # Wireless Connectivity Network core
│   ├── boot/       # Firmware/boot loader
│   ├── gnss/       # GNSS driver components
│   ├── sdio/       # SDIO interface
│   ├── usb/        # USB interface
│   ├── pcie/       # PCIe interface
│   └── ...
├── unisocwifi/     # WiFi driver (cfg80211-based)
├── tty-sdio/       # TTY over SDIO driver (for Bluetooth)
└── reference/      # Historical patches and documentation
```

## Features

- **WiFi driver**: Full cfg80211-based implementation supporting:
  - Station and SoftAP modes
  - IBSS (Ad-hoc) with WPA2 support
  - WMM AC certification
  - NAN (Neighbor Awareness Network)
  - RTT (Round Trip Time)
  - DFS (Dynamic Frequency Selection)

- **Bluetooth**: TTY over SDIO for Bluetooth HCI communication

- **GNSS**: Support for multiple satellite navigation systems

- **Power Management**: Platform-specific power saving and sleep modes

## Status

This is community-maintained software derived from vendor BSPs. It is actively developed to support newer kernel versions as they are released.

## Kernel Compatibility

The drivers are maintained to work with modern kernel versions. Patches for specific kernel versions are available in the `reference/` directory.

Supported kernel versions include:
- Linux 6.1
- Linux 6.12
- Linux 6.18
- Linux 7.0
- Linux 7.1

## Building

The driver is designed to be automatically build and included in images created with the Armbian Build Framework. Building/installing out of tree on a running system may work, though no instructions can be provided for doing so since entirely untested.

## Platform Support

Tested on:
- **Orange Pi Zero 2** (Allwinner H616)
- **Orange Pi 3 LTS** (Allwinner H6)
- **Orange Pi 4** (Rockchip RK3399)
- Similar boards with UWE5622 chipset

## Firmware

Required firmware files should be placed in `/lib/firmware/uwe5622/`:
- `wcnmodem.bin` - Main firmware binary
- `nvm.bin` - NV configuration

## Contributing

This is community-supported software. Contributions are certainly appreciated.

## License

GPL-2.0

## References

- Original driver source: Spreadtrum Communications Inc.
- Armbian integration: https://github.com/armbian/build

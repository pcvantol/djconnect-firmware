# DJConnect Firmware Releases

DJConnect. Jouw persoonlijke muziek DJ.

This repository is the public firmware distribution repository for DJConnect ESP32-S3 devices. It contains OTA release artifacts only. The firmware source code is proprietary and is not published in this repository.

## What This Repository Contains

DJConnect firmware releases are published here so the Home Assistant DJConnect integration can offer safe, board-specific OTA updates.

Each stable release normally contains:

- `firmware_manifest.json`: machine-readable release metadata for Home Assistant and OTA selection.
- `djconnect-lilygo-t-embed-s3-vX.Y.Z.bin`: firmware for LilyGO T-Embed S3 / T-Embed CC1101 devices.
- `djconnect-lilygo-t-embed-s3-vX.Y.Z.bin.sha256`: SHA256 checksum for the LilyGO firmware.
- `djconnect-esp32-s3-box-3-vX.Y.Z.bin`: firmware for ESP32-S3-BOX-3 devices.
- `djconnect-esp32-s3-box-3-vX.Y.Z.bin.sha256`: SHA256 checksum for the BOX-3 firmware.

Beta prereleases use the same board split, but beta assets include `beta` in the filename.

## Supported Devices

| Device | OTA device model | Firmware asset pattern |
| --- | --- | --- |
| LilyGO T-Embed S3 / T-Embed CC1101 | `lilygo-t-embed-s3` | `djconnect-lilygo-t-embed-s3-vX.Y.Z.bin` |
| ESP32-S3-BOX-3 | `esp32-s3-box-3` | `djconnect-esp32-s3-box-3-vX.Y.Z.bin` |

Use the firmware asset that exactly matches the device model. The Home Assistant integration does this automatically when OTA is started from Home Assistant.

## OTA Flow

Most users should not manually flash files from this repository. The normal update path is:

1. The DJConnect Home Assistant integration checks the latest release manifest.
2. The integration selects the matching firmware from the manifest `firmwares` array.
3. Home Assistant calls the paired ESP device OTA endpoint.
4. The ESP downloads the selected binary, verifies the SHA256 hash, writes the OTA partition, and reboots only after verification succeeds.

Manual downloads are mainly useful for diagnostics or recovery flows where the exact device model and firmware version are known.

## Version Compatibility

Firmware and the Home Assistant integration are versioned together by major and minor version.

For example, firmware `3.1.z` is intended for the `3.1` Home Assistant integration line. Release manifests expose compatibility metadata such as:

```json
{
  "min_ha_integration": "3.1.0",
  "max_ha_integration": "<3.2.0"
}
```

Patch versions may differ, but major/minor versions should stay aligned.

## Integrity And Safety

Every firmware binary is published with a SHA256 checksum. OTA updates are expected to verify the hash before the device reboots into the new firmware.

Do not rename assets or reuse an asset from one board on another board. Board-specific firmware contains different display, button, audio, battery and LED-ring configuration.

## Related Links

- Website: https://djconnect.pages.dev
- Home Assistant integration: https://github.com/pcvantol/djconnect
- Firmware releases: https://github.com/pcvantol/djconnect-firmware/releases

## License

Copyright (c) 2026 Peter van Tol. All rights reserved.

DJConnect firmware is proprietary software. This repository provides published firmware binaries for supported DJConnect update flows. It does not grant source-code rights or rights to modify, redistribute, reverse engineer, or create derivative works from the firmware.

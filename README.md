# DJConnect Firmware Releases

DJConnect. Muziekbediening met karakter.

DJConnect lets you ask for music and get it personally announced through Home
Assistant. This public repository distributes firmware update artifacts for
DJConnect ESP32-S3 hardware clients only. It does not contain firmware source
code.

## Repository Scope

This repository is intentionally small and contains release metadata and
board-specific OTA binaries. Firmware source development happens in the private
DJConnect firmware source repository.

DJConnect firmware releases are published here so the Home Assistant DJConnect
integration can offer safe, board-specific OTA updates.

Each stable release normally contains:

- `firmware_manifest.json`: machine-readable release metadata for Home Assistant and OTA selection.
- `djconnect-lilygo-t-embed-s3-vX.Y.Z.bin`: firmware for LilyGO T-Embed S3 / T-Embed CC1101 devices.
- `djconnect-lilygo-t-embed-s3-vX.Y.Z.bin.sha256`: SHA256 checksum for the LilyGO firmware.
- `djconnect-esp32-s3-box-3-vX.Y.Z.bin`: firmware for ESP32-S3-BOX-3 devices.
- `djconnect-esp32-s3-box-3-vX.Y.Z.bin.sha256`: SHA256 checksum for the BOX-3 firmware.

Beta prereleases use the same board split, but beta assets include `beta` in the filename.

## Requirements

- A supported DJConnect ESP32-S3 device.
- Home Assistant with the DJConnect integration installed.
- Matching major/minor versions between firmware and the Home Assistant
  integration, for example firmware `3.1.z` with integration `3.1.z`.
- Local network access from the ESP device to Home Assistant during pairing and
  runtime.
- Spotify Premium and a configured Home Assistant Assist/STT/TTS setup when
  using music playback and voice features.

## Supported Devices

| Device | OTA device model | Firmware asset pattern |
| --- | --- | --- |
| LilyGO T-Embed S3 / T-Embed CC1101 | `lilygo-t-embed-s3` | `djconnect-lilygo-t-embed-s3-vX.Y.Z.bin` |
| ESP32-S3-BOX-3 | `esp32-s3-box-3` | `djconnect-esp32-s3-box-3-vX.Y.Z.bin` |

Use the firmware asset that exactly matches the device model. The Home Assistant integration does this automatically when OTA is started from Home Assistant.

## Normal Update Flow

Most users should not manually flash files from this repository. The normal
update path is:

1. The DJConnect Home Assistant integration checks the latest release manifest.
2. The integration selects the matching firmware from the manifest `firmwares` array.
3. Home Assistant calls the paired ESP device OTA endpoint.
4. The ESP downloads the selected binary, verifies the SHA256 hash, writes the OTA partition, and reboots only after verification succeeds.

Manual downloads are mainly useful for diagnostics or recovery flows where the
exact device model and firmware version are known.

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

- Website: [https://djconnect.dev](https://djconnect.dev)
- Home Assistant integration: [pcvantol/djconnect](https://github.com/pcvantol/djconnect)
- Apple app releases: [pcvantol/djconnect-app-releases](https://github.com/pcvantol/djconnect-app-releases)
- Raspberry Pi client releases: [pcvantol/djconnect-pi-releases](https://github.com/pcvantol/djconnect-pi-releases)
- Firmware releases: [pcvantol/djconnect-firmware/releases](https://github.com/pcvantol/djconnect-firmware/releases)

## Privacy And Security

Firmware binaries do not contain Spotify credentials, Home Assistant tokens,
device tokens, WiFi passwords or other user secrets. Pairing creates a
per-device token at setup time; Spotify OAuth credentials stay in Home
Assistant.

## License

Copyright (c) 2026 Peter van Tol. All rights reserved.

DJConnect firmware is proprietary software. This repository provides published
firmware binaries for supported DJConnect update flows. It does not grant
source-code rights or rights to modify, redistribute, reverse engineer, or
create derivative works from the firmware.

Spotify is a trademark of Spotify AB. DJConnect is not affiliated with,
endorsed by, or sponsored by Spotify AB.

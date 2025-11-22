# Changelog

All notable changes to this project will be documented in this file.

The original plugin is **homebridge-yamaha-receiver** by @nitaybz. This fork is published as **homebridge-yamaha-receiver-ya**.

## [0.0.3] - 2025-11-22

- **Project branding and metadata**
  - Renamed package to `homebridge-yamaha-receiver-ya`.
  - Updated repository URL and bugs URL to point to `averkiev/homebridge-yamaha-receiver-ya`.
  - Updated README links to reference the Homebridge repo and new donation link.
- **Firmware version in HomeKit**
  - Added optional `firmware` field per receiver in `config.schema.json`.
  - Propagated `firmware` from receiver config into internal device/zone config in `lib/avr.js`.
  - Exposed firmware to HomeKit via `Characteristic.FirmwareRevision` on the Accessory Information service in `accessories/Receiver.js`.

## [0.0.2] - 2025-11-22

- **Homebridge 2 / Node 20 compatibility**
  - Set engines to `"node": ">=20.0.0"` and `"homebridge": ">=1.1.6 <3.0.0"` in `package.json`.
  - Confirmed dynamic platform registration style (`api.registerPlatform`) is compatible with Homebridge 1.x and 2.x.
- **Dependencies**
  - Updated `node-persist` to `^4.0.4`.
  - Updated `eslint` to `^9.39.1`.
  - Kept `yamaha-nodejs` at `^0.9.6` (latest available) with known `npm audit` warnings inherited from its legacy HTTP stack (`request`, `form-data`, `tough-cookie`, `xml2js`).
- **Bug fixes and minor robustness improvements**
  - Fixed zone configuration bug in `lib/avr.js` where `zone2/3/4` `minVolume` incorrectly referenced `MaxVolume` and had a typo in the config key (`zone${i}MaVolume` → `zone${i}MinVolume`).
  - Added a defensive check in `lib/stateManager.js` for `ActiveIdentifier` so an unknown input identifier no longer throws; logs a debug message and safely returns.

## [0.0.1] - 2025-11-22

- Initial fork of `homebridge-yamaha-receiver`.
- Renamed plugin and updated:
  - `index.js` `PLUGIN_NAME` to `homebridge-yamaha-receiver-ya`.
  - `package.json` metadata (name, description, repository, funding).
  - `config.schema.json` footer to indicate this is a fork by @averkiev, based on the original plugin by @nitaybz.
- No functional changes relative to upstream other than metadata.

## [0.0.7] - upstream (original project)

- Last known upstream release of `homebridge-yamaha-receiver` before this fork.
- Original implementation of Yamaha AVR discovery, zone handling, cached device state, and HomeKit Television/volume accessory behavior.

[0.0.3]: https://github.com/averkiev/homebridge-yamaha-receiver-ya/tree/v0.0.3
[0.0.2]: https://github.com/averkiev/homebridge-yamaha-receiver-ya/tree/v0.0.2
[0.0.1]: https://github.com/averkiev/homebridge-yamaha-receiver-ya/tree/v0.0.1

# Changelog



## 6.0.42 (2026-03-18)

- Release-Name: Right Here, Right Now 🔥 ⏱️ 🚀

### Features and Enhancements

- Added `dali_settings` to all `/api/devices/<id>/config` endpoints to support configuration of DALI dimmers with 1–4 channels 💡🎛️
  The DALI dimmer previously operated as a broadcast dimmer (single channel).
  It can now be configured to use 2, 3, or 4 channels, operating in group-addressed mode.
  Allows independent control of up to four DALI groups ✨
  > ⚠️ Minimum required device firmware version: 2.8.2-0

- Added soft_off option to all /api/devices/<id>/config/outputs endpoints for DALI devices 🌙✨

- Improved file system performance ⚡💾

### Bug fixes

- Improved startup reliability and device synchronization to prevent missing device information (e.g. `comm_name`, `comm_ref`, `serial_nr`) during initialization 🚀🧩

- Fixed DELETE /api/buttons/<id> to ensure all LEDs are turned off when a button is removed 🔘❌



## 6.0.41 (2026-01-23)

- Release-Name: *A Sky Full of Stars* 🌠 🚀 ✨

### Features and Enhancements

- Introduced new REST API services at the `/api/buttons` endpoint to expose buttons within the Feller-System (managed buttons) 🔘✨

- Added additional WebSocket events that are triggered when managed buttons are pressed 🔔🖱️

- Extended the device configuration endpoint `/api/devices/config/<id>/inputs` with new properties: `foreground_color` and `background_color` 🌈🧩
  > ⚠️ Please note: Updating devices is required for these changes to take effect 🔄  
    (Minimum required device version: **2.8.2-0**)

- Enhanced the scripting framework with webhook support 🌐🔗  
  You can now create custom scripts that trigger actions within the Feller-System based on incoming webhooks ⚙️✨  
  📄 A sample script is available on the scripts page for reference 👀



## 6.0.40 (2025-12-23)

- Release-Name: *Let It Be* 🎄 🕊️ ✨

### Features and Enhancements

- REST API service `/api/devices/<id>/refresh_properties` to read all device registers (e.g. `comm_ref`), as reported in issues 🐞 ([#43](https://github.com/Feller-AG/wiser-api/issues/43), [#52](https://github.com/Feller-AG/wiser-api/issues/52))

- Support for **ECDHE-RSA** cipher suite modes for SSL/TLS 🔒 ([#51](https://github.com/Feller-AG/wiser-api/issues/51))

- Optional text `reason-phrase` after the status code in HTTP response headers 🧾 ([#50](https://github.com/Feller-AG/wiser-api/issues/50))

- New option to manually select the release channel, e.g. **Preview Release Channel 🚀**

### Bug fixes

- Made HTTP response headers RFC 7230 compliant 📜 ([#50](https://github.com/Feller-AG/wiser-api/issues/50))

- Ensures that all properties of a device are always properly set 🧩 ([#43](https://github.com/Feller-AG/wiser-api/issues/43), [#52](https://github.com/Feller-AG/wiser-api/issues/52))

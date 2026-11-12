# Changelog



## 6.0.49 (2026-11-03)

- Release-Name:  **Time After Time** *(Cyndi Lauper)* 🛰️ ⏰ 🎶

### Features and Enhancements

- Added the new service `PUT /api/loads/<id>/protection` to move a motor load (e.g. blinds) to a safe position and lock it for a given time 🔒🪟
  Example: `{"action": "up and lock", "duration": 30}` moves the blind up and locks it for 30 minutes.
  Possible actions are `off` (release the lock), `up`, `down`, `stay and lock`, `up and lock`, `down and lock` and `down and tilt and lock`.
  The lock duration is given in minutes (0–255). The active protection is shown in the `protection` object of the load state.
  > ⚠️ Only for loads of type `motor`. Minimum required device firmware version: **2.8.7-283**
- Added the new optional property `protections` to `/api/jobs` 🛡️
  A job can now contain a list of motor protections, each with a `load`, an `action` and a `duration` (same as above).
  The protections are sent whenever the job is triggered, e.g. by a timer, a script or a scene SmartButton.
  This allows e.g. a "Storm" job that moves all blinds up and locks them.
- Added the new services `GET`, `PUT` and `PATCH /api/time/gpsconfig` to use the GPS time of a weather station as time source 🛰️⏰
  With `{"enabled": true}` the µGateway sets its system time from the weather station, which is useful for installations without an Internet connection.
  The GPS time is only used if NTP is disabled or NTP could not set the time since the last startup.
  The response also shows the last received GPS time (`utc`) and position (`position`) and whether the system time was synchronized (`synced`).
- Added the new read-only property `synced` to `/api/time/ntpconfig`, which is `true` as soon as NTP has set the system time since the last startup ✅
- Added the new optional property `ntc_r25` to the inputs of `/api/devices/<id>/config` to set the resistance of an external NTC temperature sensor at 25 °C (1000–100000 Ω, default 33000 Ω) 🌡️
  This allows the use of NTC sensors with different characteristics. The property is only present if the NTC input is enabled and supported by the device firmware.
- Changed `PUT /api/time/now`: after setting the time manually, the µGateway reboots with the new reboot cause `API_RTC_CHANGE` 🔄
  In contrast to before, NTP or GPS may now correct the manually set time immediately after this reboot.
- Improved the detection of devices: faster startup, new or restarted devices are found much faster and several µGateways on the same installation work together better 🔍⚡
- Improved the local web interface with a new **Time (NTP & GPS)** section on the **settings** page, timers for HVAC groups, a device bindings viewer and new filters on the **devices** page 🖥️✨
- Reduced memory usage for more stability in large installations 💾

### Bug Fixes

- Fixed `/api/devices` to show the SmartButton id of local buttons in the device inputs 🔘
- Fixed the web server to treat a request without `Content-Length` header as a request with an empty body 📨
- Fixed the web server to correctly finish large (chunked) responses, so following requests are not blocked anymore 🧩
- Fixed button groups on the local outputs of the µGateway, e.g. after the device configuration was changed to more outputs (number of DALI groups) 💡
- Fixed a rare crash during device requests 🩹



## 6.0.48 (2026-10-02)

- Release-Name:  **Our House** *(Madness)* 🏠 🎹 🎶

### Features and Enhancements

- Improved the **loads** and **sensors** pages of the local web interface: sensors are now grouped (e.g. by room), groups can be renamed and loads/sensors can be moved between groups 🗂️
- Improved the developer options of the **devices** page with a register picker showing the full register description 🔍
- Added tooltips to the icon buttons of the local web interface 💬

### Bug Fixes

- Fixed `cat` on the **cli** page of the local web interface for files containing UTF-8 characters (e.g. emojis) 🔤



## 6.0.47 (2026-9-21)

- Release-Name:  **Come Together** *(Beatles)* 🤝 🔗 🎶

### Features and Enhancements

- Extended `api/westgroups` to include the actual sensor value 🌡️ and sensor reference 🔗.
- Improved the overall user experience of the local web interface with various general improvements and a cleaner 🧹, more polished 🧼 user interface.

### Bug Fixes

- Fixed `api/smartbutton/notify` in `groupctrl` program mode so that the LED now lights up yellow 🟡 instead of blue 🔵.
- Fixed 🩹 an glitch with the local toggle button of the µGW where the button's status LED could become out of sync with the actual state of the corresponding output channel.



## 6.0.46 (2026-8-21)

- Release-Name:  **Running Up That Hill** *(Kate Bush)* 🌙 🏃‍♀️ ⛰️

### Features and Enhancements

- Added database hash caching to improve performance
- Added scripts, script-configs and script-crontabs to backup (csa archive)


## 6.0.45 (2026-7-17)

- Release-Name:  **Connected** *(Stereo MC's)* 🔗 ☁️ ⚡

### Features and Enhancements

- Enhanced overall system stability

### Bug Fixes

- Improved chunked response handling with fixed unicode support and better error handling



## 6.0.44 (2026-07-01)

- Release-Name: **Superstylin** *(Groove Armada)* ✨ 🕶️ 🎛️

### Features and Enhancements

- Extended `api/hvac/config` with new configuration options for the touch display thermostat 🌡️🎛️

- Extended `api/scripts` with trigger information, making it easier for clients to identify how and why a script was started, such as by a cron job, a sensor event, or a button action 🔍⚙️

### Bug Fixes

- Fixed the default `findme` button colors in `api/buttons/findme`, so different button types now blink with distinct colors and can be identified more easily 🔍💡

- Fixed the mDNS responder to properly re-initialize the mDNS service after the µGateway receives a new IP address, ensuring the device remains discoverable after network changes such as WLAN reconnects 📡🔧

- Improved overall system performance when the µGateway has no network connection, reducing delays and improving responsiveness in offline or temporarily disconnected installations ⚡🌐



## 6.0.43 (2026-05-06)

- Release-Name: **Freestyler** *(Bomfunk MC's)* 🎲 🔥 ✨

### Features and Enhancements

- Extended `api/hvacgroup/<id>/config` with new HVAC configuration options, laying the groundwork for next-generation thermostat support 🌡️✨

- Added endpoint `api/database/hash` to allow clients to verify the integrity of the µGateway database without downloading the full database 🗄️🔑

- Added header fields `Content-Signature` & `Content-Hash` to endpoint `api/database`, allowing clients to verify the authenticity and integrity of the database response 🔒

- Improved HVAC page with additional configuration options, ready for the next generation of thermostat devices 🌡️✨

### Bug Fixes

- Fixed `findme` service across `api/loads/findme`, `api/sensors/findme` and `api/buttons/findme` to always correctly apply default colors, ensuring loads, sensors and buttons blink as expected when locating them in an installation 🔍💡



## 6.0.42 (2026-03-18)

- Release-Name: **Right Here, Right Now** *(Fatboy Slim)* 🔥 ⏱️ 🚀

### Features and Enhancements

- Added `dali_settings` to all `/api/devices/<id>/config` endpoints to support configuration of DALI dimmers with 1–4 channels 💡🎛️
  The DALI dimmer previously operated as a broadcast dimmer (single channel).
  It can now be configured to use 2, 3, or 4 channels, operating in group-addressed mode.
  Allows independent control of up to four DALI groups ✨
  > ⚠️ Minimum required device firmware version: 2.8.2-0

- Added soft_off option to all `/api/devices/<id>/config/outputs` endpoints for DALI devices 🌙✨

- Improved file system performance ⚡💾

### Bug fixes

- Improved startup reliability and device synchronization to prevent missing device information (e.g. `comm_name`, `comm_ref`, `serial_nr`) during initialization 🚀🧩

- Fixed DELETE `/api/buttons/<id>` to ensure all LEDs are turned off when a button is removed 🔘❌



## 6.0.41 (2026-01-23)

- Release-Name: **A Sky Full of Stars** *(Coldplay)* 🌠 🚀 ✨

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

- Release-Name: **Let It Be** *(The Beatles)*  🎄 🕊️ ✨

### Features and Enhancements

- REST API service `/api/devices/<id>/refresh_properties` to read all device registers (e.g. `comm_ref`), as reported in issues 🐞 ([#43](https://github.com/Feller-AG/wiser-api/issues/43), [#52](https://github.com/Feller-AG/wiser-api/issues/52))

- Support for **ECDHE-RSA** cipher suite modes for SSL/TLS 🔒 ([#51](https://github.com/Feller-AG/wiser-api/issues/51))

- Optional text `reason-phrase` after the status code in HTTP response headers 🧾 ([#50](https://github.com/Feller-AG/wiser-api/issues/50))

- New option to manually select the release channel, e.g. **Preview Release Channel 🚀**

### Bug fixes

- Made HTTP response headers RFC 7230 compliant 📜 ([#50](https://github.com/Feller-AG/wiser-api/issues/50))

- Ensures that all properties of a device are always properly set 🧩 ([#43](https://github.com/Feller-AG/wiser-api/issues/43), [#52](https://github.com/Feller-AG/wiser-api/issues/52))

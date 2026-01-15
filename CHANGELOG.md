# 6.0.40 (2025-12-23)

- Release-Name: *Let It Be* 🎄 🕊️ ✨

## Features and enhancements

- REST-API service `/api/devices/<id>/refresh_properties` to read all device-register (e.g. `comm_ref`), reported in issues ([#43](https://github.com/Feller-AG/wiser-api/issues/43), [#52](https://github.com/Feller-AG/wiser-api/issues/52))
- support for **ECDHE-RSA** cipher suite modes for SSL/TLS ([#51](https://github.com/Feller-AG/wiser-api/issues/51))
- optional text `reason-phrase` after the status code in HTTP response headers ([#50](https://github.com/Feller-AG/wiser-api/issues/50))
- New option to manually select the release channel e.g. **[Preview Release Channel 🚀]**

## Bug fixes

- make HTTP response-header RFC 7230 compliant ([#50](https://github.com/Feller-AG/wiser-api/issues/50))
- ensures that all properties of a device are always set ([#43](https://github.com/Feller-AG/wiser-api/issues/43), [#52](https://github.com/Feller-AG/wiser-api/issues/52))

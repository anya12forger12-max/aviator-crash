# GP Aviator APKs

Permanent public downloads for the Android builds. The current files are the
audit-fixed release (branch `fix/audit-findings`, commit `f80f81d`) with version code 6.

- Debug APK: `gp-aviator-debug.apk`
- Signed release APK: `gp-aviator-release.apk`
- SHA-256 checksums: `SHA256SUMS.txt`
- Current gateway URL: `gateway-url.txt` in this branch

Direct URLs:

- https://raw.githubusercontent.com/anya12forger12-max/aviator-crash/apk-release/gp-aviator-debug.apk
- https://raw.githubusercontent.com/anya12forger12-max/aviator-crash/apk-release/gp-aviator-release.apk

The gateway is an ephemeral Cloudflare HTTP/2 Quick Tunnel and can change when
the tunnel or machine restarts. Both APKs have `gateway-url.txt` baked in, but
the app's in-app gateway setting can override it without reinstalling. The
quick tunnel targets the hardened nginx port 8444, which blocks admin routes.

The signed APK is signed with `CN=Aviator, O=GP, C=US` (certificate SHA-256
`a8b758c357110b3e6b72634f41ccf7c204f6b13914494a5f0d36d8688cb01bc0`) and
verifies with APK Signature Scheme v2 and v3. It is a new key: devices with an
older signing identity must uninstall the old app first.

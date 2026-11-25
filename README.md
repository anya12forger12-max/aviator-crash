# GP Aviator APKs

Permanent public downloads for the Android builds.

- Debug APK: `gp-aviator-debug.apk`
- Signed release APK: `gp-aviator-release.apk`
- SHA-256 checksums: `SHA256SUMS.txt`
- Current gateway URL: `gateway-url.txt` in this branch

Direct URLs:

- https://raw.githubusercontent.com/anya12forger12-max/aviator-crash/apk-release/gp-aviator-debug.apk
- https://raw.githubusercontent.com/anya12forger12-max/aviator-crash/apk-release/gp-aviator-release.apk

The gateway is a temporary Cloudflare Quick Tunnel and can change when the
local tunnel restarts. Both APKs have the URL in `gateway-url.txt` baked in, but
the app's in-app gateway setting can override it without reinstalling.

The signed release is signed with a self-signed key (`CN=Aviator`) and verified
with APK Signature Scheme v2 and v3. It is not a Play Store signing key.

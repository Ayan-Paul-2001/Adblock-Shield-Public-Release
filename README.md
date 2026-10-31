# AdBlock Shield Pro — Official Public Release (`V2.0.1`)

<p align="center">
  <img src="app_logo.png" alt="AdBlock Shield Pro Logo" width="140" />
</p>

<p align="center">
  <b>System-Wide Android Ad, Tracker & YouTube Blocker Powered by Brave Shields Technology</b><br/>
  Compatible with <b>Android 8.0 (Oreo, API 26) through Android 16+</b> • Developed by <a href="https://ayanpaul.me"><b>Ayan Paul</b></a>
</p>

---

## Direct APK Download (`V2.0.1`)

| Package | Version | Build Code | Download Link |
| :--- | :--- | :--- | :--- |
| **AdBlock Shield Pro (Latest Release APK)** | `V2.0.1` | `201` | [**Download `AdBlock-Shield.apk`**](https://raw.githubusercontent.com/Ayan-Paul-2001/Adblock-Shield-Public-Release/main/AdBlock-Shield.apk) |
| **OTA Auto-Update Version Manifest** | `V2.0.1` | `201` | [`version.json`](./version.json) |

---

## What's New in `V2.0.1`

1. **Brave Browser Shields Engine (`v156.1.98.63` Parity)**:
   - **Dual-Stack IPv4 + IPv6 System DNS Sinkhole**: Routes both IPv4 (`10.111.222.1/24`) and IPv6 (`fd00:1:fd00:1:fd00:1:fd00:1/128`) DNS traffic—including Chrome's built-in `AsyncDns` resolvers (`8.8.8.8`, `1.1.1.1`, `9.9.9.9`, `2001:4860:4860::8888`, `2606:4700:4700::1111`)—through the on-device sinkhole.
   - **Anti-DoH Canary & `HTTPS`/`SVCB` (QTYPE 65/64) Blocking**: Prevents browsers and apps from silently upgrading to encrypted DNS-over-HTTPS (`use-application-dns.net`, `dns.google`, `cloudflare-dns.com`, `one.one.one.one`) to bypass ad filtering.
   - **Brave CNAME-Uncloaking Engine**: Inspects DNS `CNAME` chains in real time before delivering responses, blocking disguised first-party subdomains that resolve to third-party trackers (`*.omtrdc.net`, `*.2o7.net`, `*.adobedc.net`, `*.dnsdelegation.io`, `*.eulerian.net`, `*.dataunlocker.com`, `*.stape.io`, `*.tracedock.com`, `*.intentiq.com`).
   - **Brave `CleanUrlsEngine` & `DebounceEngine`**: Strips tracking parameters (`utm_*`, `gclid`, `fbclid`, `msclkid`, `ttclid`, `twclid`, `mc_eid`, `igshid`, YouTube `si`) and unwraps bounce-tracking redirects and Google AMP wrappers (`/amp/s/*`).
   - **Brave `resources.json` Surrogate Scripts**: Serves full-fidelity mocks for `adsbygoogle.js`, `gpt.js`, `ima3.js`, `/instream/ad_status.js`, `scorecardresearch.com/beacon.js`, and VAST/VMAP XML payloads so websites and video players never break or trigger anti-adblock walls.
2. **Official YouTube App Background Ad-Blocker & Skipper**:
   - Runs in the background while you watch videos in the official YouTube Android app (`com.google.android.youtube`) or YouTube Music (`com.google.android.apps.youtube.music`).
   - Automatically detects and clicks YouTube's native **Skip Ad** buttons (`skip_ad_button`, `modern_skip_ad_button`, `skip_ad_button_container`) within `80ms`.
   - Automatically mutes device media audio during unskippable ad segments (`ad_progress_text`, `ad_badge`, `ad_attribution`) and restores volume the instant your video resumes.
3. **Brave YouTube `sabr=1` Protobuf Backoff Patch (`brave-yt-sabr-fix.js`)**:
   - Zeroes out `backoffTimeMs` (protobuf varint tag `0x20`) in `*.googlevideo.com/videoplayback` (`sabr=1`) binary responses, rewrites `"adPlacements"` and `"adSlots"` in `/youtubei/v1/player` and `/youtubei/v1/next` payloads, splices out YouTube Shorts ads, and enables background audio playback (`brave-video-bg-play-update.js`).
4. **Silent Over-The-Air (OTA) Auto-Update System**:
   - Automatically checks for new app releases in the background, sends a system Android notification when a newer version is published, and installs the new APK in one tap via `FileProvider`.

---

## How to Publish a New Auto-Update Release

Installed copies of **AdBlock Shield Pro** automatically check [`version.json`](./version.json) in this repository. To push a new version (for example, `V2.0.2`) and trigger an automatic update notification on all installed devices:

1. Replace `AdBlock-Shield.apk` in the repository root with your new signed APK build.
2. Increment `versionCode` and `versionName` in [`version.json`](./version.json):
   ```json
   {
     "versionCode": 202,
     "versionName": "2.0.2",
     "apkUrl": "https://raw.githubusercontent.com/Ayan-Paul-2001/Adblock-Shield-Public-Release/main/AdBlock-Shield.apk",
     "changelog": "Describe your V2.0.2 improvements here."
   }
   ```
3. Commit and push to `main`:
   ```bash
   git add AdBlock-Shield.apk version.json README.md
   git commit -m "Release V2.0.2"
   git push origin main
   ```

---

## Developer

- **Lead Developer & Architect**: **Ayan Paul**
- **Website**: [ayanpaul.me](https://ayanpaul.me)

© 2026 Ayan Paul. All rights reserved.

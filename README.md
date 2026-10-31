# AdBlock Shield Pro — Official Public Release (`V2.0.2`)

<p align="center">
  <img src="app_logo.png" alt="AdBlock Shield Pro Logo" width="140" />
</p>

<p align="center">
  <b>Background System-Wide Android Ad, Tracker, Popunder & YouTube Blocker Powered by Brave Shields Technology</b><br/>
  Compatible with <b>Android 8.0 (Oreo, API 26) through Android 16+</b> • Developed by <a href="https://ayanpaul.me"><b>Ayan Paul</b></a>
</p>

---

## Direct APK Download (`V2.0.2`)

| Package | Version | Build Code | Download Link |
| :--- | :--- | :--- | :--- |
| **AdBlock Shield Pro (Latest Release APK)** | `V2.0.2` | `202` | [**Download `AdBlock-Shield.apk`**](https://raw.githubusercontent.com/Ayan-Paul-2001/Adblock-Shield-Public-Release/main/AdBlock-Shield.apk) |
| **OTA Auto-Update Version Manifest** | `V2.0.2` | `202` | [`version.json`](./version.json) |

---

## What's New in `V2.0.2`

1. **Pure Background System-Wide Brave Engine (`186,000+` Bundled Domain Rules)**:
   - Works strictly in the background across all installed Android apps, games, external browsers (`Chrome`, `Opera`, `UC Browser`, `Phoenix`, `Firefox`, `Samsung Internet`), and the official YouTube app—no in-app WebView/browser required.
   - **4G/5G Carrier & Wi-Fi Router DNS Interception**: Dynamically discovers and routes active 4G/5G SIM carrier DNS servers, Wi-Fi router gateways, and hardcoded public DNS resolvers (`8.8.8.8`, `1.1.1.1`, `9.9.9.9`, `208.67.222.222`) into the local TUN sinkhole so no external browser or app can bypass filtering on mobile data.
   - **Popunder, Betting & Casino Redirect Blocker**: Blocks rotating numbered popunder/casino/betting domains (`krikya11.live`, `krikya*`, `1xbet*`, `melbet*`, `mostbet*`, `baji*`, `jeetbuzz*`, `crickex*`, `babu88*`, `nagad88*`, `adsterra*`, `propellerads*`, `onclkds*`, `realsrv*`, `tsyndicate*`) at both the DNS layer and browser window layer.
   - **Anti-DoH Canary & `HTTPS`/`SVCB` (QTYPE 65/64) Blocking**: Prevents browsers and apps from silently upgrading to encrypted DNS-over-HTTPS (`use-application-dns.net`, `dns.google`, `cloudflare-dns.com`, `doh.opera.com`, `ucdns.ucweb.com`) to bypass ad filtering.
   - **Brave CNAME-Uncloaking Engine**: Inspects DNS `CNAME` chains in real time before delivering responses, blocking disguised first-party subdomains that resolve to third-party trackers.
2. **Official YouTube App Background Ad-Blocker & Skipper (`YouTubeAppAdSkipperService`)**:
   - Runs in the background while you watch videos in the official YouTube Android app (`com.google.android.youtube`) or YouTube Music (`com.google.android.apps.youtube.music`).
   - Automatically detects and clicks YouTube's native **Skip Ad** buttons (`skip_ad_button`, `modern_skip_ad_button`, `skip_ad_button_container`, and Litho `ComponentHost` buttons) using both `ACTION_CLICK` and coordinate-level `dispatchGesture` taps within `50ms`.
   - Automatically mutes device media audio during unskippable ad segments (`ad_progress_text`, `ad_badge`, `ad_attribution`, `"Sponsored"`) and restores volume the instant your video resumes.
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

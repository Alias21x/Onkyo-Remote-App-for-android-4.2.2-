# Onkyo Remote for Galaxy Tab 3 Lite (SM-T110, Android 4.2.2)

Native Android app (Java, no libraries, minSdk 17, landscape). Talks eISCP (TCP 60128) straight to a TX-NR626.

## Build the APK (pick one)

**A. GitHub Actions (no installs, free)**
1. Create a new empty GitHub repository, upload this whole folder (keep `.github/workflows/build.yml`).
2. Open the repo's **Actions** tab, run **Build APK** (it also runs on every push).
3. Download the `OnkyoRemote-apk` artifact, unzip it, you get `app-release.apk`.

**B. Android Studio**
Open this folder, wait for Gradle sync, then Build > Build APK(s) (use the *release* variant for the smallest file).

## Install on the tablet
Copy the APK to the tablet, Settings > Security > Unknown sources ON, open the APK, install.

## First run
1. Receiver: Setup > Network > **Network Standby = On** (needed to power on from the app).
2. Tablet on the same Wi-Fi. Open the app > **SETUP** > **SEARCH**, tap the receiver. Or type its IP and tap **CONNECT**.
3. The IP is remembered and the app reconnects automatically.

## What works / what is a best guess
Verified against a fake receiver (packet framing, discovery, replies, state parsing): power, volume, mute,
input select, listening modes, bass/treble/center/sub, info (IFA/IFV), connection handling.
Taken from the protocol spec and your older app but **untested on a real NR626**: OSD buttons
(Home/Setup/Return/Quick/Audio/Video/arrows), Dimmer, and the **TV tab** (CTV commands - experimental).
Use SETUP > raw command + traffic log to see what the receiver accepts or replies.

Safety: SETUP has a max-volume limit (default 65 of 80) applied to the knob and VOL+.

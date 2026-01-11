---
weight: 1
title: Crashes and Bugs
---

### Setting up ADB

First, download the official **SDK Platform Tools**:
[Download SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools)

#### Windows
1. Download the SDK Platform-Tools for Windows.
2. Extract the ZIP file to a convenient location (e.g., `C:\platform-tools`).
3. Open the folder, verify you see `adb.exe`.
4. Hold `Shift`, right-click in the empty space of the folder, and select **Open PowerShell window here** (or Command Prompt).
5. Type `.\adb devices` to verify your device is connected (commands in PowerShell require `.\` prefix unless added to PATH).

#### Linux
You can often install ADB via your package manager:
- **Arch/Manjaro:** `sudo pacman -S android-tools`
- **Debian/Ubuntu:** `sudo apt install adb fastboot`

Alternatively, download the Linux ZIP from the link above, extract it, and run from the terminal:
```bash
./adb devices
```
*(You may need to add the folder to your PATH or use `./adb` prefix)*.

### Obtaining Logs

Connect your device to your PC and ensure **USB Debugging** is enabled in Developer Options.
To stop logging you can use Ctrl+C to cancel adb logcat.

#### With Root Access
If your device is rooted, you can easily grab specific logs.

**Logcat (System Logs):**
```bash
adb logcat -d > logcat.txt
```

**Dmesg (Kernel Logs):**
Enable adb root in Developer Options, then run:

```bash
adb root
```

```bash
adb shell -c dmesg > dmesg.txt
```

If adb root is not enabled, you can use magisk or kernelsu:
```bash
adb shell su -c dmesg > dmesg.txt
```

#### Without Root
If root access is not available, you cannot view `dmesg` directly. Please generate a full bugreport instead:

```bash
adb bugreport
```
This will generate a zip file containing all system logs.


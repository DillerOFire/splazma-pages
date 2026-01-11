---
weight: 2
title: Oneplus Ace 3v PixelOS
---

## Installation

### Prerequisites

- [Unlocked bootloader](/Unlocking-and-unbricking/)
- PC with ADB and Fastboot installed
- `recovery-pix.img` (PixelOS Recovery)
- `pixelos-latest.zip` (PixelOS ROM zip)

Grab latest ota files at [splazma.site](https://splazma.site)
(RU: just change to [http](http://splazma.site) to avoid cloudflare ban issues)

### Steps

1. **Verify Bootloader Unlock**
   Ensure your device has an unlocked bootloader.

2. **Enter Bootloader Mode**
   Plug your device into your PC and reboot to the bootloader:
   ```bash
   adb reboot bootloader
   ```

3. **Flash Recovery**
   Flash the PixelOS recovery image:
   ```bash
   fastboot flash recovery recovery-pix.img
   ```

4. **Reboot to Recovery**
   Reboot into the newly flashed recovery:
   ```bash
   fastboot reboot recovery
   ```

5. **Format Data**
   On the device, select **Factory Reset** -> **Format data / Factory reset**.

6. **Sideload ROM**
   Select **Apply update** -> **Apply from ADB**, then run on your PC:
   ```bash
   adb sideload pixelos-latest.zip
   ```

7. **Reboot**
   Once finished, go back and select **Reboot system now**.
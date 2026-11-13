# Huawei MateBook D15 2020 (BOHB-WAX9) Hackintosh

OpenCore EFI for the Huawei MateBook D15 2020 (BOHB-WAX9), running macOS Sonoma 14.8.9 (23J631).

I previously used macOS Tahoe on this laptop, but several things weren't working at the time, especially Wi-Fi, Bluetooth and the Everest ESSX8336 audio codec.

I've since moved to Sonoma and managed to get those features working, including AirDrop, without replacing any of the original hardware.

## Hardware

| Component | Specification |
|---|---|
| Model | Huawei MateBook D15 2020 (BOHB-WAX9) |
| CPU | Intel Core i3-10110U @ 2.10 GHz |
| GPU | Intel UHD Graphics (spoofed as Iris Plus Graphics 655) |
| RAM | 8 GB DDR4 |
| Wi-Fi | Intel Wireless-AC 9560 160MHz |
| Audio | Everest ESSX8336 (Intel SST) |
| Bootloader | OpenCore |
| macOS | Sonoma 14.8.9 (23J631) |

## What's Working

- Native Wi-Fi through the macOS Wi-Fi menu, without HeliPort
- Bluetooth
- AirDrop discovery, sending and receiving files
- Internal speakers and headphone output
- Graphics acceleration
- Keyboard, Fn keys and trackpad
- Built-in webcam
- USB ports and HDMI
- Apple Account, iCloud and App Store

All of the above have been tested on my own laptop. Other MateBook D15 configurations may behave differently.

## What's Changed

On my previous Tahoe setup, Wi-Fi required `itlwm` and HeliPort. Bluetooth and AirDrop weren't working, and the internal speakers had no sound.

The audio issue was the hardest part to fix. This laptop uses the Everest ESSX8336 codec with Intel SST, so the usual AppleALC and VoodooHDA methods weren't enough.

On Sonoma, the internal speakers and headphone output now work. Wi-Fi is also recognized natively by macOS, Bluetooth works, and I've tested AirDrop transfers in both directions.

No hardware replacement was needed.

## Performance

For an older dual-core i3 with 8 GB RAM, Sonoma runs surprisingly well. Web browsing, YouTube, music, movies and documents are all comfortable to use.

It's not a performance machine, but it's still perfectly usable for everyday tasks.

## Before Using This EFI

**Generate your own SMBIOS values before booting.**

The shared EFI contains placeholder values. Do not use them as your machine identity.

1. Back up your current EFI.
2. Download [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
3. Generate new values for the SMBIOS model used by this configuration (`MacBookPro15,4`).
4. Open `EFI/OC/config.plist` and update `PlatformInfo -> Generic`.
5. Set your own `SystemSerialNumber`, `MLB`, `SystemUUID` and `ROM`.
6. Test the EFI from a USB drive before replacing your working configuration.

**Compatibility notes:**

- This EFI was tested on macOS Sonoma 14.8.9 (23J631).
- Compatibility with Tahoe or other macOS versions is not guaranteed.
- Some features may depend on system-level patches as well as the EFI.
- Check the installed Kexts and patch requirements before using it.
- Keep a backup of your existing EFI in case you need to roll back.

## Downloads

Check the [Releases](../../releases) page for available EFI builds.

The older Tahoe configuration is kept for reference. The current tested setup is **Sonoma 14.8.9**.

## Disclaimer

This is my personal Hackintosh setup, shared for anyone working on the same laptop. I can't guarantee that everything will work on another machine without changes.

Please back up your EFI before trying it.

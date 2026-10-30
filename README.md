# Custom DMG Dash firmware

Unofficial firmware for the DMG Lumière **Dash** (production batch B4, original firmware 1.0.16),
with a Mac app that installs it over USB. Not made, checked or supported by DMG Lumière or Rosco.
Use at your own risk.

**Download:** [latest release](https://github.com/jfitzgaffer/custom-dmg-dash-firmware/releases/latest)
- `Dash Firmware Updater 1.0.16a.dmg`: the Mac app (Apple silicon and Intel, macOS 12 or newer)
- `Dash_DMX_Profiles.xlsx`: every DMX mode, every channel, every value range
- `dash-firmware-1.0.16a-B4.bin`: the firmware image itself, for people who flash with esptool

## What's new in 1.0.16a (compared with DMG's 1.0.16)

- New DMX modes: 23 RGB 8b, 24 RGB 16b, 25 RGBW 8b, 26 RGBW 16b, 27 CCT RGBW 8b, 28 CCT RGBW 16b.
- Reduced latency when controlled over CRMX.
- Fixed bug where Dash only updated every other DMX frame it received, causing significant steppiness during fades.
- DMX Smoothing now applies to all parameters, not just intensity.
- DMX Smoothing is now consistent: LOW, MEDIUM and HIGH always take 20, 100 and 600 ms. Before, the timing varied with how busy the Dash was.
- Exponential dimming curve now functional.
- If the firmware ever hangs, the Dash restarts itself after 5 seconds instead of staying frozen.
- Settings shows the version as 1.0.16a (the MyMix app still sees 1.0.16).

## Installing with the Mac app

1. Open the disk image and drag **Dash Firmware Updater** into Applications.
2. Open it from Applications. The app isn't from the App Store, so the first time macOS blocks it:
   go to System Settings > Privacy & Security and click **Open Anyway** (macOS 14 or older:
   right-click the app > Open).
3. In the Dash menu set CRMX and Bluetooth to OFF. Switch the light off; the Dash can stay switched
   off, the USB-C cable powers it.
4. Plug the Dash into the Mac, tick the four boxes, click **Check Dash**, then **Install**. It takes
   about two minutes. Don't unplug until the app says it's done.

The app reads the Dash before it changes anything and only updates a Dash it recognises. It writes
only the firmware slot the Dash starts from, checks it afterwards, and never touches the Dash's
settings. **Restore original DMG firmware** puts DMG's 1.0.16 back; set the Dash to a DMX mode
numbered 22 or lower first (the original firmware doesn't have modes 23-28).

## DMX modes

`Dash_DMX_Profiles.xlsx` lists all 15 modes (the 9 original ones and 23-28), what every channel does,
and the value ranges of the control channel, strobe, colour modes, gels, source match and effects,
as the Dash firmware actually decodes them (with notes where that differs from DMG's DMX chart).

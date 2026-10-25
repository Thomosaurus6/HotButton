# HotButton

HotButton is a network-connected, illuminated hardware button for [Bitfocus Companion](https://bitfocus.io/companion). One Ethernet connection supplies power and network communication, while Companion controls the button's actions, LED color, brightness and animation.

**Current release:** 2.0.0

## What HotButton provides

- Direct registration as a Companion control surface.
- A dedicated Companion connection for configuration, actions, feedbacks and variables.
- Automatic pairing after a physical button press or manual connection by IP address.
- Press, Release and configurable Long Press behavior.
- Preset colors, custom RGB colors and timed color transitions.
- Adjustable brightness, LED power control and ten preset flash programs.
- A configurable Custom pulse with separate high/low phases, fades and brightness levels.
- Browser-based network setup, device settings, diagnostics and firmware updates.
- A local overview page for finding multiple HotButtons on the same network.
- DHCP and static IPv4 configuration with a recovery fallback.

## Companion controls

### Actions

| Action | Purpose |
| --- | --- |
| LED Color | Select a preset or custom RGB color, optionally with a timed transition |
| LED Brightness | Set, increase or decrease brightness |
| LED Flash Mode | Select solid output, flash programs 1–10 or Custom |
| LED Flash Custom | Configure high/low phases, fade times and brightness levels |
| LED State | Switch the LED on, off or toggle its current state |
| LED Reset | Return the LED control state to its defaults |

### Feedbacks

HotButton provides feedback for button presses, long presses, device availability, LED state, LED color, brightness and the active flash mode. The Long Press feedback remains active until the physical button is released.

### Variables

Companion variables expose the device name and identity, address, pairing and online status, button state, last event, press timing and current LED values.

## Connection and discovery

Each physical HotButton uses its own Companion connection. Learn mode waits for an intentional button press and then pairs with that device. Manual mode connects to a specified address.

Every unit has an individual local network name. The read-only overview at **hotbutton.local** lists active HotButtons with their names, addresses, Companion targets, firmware versions and most recent button presses. Another active unit automatically takes over the overview if its current host disappears.

The control-surface connection can be enabled or disabled from the browser without disabling the separate Companion connection.

## Network and recovery

HotButton supports DHCP and persistent static IPv4 settings. If DHCP cannot provide an address within 60 seconds, the device uses the recovery address **192.168.1.10/24** so its network settings remain accessible.

Holding the physical button during startup opens the reset window. Releasing it during that window clears saved network and pairing settings. Device identity remains tied to the physical unit.

## Browser interface

The browser interface provides:

- Device and network overview.
- DHCP or static network configuration.
- Device name and local network address.
- Companion target and control-surface switch.
- Status and maximum LED brightness.
- Search-indicator duration.
- LED Override with color picker and RGB values.
- Diagnostics download, restart and firmware update.

## Status indications

| Indication | Meaning |
| --- | --- |
| Red breathing | No usable network address |
| Green fast flash | Network or Companion connection confirmed |
| Violet fast flash | Network recovery fallback active |
| Blue breathing | Checking a saved Companion connection |
| Orange breathing | Pairing or connection recovery available |
| Red fast flash during startup | Reset confirmation |

The blue/orange search indication can switch off after a configurable period while discovery, connection checks and button operation continue in the background.

## Availability

This public repository contains product and user documentation only. Source code, firmware packages, Companion installation packages, schematics, component details, wiring and manufacturing information are not published here.

Distribution through the official Bitfocus Companion module registry can provide the Companion integration without publishing the private development repository.

For operating details, see [HELP.md](HELP.md).


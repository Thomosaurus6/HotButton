# HotButton 2.0.0 — User Guide

HotButton combines a physical illuminated button with Bitfocus Companion. One Companion connection represents one physical HotButton.

## Connection setup

**Learn mode:** Create a HotButton connection in Companion, select Learn and press the physical button. The intentional press pairs that connection with the device.

**Manual mode:** Enter the HotButton's current IP address. Companion validates the responding device before using it.

The connection page displays the device name and links to its individual local address and the shared **hotbutton.local** overview whenever that information is available.

## Startup indications

| State | Indication |
| --- | --- |
| Waiting for a usable network address | Red breathing |
| Network ready | Green fast flash |
| Recovery fallback active | Violet fast flash |
| Checking a saved Companion connection | Blue breathing |
| Waiting for pairing or recovering a connection | Orange breathing |
| Companion connection confirmed | Green fast flash |
| Startup reset confirmed | Red fast flash |

The blue/orange indication has a configurable display period. When it expires, the light turns off while pairing, discovery and physical button events continue normally.

## Control surface

When enabled, HotButton registers directly in Companion as a one-key control surface. Set the Companion address in the browser interface. Disabling the control surface stops surface events immediately and does not disable the separate Companion connection used for LED control and monitoring.

## Browser settings

The browser interface provides network configuration and device information on its main page. The Settings page provides:

- Device name and restoration of the original generated name.
- Control-surface enable switch.
- Status brightness and maximum LED brightness.
- Connection-search indication duration.
- LED Override with color picker, RGB values and brightness.
- Restart, diagnostics and firmware update.

LED Override is intended for testing and color selection. While enabled, it masks Companion's visible LED output without replacing Companion's stored LED state.

## Network and recovery

DHCP is used by default. Static IPv4 configuration is stored on the device. If DHCP does not provide an address within 60 seconds, HotButton uses **192.168.1.10/24** as a recovery address.

To clear saved network and pairing settings, hold the physical button while powering the device and release it during the red reset-confirmation indication. The device then restarts with DHCP.

Local names depend on multicast name resolution in the network and computer. If a local name is temporarily unavailable, use the current IP address.

## Device overview

The read-only overview at **hotbutton.local** shows active devices, individual local addresses, IP addresses, Companion targets, firmware versions and Last Press times. Device names link to their individual browser pages.

One active HotButton hosts the overview. If that unit disappears, another unit takes over automatically after a short timeout. Browser, router or operating-system caches can briefly delay the change.

## Companion actions

| Action | Behavior |
| --- | --- |
| LED Color | Select a named or custom RGB color; an optional duration fades from the current color |
| LED Brightness | Set, increase or decrease the shared LED brightness |
| LED Flash Mode | Off selects solid output; programs 1–10 provide increasing flash speeds; Custom resumes the current custom pulse |
| LED Flash Custom | Set high/low phase durations, fade-in/fade-out durations and minimum/maximum brightness |
| LED State | On, Off or Toggle without discarding the selected color or animation |
| LED Reset | Reset color, brightness, flash mode and LED power |

Color, brightness, flash mode and LED power are separate controls. Set the parameters required by the intended Companion action.

## Custom pulse

A Custom pulse moves between its minimum brightness and the current LED brightness. If the current brightness is below the configured minimum, both effective levels become equal and the pulse appears paused.

High and Low Phase durations include their respective fades. A new Custom configuration replaces the active pulse parameters for the current session. After a restart, the device returns to its built-in Custom defaults until Companion sends another configuration.

## Feedbacks and Long Press

Feedbacks are available for:

- Button press pulse.
- Long Press event.
- Device online state.
- LED state and color.
- LED brightness.
- Active flash mode, including Custom.

A normal Press occurs immediately. Long Press is an additional event and remains active until Release, readying it for the next long press. Companion's online timeout determines how quickly an unavailable device is reported offline.

## Variables

Variables provide the current device information, address, pairing state, online state, button state, last button event, press duration, interval between presses and current LED state.

## Updates and diagnostics

Firmware updates are installed through the device browser. Keep power and network connected until verification and installation finish. The diagnostics download contains the operating information needed to investigate network, pairing, surface or LED-control problems.


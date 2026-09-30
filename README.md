![Banner](Bloopair.png?raw=true)
# Bloopair
Bloopair allows connecting controllers from other consoles like native Wii U Pro Controllers on the Wii U.  
It temporarily applies patches to the IOS-PAD module responsible for Bluetooth controller connections.

> For this fork's Switch Pro support in GameCube games, follow [Switch Pro in Nintendont](#switch-pro-in-nintendont). It requires the companion Nintendont fork as well as this Bloopair build.

## Features
- Connect up to 7 controllers wirelessly via Bluetooth
- Rumble support
- Battery levels
- Button and stick remapping (only for Bloopair controllers)

## Supported controllers
- Nintendo Switch Pro Controller
- Nintendo Switch Joy-Con
- Nintendo Switch Online SNES / N64 Controller
- Microsoft Xbox One S/X Controller  
Note: The latest firmware versions and all Series S/X Controllers are currently not supported due to missing Bluetooth LE support.
- Sony DualShock 3 Controller  
To pair a DualShock 3 to the console, see the [Pairing a DualShock 3](#pairing-a-dualshock-3) section.
- Sony DualShock 4 Controller
- Sony DualSense Controller

## Installation
- Download and extract the latest .zip from the [releases page](https://github.com/GaryOderNichts/Bloopair/releases).
- Copy the `30_bloopair.rpx` from the .zip file to the `modules/setup/` folder of your target environment on the SD Card.  
  This would be `wiiu/environments/aroma/modules/setup/` for Aroma.
- Copy the `wiiu` folder from the .zip and copy it to the root of your SD Card.  
  If you're using aroma you can delete the `Koopair.rpx` in the `wiiu/apps` folder and use the .wuhb instead.

Make sure you're using Aroma or Tiramisu. Follow https://wiiu.hacks.guide/#/ to setup Aroma.

## Usage
- Once you're booted into Aroma or Tiramisu and are in the Wii U menu, press the SYNC button on your console and controller.
- Wait until the Controller is connected.

If a controller had been paired in the past, simply turn it on again and it should reconnect.

### Switch Pro in Nintendont

This fork lets original **Nintendo Switch 1 Pro Controllers** paired on a Wii U
reconnect wirelessly in GameCube games through the companion Nintendont fork.
It requires **Aroma**, an SD card left in the Wii U, and both matching fork
builds. It does not add Nintendont support for Switch 2 Pro Controllers,
Joy-Con or third-party Switch controllers. Other controllers remain usable in
Bloopair and do not consume an export slot.

#### Download the matching prereleases

The hardware-tested source pair is:

| Component | Tested commit | Draft prerelease |
| --- | --- | --- |
| Bloopair, sync plugin and Koopair | `479479b` | [`switch-pro-nintendont-v0.1.0-rc1`](https://github.com/GerwinVerkerk/Bloopair/releases/tag/switch-pro-nintendont-v0.1.0-rc1) |
| Nintendont | `889420e` | [`switch-pro-bloopair-v0.1.0-rc1`](https://github.com/GerwinVerkerk/Nintendont/releases/tag/switch-pro-bloopair-v0.1.0-rc1) |

These releases are currently **drafts**. Their downloads are not publicly
available until the fork maintainer publishes them. Do not mix either package
with an upstream release or a different fork build.

#### Install on the SD card

Back up existing files, then extract both installation ZIPs to the root of the
same SD card. The resulting paths must be:

| File | Destination |
| --- | --- |
| `30_bloopair.rpx` | `sd:/wiiu/environments/aroma/modules/setup/30_bloopair.rpx` |
| `bloopair_nintendont_sync.wps` | `sd:/wiiu/environments/aroma/plugins/bloopair_nintendont_sync.wps` |
| `Koopair.wuhb` | `sd:/wiiu/apps/Koopair/Koopair.wuhb` |
| Nintendont `boot.dol` | `sd:/apps/Nintendont/boot.dol` |
| Nintendont `meta.xml` and `icon.png` | `sd:/apps/Nintendont/` |

Do not leave a second active copy of the module or plugin under another name.
Fully restart the Wii U after installation so Aroma loads the new components.

#### Pair and play

1. In the Wii U menu, pair each original Switch 1 Pro Controller normally with
   the console and controller SYNC buttons. Existing working pairings can stay.
2. Start vWii/Nintendont and a GameCube game. If using another loader, verify
   that it starts `sd:/apps/Nintendont/boot.dol` from this fork.
3. In the game, press **A** on each Switch Pro to reconnect.

No Manual export, file copy or controller setting is required. The Aroma plugin
automatically maintains `sd:/wiiu/bloopair/nintendont-switch-pro.bin`, and
Nintendont reads that file when it starts. Keep the SD card inserted. The file
contains Bluetooth authentication keys and must not be shared.

Up to four supported pairings can be exported. Player LEDs follow the assigned
GameCube channel: player 1 lights LED 1, player 2 lights LEDs 1+2, player 3
lights 1+2+3, and player 4 lights all four. A physical GameCube controller can
take an earlier channel and move the Bluetooth controllers to later channels.

#### Troubleshooting

- Confirm that each Switch Pro works in the Wii U menu first.
- Verify all five installation paths, that the sync plugin is enabled, and that
  the SD card is writable; then fully restart the Wii U.
- Confirm that the game launcher uses this fork's Nintendont `boot.dol`.
- Return to Wii U mode, reconnect the controller there, then start Nintendont
  again. Nintendont reads the handoff only at startup.
- Never publish the handoff file or use Manual export for this integration.

The cleaned builds were hardware-tested with two simultaneous Switch Pro
Controllers in Mario Kart: Double Dash!!, a searching PowerA in different
activation orders, correct player LEDs and input, and reassignment when a
physical GameCube controller takes adapter port 1. Four simultaneous Switch Pro
Controllers were not tested.

This is a fork-specific integration. Compatibility with Bloopair's announced
upstream SD pairing storage has not yet been established. The automatic route
requires Aroma on Wii U; it is not available on Tiramisu or an original Wii.

## Koopair
Koopair is the Bloopair companion app which comes with Bloopair.  

<img src="https://i.imgur.com/w4CaDXL.png" width="23%"></img> <img src="https://i.imgur.com/ugzZorg.png" width="23%"></img> <img src="https://i.imgur.com/Zf3XoBZ.png" width="23%"></img> <img src="https://i.imgur.com/VUnR3S8.png" width="23%"></img>
<img src="https://i.imgur.com/E4CqggT.png" width="23%"></img> <img src="https://i.imgur.com/eaych2U.png" width="23%"></img> <img src="https://i.imgur.com/CFLP3WL.png" width="23%"></img> <img src="https://i.imgur.com/7GbLf2P.png" width="23%"></img>

Koopair supports:
- Testing connected controllers
- Creating mappings for buttons and sticks
- Editing controller options
- Managing configuration files
- Pairing DualShock 3 controllers

## Pairing a DualShock 3
The DualShock 3 needs to be paired using a USB cable. After the initial pairing it can be used like any other wireless Bluetooth controller.  
- Open Koopair from the Wii U menu or Homebrew Launcher. Now open the "Controller Pairing" option on the menu.
- Connect the DualShock 3 using a USB cable to the front or back ports of the console.
- The screen will say "Successfully paired controller!" once the controller has been successfully paired.  
You can now remove the USB cable from the controller. Press the PS button to connect it to the console.
- Press the HOME button to exit.

The DualShock 3 is now ready to use with the console.

## FAQ / Troubleshooting

**My controller doesn't pair to the console**  
Make sure Bloopair is running and both the console and the controller are in SYNC mode.  
Also make sure the controller is on the supported list.  
Wait for about a minute, and if nothing happens restart your console and redo the process.  
You can also try [clearing controller syncs](https://en-americas-support.nintendo.com/app/answers/detail/a_id/1705/~/how-to-clear-all-syncs).

**Will you add support for controller xyz?**  
Possibly, I've for now added support for all the controllers I currently own. Maybe I can get a few more controllers which I could add support for.  
Pull requests for different controllers are always welcome.

**Where are configuration files stored?**
Bloopair loads configuration files from the `wiiu/bloopair` folder on your SD Card.  
This means configurations work across multiple environments.

## To-Do
- Support more controllers
- Bluetooth LE support (Unlikely, only partially supported by the Bluetooth Stack)

## How it works
Bloopair will patch the IOSU's IOS-PAD module in memory. It will make sure any bluetooth peripheral can be paired to the console.  
Once paired and connected it will convert received HID reports to the Pro Controller HID report format, which padscore expects.

## Project structure
```
Bloopair
├── dist            - Used for creating distributable packages.
├── ios             - Bloopair IOSU patches.
│   ├── ios_kernel  - Kernel patches used for setting up Bloopair.
│   ├── ios_pad     - Core Bloopair patches.
│   └── ios_usb     - Patches used to recover from IOS exploit done by loader.
├── koopair         - Bloopair companion app.
├── libbloopair     - Library to communicate with Bloopair IPC.
├── loader          - Setup module which loads Bloopair.
├── nintendont_sync - Aroma plugin that maintains Nintendont pairings.
└── third_party     - Third-party content included in Bloopair.
```

## Building
The reproducible Docker build installs Wii U Plugin System from a pinned
artifact image. Alternatively install devkitPPC, devkitARM, wut and WUPS.

**Koopair dependencies**  
Koopair additionally requires the following packages:
- wiiu-sdl2
- wiiu-sdl2_gfx
- wiiu-sdl2_ttf
- wiiu-sdl2_image

Run `make`.

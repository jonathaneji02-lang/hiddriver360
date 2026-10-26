# HidDriver 360
Experimental on-console HID driver focussing on providing third party, non xinput controller support to the xbox 360 without dongles.

## What works
- Supports both 17559 retail and 17489 devkit dashboards
- Reading controller input via USB
- Up to 4 concurrent controllers, in combination with original xbox 360 controllers or without them
- Controllers are registered inside xam and therefore fully recognized in the entire xbox 360 user interface, ring of light will update accordingly, no original controllers are needed etc
- The controller works in all tested games
- **(fork)** Hold **L1 + R1** for 0.5s on any connected controller to show the connection status of every slot as on-screen notifications (`Slot 1: DualShock 4 - connected (Player 1)`, `Connected controllers: 2/4`). Controllers the driver has seen but that failed to register inside xam are registered again at the same time. The notification texts are in Portuguese.

## Current limitations
- no rumble support
- **(fork)** The L1 + R1 status combo is untested on real hardware. It can only report controllers that reached the driver, a controller that never enumerated over USB will not show up
- **(fork)** Controller initialisation state is global, so two controllers enumerating at the exact same moment can interfere with each other. Plugging them in one at a time is safer

## Supported controllers
- DualShock 4 (PS4 controller)
- DualShock 4 Wireless Adapter (CUH-ZWA1E)
- DualSense (PS5 controller)
- DualSense Edge
- DualShock 3
- Nintendo Switch Pro controller
- Any USB HID compliant controller thanks to built in mapping assistant :) (this excludes modern xbox controllers like xbox one and xbox series because microsoft made them GIP only)

## How to use
1. load plugin (either at runtime or at boot via your launch.ini)
2. Connect controllers via USB
3. Controllers with a built in mapping will start working right away, for all other controllers that are USB HID compliant a mapping assistant will be started that guides you through the process of mapping your controller
4. hold L1 + R1 at any time to check which controllers are connected (fork only)
5. enjoy :)

## How to build
1. Acquire the official Xbox 360 SDK using black magic
2. Install visual studio 2010 ultimate and visual studio 2019
3. Install the sdk using the "FULL" preset
4. Open the solution in visual studio 2019 and build
5. Hopefully enjoy :)

## Showcase
https://github.com/user-attachments/assets/f090e5f4-538d-457f-8189-2c5b98579984


## Attributions
- [EinTim23](https://github.com/EinTim23/) for Reverse engineering the xbox 360s HID and controller implementation and implementing this driver
- [localcc](https://github.com/localcc/) for providing help about low level USB related questions and beaming the idea of doing this into my head
- [Rapidjson](https://github.com/Tencent/rapidjson/) JSON library used to save/load user defined mappings
- [Lufa](https://github.com/abcminiuser/lufa) HID report descriptor parser implementation used in hiddriver360 is derived from their implementation
- [iMoD1998](https://github.com/iMoD1998) Creating the Detours library used in hiddriver360

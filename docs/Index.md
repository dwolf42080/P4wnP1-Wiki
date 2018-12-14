# Official P4wnP1 A.L.O.A Wiki

This is the **Official** Wiki for the [P4wnP1 A.L.O.A](https://github.com/mame82/p4wnp1_aloa) Framework by [@MaMe82](https://twitter.com/mame82).  
The Wiki is maintained by [@Swiftb0y_DE](https://twitter.com/swiftb0y_de)  
Head over to [Quickstart](Quickstart.md) to get started.


## Feature Comparision


| Feature                                                                         | BashBunny                                                                                             | P4wnP1 (Legacy)                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | P4wnP1 A.L.O.A                                                                                                                                                   |
|:--------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RNDIS, CDC ECM, HID , serial and Mass storage support                           | supported, usable in several combinations, Windows Class driver support (Plug and Play) in most modes | supported, usable in most combinations, Windows Class driver support (Plug and Play) in all modes as composite device                                                                                                                                                                                                                                                                                                                                                                       | supported, usable in most combinations, Windows Class driver support (Plug and Play) in all modes as composite device                                            |
| Target to device communication on covert HID channel                            | no                                                                                                    | Raw HID device allows communication with Windows Targets (PowerShell 2.0+ present) via raw HID<br>There's a full automated payload, allowing to access P4wnP1 bash via a custom PowerShell console from target device (see 'hid_frontdoor.txt' payload).<br>An additional payload based on this technique, allows to expose a backdoor session to P4wnP1 via HID covert channel and relaying it via WiFi/Bluetooth to any SSH capable device (bridging airgaps, payload 'hid_backdoor.txt') | Currently WIP (14.12.2018)                                                                                                                                       |
| Mouse emulation                                                                 | no                                                                                                    | Supported: relative Mouse positioning (most OS, including Android) + ABSOLUTE mouse positioning (Windows); dedicated scripting language "MouseScript" to control the Mouse, MouseScripts on-demand from HID backdoor shell                                                                                                                                                                                                                                                                  | Supported: relative Mouse positioning (most OS, including Android) + ABSOLUTE mouse positioning (Windows); Scripting complex behavior via HIDScript (Javascript) |
| Trigger payloads via target keyboard                                            | No                                                                                                    | Hardware based: LEDs for CAPSLOCK/SCROLLLOCK and NUMLOCK are read back and used to branch or trigger payloads (see hid_keyboard2.txt payload)                                                                                                                                                                                                                                                                                                                                               | Hardware based: LEDs for CAPSLOCK/SCROLLLOCK and NUMLOCK are read back and used to branch or trigger payloads                                                    |
| Interactive DuckyScript execution                                               | Not supported                                                                                         | supported, HID backdoor could be used to fire scripts on-demand (via WiFi, Bluetooth or from Internet using the HID remote backdoor)                                                                                                                                                                                                                                                                                                                                                        | Not Yet (14.12.2018)                                                                                                                                             |
| USB configuration changable during runtime                                      | supported                                                                                             | will maybe be implemented                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | supported                                                                                                                                                        |
| Support for RubberDucky payloads                                                | supported                                                                                             | supported                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Not Yet (14.12.2018)                                                                                                                                             |
| Support for piping command output to HID keyboard out                           | no                                                                                                    | supported                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Not confirmed yet by @mame82                                                                                                                                     |
| Switchable payloads                                                             | Hardware switch                                                                                       | manually in interactive mode (Hardware switch could be soldered, script support is a low priority ToDo. At least till somebody prints a housing for the Pi which has such a switch and PIN connectors)                                                                                                                                                                                                                                                                                      | supported. Individual Templates, Payloads, Configurations, etc can be deployed based on GPIO Pin states (requires a manually soldered switch)                    |
| Interactive Login with display out                                              | SSH / serial                                                                                          | SSH / serial / stand-alone (USB OTG + HDMI)                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Web UI / SSH / (serial & Standalone not confirmed)                                                                                                               |
| Performance                                                                     | High performance ARM quad core CPU, SSD Flash                                                         | Low performance single core ARM CPU, SDCARD                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Low performance single core ARM CPU, SDCARD                                                                                                                      |
| Network interface bitrate                                                       | Windows RNDIS: 2 GBit/s<br>Linux/MacOS ECM: 100 MBit/s<br>Real bitrate 450 MBit max (USB 2.0)         | Windows RNDIS: 20 GBit/s<br>Linux/MacOS ECM: 4 GBit/s (detected as 1 GBit/s interface on MacOS)<br>Real bitrate 450 MBit max (USB 2.0)<br>Here's the needed P4wnP1 patch                                                                                                                                                                                                                                                                                                                    | Windows RNDIS: 20 Gbit/s (not confirmed)<br>Linux/MacOS ECM: 4 GBit/s (detected as 1 GBit/s interface on MacOS)<br>Real bitrate 450 MBit max (USB 2.0)           |
| LED indicator                                                                   | RGB Led, driven by single payload command                                                             | mono color LED, driven by a single payload command                                                                                                                                                                                                                                                                                                                                                                                                                                          | mono color LED                                                                                                                                                   |
| Customization                                                                   | Debian based OS with package manager                                                                  | Debian based OS with package manager                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Kali Linux with package manager and custom kernel                                                                                                                |
| External network access via WLAN (relay attacks, MitM attacks, airgap bridging) | Not possible, no external interface                                                                   | supported with Pi Zero W                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | supported                                                                                                                                                        |
| SSH access via Bluetooth                                                        | not possible                                                                                          | supported (Pi Zero W)                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | supported                                                                                                                                                        |
| Connect to existing WiFi networks (headless)                                    | not possible                                                                                          | supported (Pi Zero W)                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | supported                                                                                                                                                        |
| Shell access via Internet                                                       | not possible                                                                                          | supported (WiFi client connection + SSH remote port forwarding to SSH server owned by the pentester via AutoSSH)                                                                                                                                                                                                                                                                                                                                                                            | supported (WiFi client connection + SSH remote port forwarding to SSH server owned by the pentester via AutoSSH) (not confirmed)                                 |
| Ease of use                                                                     | Easy, change payloads based on USB drive, simple bash based scripting language                        | Medium, bash based event driven payloads, inline commands for HID (DuckyScript and ASCII keyboard printing, as well as LED control)                                                                                                                                                                                                                                                                                                                                                         | Easiest, custom mobile friendly Web UI. Advanced Scripting via Javascript, Bash and custom Event system                                                          |
| Available payloads                                                              | Fast growing github repo (big community)                                                              | Slowly growing github repo (spare time one man show ;-)) Edit: Growing community, but no payload contributions so far                                                                                                                                                                                                                                                                                                                                                                       | Slowly growing community, but no payload contributions so far                                                                                                    |
| In one sentence ...                                                             | "World's most advanced USB attack platform."                                                          | A open source project for the pentesting and red teaming community.                                                                                                                                                                                                                                                                                                                                                                                                                         | A open source project for the pentesting and red teaming community.                                                                                              |
| Total Costs of Ownership                                                        | about 99 USD                                                                                          | about 5 USD (11 USD fow WLAN capability with Pi Zero W)                                                                                                                                                                                                                                                                                                                                                                                                                                     | About 11USD (Pi Zero W ONLY!)                                                                                                                                    |
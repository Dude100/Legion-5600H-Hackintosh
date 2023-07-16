# macOS on Lenovo Legion 5-15ACH6A - Ryzen 5600H & Radeon RX 6600m

Lenovo Legion 5-15ACH6A Type 82NW Opencore EFI and some info for running macOS Ventura.

![screen1](https://github.com/kalkmann/Legion-5600H-Hackintosh/assets/8891448/3b6a0492-2835-4231-bf29-ccf1c918bde5)

## Considerations

_Information available only for possible references. I do not recommend following all the information presented here._

## Table of Contents

*   [Specifications](#specifications)
*   [What's Working](#whats-working)
*   [What's not Working](#whats-not-working)
*   [Bios Options](#bios-options)
*   [UMAF Tool - Disable XHC1](#umaf-tool---disable-xhc1)
*   [Kexts Used](#kexts-used)
*   [SSDTs Used](#ssdts-used)
*   [Credits](#credits)
*   [Screenshots](#screenshots)

## Specifications

<table>
	<tbody>
		<tr>
			<td>Model</td>
			<td>Legion 5-15ACH6A Type 82NW</td>
		</tr>
		<tr>
			<td>CPU</td>
			<td>AMD Ryzen&trade; 5 5600H Processor</td>
		</tr>
		<tr>
			<td>DGPU</td>
			<td>AMD Radeon RX 6600M 8GB</td>
		</tr>
		<tr>
			<td>RAM</td>
			<td>2x 16GB Kingston DDR4 2400 MHz</td>
		</tr>
		<tr>
			<td>NVMe</td>
			<td>Kingston SNV2S1000G 1TB for macOS / Micron MTFDHBA512QFD 512gb for Windows 11</td>
		</tr>
		<tr>
			<td>WIFI</td>
			<td>Intel&reg; Wi-Fi 6E AX210</td>
		</tr>
		<tr>
			<td>Bluetooth</td>
			<td>Orico USB Dongle (chip CSR8510)</td>
		</tr>
		<tr>
			<td>Ethernet</td>
			<td>Realtek RTL8111</td>
		</tr>
		<tr>
			<td>Audio</td>
			<td>Realtek ALC287</td>
		</tr>
		<tr>
			<td>LCD Panel</td>
			<td>15.6 FHD IPS 120Hz</td>
		</tr>
		<tr>
			<td>Bios Version</td>
			<td>G9CN32WW</td>
		</tr>
		<tr>
			<td>Opencore Version</td>
			<td>0.9.3</td>
		</tr>
		<tr>
			<td>SMBIOS used</td>
			<td>MacBookPro16,3 (Need to enter your information generated by <a href="You need to enter your information generated by the">GenSMBIOS</a>)</td>
		</tr>
		<tr>
			<td>Target MacOS Version</td>
			<td>MacOS Ventura&nbsp;13.4.1</td>
		</tr>
	</tbody>
</table>


## What's Working

| Item | Status | Notes |
| --- | --- | --- |
| CPU | ✅ | AMD Vanilla Kernel Patches ([Modify according to yours Core Count](https://github.com/AMD-OSX/AMD_Vanilla)) |
| DGPU | ✅ | With some DeviceProperties |
| Brightness Control | ✅ | With Lunar app |
| HDMI A/V out | ✅ |   |
| USB | ✅ | Only rear ports - [XHC1 controller disabled](#umaf-tool---disable-xhc1) |
| Keyboard | ✅ | Voodoops2controller Kext + Karabiner-Elements app for mapping |
| Audio | ✅ | AppleALC kext working with layout-id 21 |
| Trackpad | ✅ | VoodooI2C |
| Ethernet | ✅ | RealtekRTL8111 Kext |
| Intel WIFI | ✅ | AirportItlwm Kext |
| Bluetooth | ✅ | External USB Dongle - BlueToolFixup Kext |
| Battery | ✅ | VoodooBatteryStatus Kext |
| AppleTV+ DRM | ✅ | Work with CFG_LINK_FIXED_MAP=1 |
| iServices | ✅ | Message/Facetime tested and working |
| Shutdown/Reboot | ✅ |   |

## What's not Working

| Item | Status | Notes |
| --- | --- | --- |
| [XHC1 USB Controller](#umaf-tool---disable-xhc1) | ❓ | For some reason, with both controllers activated, random freezes occurs. Only XHC0 enabled (rear ports): 3 3.2 USB-A + 1 3.2 USB-C |
| Sleep | ❓ | DGPU's powerplay + TSC issues |

## Bios Options

*   **Only Discrete** GPU
*   Device Guard **Disabled**
*   Secure Boot **Disabled**

## UMAF Tool - Disable XHC1

Read [Disclaimer](https://github.com/DavidS95/Smokeless_UMAF) and download [UniversalAMDFormBrowser](https://github.com/DavidS95/Smokeless_UMAF/blob/main/UniversalAMDFormBrowser.zip)

1.  Format a pendrive in **FAT32** and copy content to root
2.  **Boot** from **pendrive** 
3.  Navigate to **Device Properties** > **AMD CBS** > **FCH Common Options** > **USB Configuration Options** > **XHCI1 Controller Enable**: Change to **Disabled**
4.  **Esc** to back and press **Y** when prompted to save, Esc to back, then **Reset** on first menu (not continue)

![](https://user-images.githubusercontent.com/8891448/226887440-8712f449-cc25-43e4-9fb4-1afac1c74b54.gif)

## Kexts Used

| Kext | Description |
| --- | --- |
| [AirportItlwm.kext](https://github.com/OpenIntelWireless) | Adds Intel WIFI support |
| [AMDRyzenCPUPowerManagement.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [AppleALC.kext](https://github.com/acidanthera/AppleALC) | Native macOS HD audio for not officially supported codecs |
| [AppleMCEReporterDisabler.kext](https://files.amd-osx.com/AppleMCEReporterDisabler.kext.zip) | Disables AppleIntelMCEReporter which causes panics on AMD CPUs |
| [BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM) | Patches Bluetooth stack to allow non-Apple Bluetooth |
| [Lilu.kext](https://github.com/acidanthera/Lilu) | Platform for arbitrary kext, library, and program patching throughout the system |
| [NVMeFix.kext](https://github.com/acidanthera/NVMeFix) | Improve compatibility with non-Apple SSDs |
| [RadeonSensor.kext](https://github.com/aluveitie/RadeonSensor) | GPU temperature |
| [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X) | Open source driver for the Realtek RTL8111/8168 family |
| [RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents) | Blocking unwanted processes causing compatibility issues on different hardware and unlocking the support for certain features restricted to other hardware |
| [SMCAMDProcessor.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [SMCBatteryManager.kext](https://github.com/acidanthera/VirtualSMC) | Enables battery readings |
| [USBToolBox.kext](https://github.com/USBToolBox/kext) | Common actions for USB mapping easier |
| [UTBMap.kext](https://github.com/USBToolBox/tool) | USB Map performed with the USBToolbox tool on Windows 11 |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) | Advanced Apple SMC emulator in the kernel |
| [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2) | Fixes keyboard |
| [VoodooI2C.kext & VoodooU2CHID.kext](https://github.com/VoodooI2C) | Fixes trackpad |


## SSDTs Used

Done with [SSDTTime](https://github.com/corpnewt/SSDTTime) in Windows 11

| Table | Description |
| --- | --- |
| [SSDT-EC](https://github.com/corpnewt/SSDTTime) | Adds a fake Embedded Controller device |
| [SSDT-PLUG-ALT](https://github.com/corpnewt/SSDTTime) | Fixes CPU definitions |
| [SSDT-USBX](https://github.com/corpnewt/SSDTTime) | Enables USB Power Management |
| [SSDT-XOSI](https://github.com/corpnewt/SSDTTime) | Spoof macOS to Windows for some ACPI features |

## Credits

*   [AMD-OSX](https://forum.amd-osx.com/) Forum and the [dedicated Thread](https://forum.amd-osx.com/threads/amd-rayon-r7-5800h-install-monterey-kernel-panic.2725) users.
*   ExtremeXT for help, corrections, my [first EFI](https://github.com/ExtremeXT/Lenovo_Legion_5_Hackintosh) reference, the original concept of disable one USB Controller AND README informations.
*   Telegram Noot group members for mention UMAF tool.
*   zxc2689963 for EFI references.
*   [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) for the guides.
*   [DavidS95](https://github.com/DavidS95) for [UMAF](https://github.com/DavidS95/Smokeless_UMAF).
*   [Apple](https://www.apple.com/) for macOS.
*   [Acidanthera](https://github.com/acidanthera) for OpenCore and most Kexts.
*   Anyone else that helped to develop and improve hackintoshing.

## Screenshots

![screen2](https://github.com/kalkmann/Legion-5600H-Hackintosh/assets/8891448/0340a459-ccde-4dab-ae11-848c5fc8acb7)

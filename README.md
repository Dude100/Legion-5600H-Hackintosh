# macOS on Lenovo Legion 5-15ACH6A - Ryzen 5600H & Radeon RX 6600M 🇧🇷

Lenovo Legion 5-15ACH6A Type 82NW Opencore EFI and some info for running macOS Sonoma.

![Static Badge](https://img.shields.io/badge/Bios_Version-GKCN36WW-blue?logo=lenovo&logoColor=%23fff) ![Static Badge](https://img.shields.io/badge/Opencore_Version-0.9.8-black) ![Static Badge](https://img.shields.io/badge/MacOS_Version-Sonoma%2014.2-green?logo=apple&logoColor=%23fff)

![print-oc096](https://github.com/kalkmann/Legion-5600H-Hackintosh/assets/8891448/03994a13-7373-4073-98da-f48412df28c3)

![Sleep-Wake](https://github.com/kalkmann/Legion-5600H-Hackintosh/assets/8891448/f51cd1f4-225c-4b58-968e-bda1becc2b02)

## Considerations

_Information available only for possible references. I do not recommend following all the information presented here._

## Table of Contents

*   [Specifications](#specifications)
*   [What's Working](#whats-working)
*   [What's not Working](#whats-not-working)
*   [Bios Options](#bios-options)
*   [Kexts Used](#kexts-used)
*   [SSDTs Used](#ssdts-used)
*   [Credits](#credits)
*   [Screenshots](#screenshots)

## Specifications

| Item  | Info  |
| ------------ | ------------ |
| Model  | Legion 5-15ACH6A Type 82NW  |
| Bios Version  | G9CN36WW  |
| CPU  |  AMD Ryzen™ 5 5600H Processor |
|  DGPU | AMD Radeon RX 6600M 8GB  |
| RAM  | 2x 16GB Kingston DDR4 2400/3200 MHz  |
| NVMe  | Kingston SNV2S1000G 1TB for macOS / Micron MTFDHBA512QFD 512gb for Windows 11  |
| WIFI  | Intel® Wi-Fi 6E AX210  |
| Bluetooth  | With Intel wifi combo card  |
| Ethernet  | Realtek RTL8111  |
| Audio  | Realtek ALC287  |
| LCD Panel  | 15.6 FHD IPS 120Hz  |
| Opencore Version  | 0.9.8  |
| SMBIOS used  | MacBookPro16,3 (Need to enter your information generated by [GenSMBIOS](http://https://github.com/corpnewt/GenSMBIOS "GenSMBIOS"))  |
| Target MacOS Version  | macOS Sonoma 14.2  |

## What's Working

| Item | Status | Notes |
| --- | --- | --- |
| CPU | ✅ | AMD Vanilla Kernel Patches ([Modify according to yours Core Count](https://github.com/AMD-OSX/AMD_Vanilla)) |
| DGPU | ✅ | With some DeviceProperties |
| Brightness Control | ✅ | With [Lunar app](https://lunar.fyi/ "Lunar app") |
| HDMI A/V out | ✅ |   |
| USB | ✅ | All ports working with **[GUX-RyzenXHCIFix](https://github.com/RattletraPM/GUX-RyzenXHCIFix "GUX-RyzenXHCIFix")** / [USBMap](https://github.com/corpnewt/USBMap "USBMap")|
| Keyboard | ✅ | Voodoops2controller Kext + [Karabiner-Elements app](https://karabiner-elements.pqrs.org/ "Karabiner-Elements app") for mapping |
| Audio | ✅ | AppleALC kext working with layout-id 21 |
| P2 Mic | ✅ | Working with AppleALC 1.8.8 |
| Trackpad | ✅ | VoodooI2C |
| Ethernet | ✅ | RealtekRTL8111 Kext |
| Intel WIFI | ✅ | AirportItlwm Sonoma Alpha Kext |
| Bluetooth | ✅ | From Intel AX210 with IntelBluetoothFirmware.kext + BlueToolFixup Kext |
| Battery | ✅ | VoodooBatteryStatus Kext |
| AppleTV+ DRM | ✅ | Work with CFG_LINK_FIXED_MAP=1 |
| iServices | ✅ | Message/Facetime tested and working |
| Shutdown/Reboot | ✅ |   |
| Sleep/Wake | ✅ | Finally working with Seey6 [CpuTscSync](https://github.com/Seey6/CpuTscSync "CpuTscSync") and SSDT for USB |

## What's not Working

| Item | Status | Notes |
| --- | --- | --- |
| ❓ |  |   |

## Bios Options

*   **Only Discrete** GPU
*   Device Guard **Disabled**
*   Secure Boot **Disabled**

## Kexts Used

| Kext | Description |
| --- | --- |
| [AirportItlwm.kext](https://github.com/OpenIntelWireless) | Adds Intel WIFI support |
| [AMDRyzenCPUPowerManagement.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [AppleALC.kext](https://github.com/acidanthera/AppleALC) | Native macOS HD audio for not officially supported codecs |
| [AppleMCEReporterDisabler.kext](https://files.amd-osx.com/AppleMCEReporterDisabler.kext.zip) | Disables AppleIntelMCEReporter which causes panics on AMD CPUs |
| [CpuTscSync](https://github.com/Seey6/CpuTscSync "CpuTscSync") | It is a Lilu plugin, modify from CpuTscSync. It should solve some wake issues for AMD Mobile |
| [IntelBTPatcher.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | Intel Bluetooth Kernel Extensions for macOS |
| [IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | Intel Bluetooth Kernel Extensions for macOS |
| [BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM) | Patches Bluetooth stack to allow non-Apple Bluetooth |
| [GUX-RyzenXHCIFix](https://github.com/RattletraPM/GUX-RyzenXHCIFix) | A fork of GenericUSBXHCI aimed at analyzing and fixing the USB3 |
| [Lilu.kext](https://github.com/acidanthera/Lilu) | Platform for arbitrary kext, library, and program patching throughout the system |
| [NVMeFix.kext](https://github.com/acidanthera/NVMeFix) | Improve compatibility with non-Apple SSDs |
| [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X) | Open source driver for the Realtek RTL8111/8168 family |
| [RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents) | Blocking unwanted processes causing compatibility issues on different hardware and unlocking the support for certain features restricted to other hardware |
| [SMCAMDProcessor.kext](https://github.com/trulyspinach/SMCAMDProcessor) | Power management and monitoring of AMD processors |
| [SMCBatteryManager.kext](https://github.com/acidanthera/VirtualSMC) | Enables battery readings |
| [USBMap](https://github.com/corpnewt/USBMap "USBMap") | Python script for mapping USB ports in macOS and creating a custom injector kext |
| [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC) | Advanced Apple SMC emulator in the kernel |
| [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2) | Fixes keyboard |
| [VoodooI2C.kext & VoodooU2CHID.kext](https://nootinc.github.io/Extras/Kexts/VoodooI2C.zip) | Fixes trackpad |


## SSDTs Used

Done with [SSDTTime](https://github.com/corpnewt/SSDTTime) in Windows 11

| Table | Description |
| --- | --- |
| [SSDT-EC](https://github.com/corpnewt/SSDTTime) | Adds a fake Embedded Controller device |
| [SSDT-PLUG-ALT](https://github.com/corpnewt/SSDTTime) | Fixes CPU definitions |
| SSDT-SLEEP | Prevents instant wake up of USB controllers. (after sleep, wake by pressing the power button) |
| [SSDT-USBX](https://github.com/corpnewt/SSDTTime) | Enables USB Power Management |
| [SSDT-XOSI](https://github.com/corpnewt/SSDTTime) | Spoof macOS to Windows for some ACPI features |

## Credits

*   [OC-Little-Translated](https://github.com/5T33Z0/OC-Little-Translated) Guides.
*   [AMD-OSX](https://forum.amd-osx.com/) Forum and the [dedicated Thread](https://forum.amd-osx.com/threads/amd-rayon-r7-5800h-install-monterey-kernel-panic.2725) users.
*   ExtremeXT for help, corrections, my first EFI and git README info/references.
*   zxc2689963 for EFI references.
*   [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) for the guides.
*   [Apple](https://www.apple.com/) for macOS.
*   [Acidanthera](https://github.com/acidanthera) for OpenCore and most Kexts.
*   Anyone else that helped to develop and improve hackintoshing.

## Screenshots

![screen2](https://github.com/kalkmann/Legion-5600H-Hackintosh/assets/8891448/0340a459-ccde-4dab-ae11-848c5fc8acb7)

![screen1](https://github.com/kalkmann/Legion-5600H-Hackintosh/assets/8891448/3b6a0492-2835-4231-bf29-ccf1c918bde5)

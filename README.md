# 7950X-6650XT-B650M-Hackintosh
*EFI files for my macOS 15 Seqoia Hackintosh configuration*

## Screenshots
![obfuscat](https://github.com/user-attachments/assets/1add2ca8-d569-4a8f-aebc-7e9ee20fb995)

## Specifications
**CPU:** *AMD Ryzen 9 7950X* <br>
**GPU:** *AMD Radeon 6650-XT* (ACPI spoof as 6600-XT by [7luk](https://github.com/7luk)) <br>
**RAM:** *32GB 6000MHz Corsair Vengeance (2x16)* <br>
**Storage:** *Kingston NV3 1TB (SNV3S/1000G)* <br>
**Motherboard:** *GIGABYTE B650M-D3HP* <br>
<sub>*RTL8125 Network Chipset* <br> *ALC897 Audio* <br>
<sub>
*1 x PS/2 keyboard/mouse port;
1 x USB Type-C® port, with USB 3.2 Gen 1 support;
3 x USB 3.2 Gen 1 ports;
2 x USB 2.0/1.1 ports;
1 x HDMI port;
2 x DisplayPorts;
1 x RJ-45 port;
3 x audio jacks* </sub> </sub>
<br>

## Installation

***You should read [Dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/) prior to following through with the installation process.*** If you like taking your chances, you should at least be familiar with the [terminology](https://dortania.github.io/OpenCore-Install-Guide/terminology.html) used in this guide.

> [!CAUTION]
> *You must **generate your own SMBIOS.*** <br> *SMBIOS information* is specific to every individual Hackintosh and therefore is not included in the config.plist file. Failure to generate the SMBIOS will result in a lack of functionality for Apple services (such as App Store) or ***cause the installer to fail to boot entirely.*** <br>
> [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) does this automatically. It's best you use *MacPro7,1* for the B650M-7950X combo *(see [Dortania](https://dortania.github.io/OpenCore-Install-Guide/extras/smbios-support.html#how-to-decide) for more information).*

> [!IMPORTANT]
> *You should **map your USB ports yourself.*** <br>
> Given we have the same motherboard, my mapping *might* work with your setup, though it's recommended you *generate your own USB map.* You can do so using [USBToolBox](https://github.com/USBToolBox/tool) (replace the UTBMap.kext file with yours under EFI/OC/Kexts).

### 1. BIOS Settings
Access your BIOS settings by pressing the Delete key during startup and change the following settings: <br>

| Setting | Value |
| :--  | :-- |
| CSM Support| *Disabled*
| Secure Boot | *Disabled*
| Fast Boot | *Disabled*
| SVM Enable | *Disabled*
| Initial Display Output | *PCIe 1 Slot*
| Integrated Graphics | *Disabled*
| Above 4G Decoding | *Enabled*
| Legacy USB Support | *Disabled*
| IOMMU | *Disabled*

<br>

*CSM Support: Disabled* <br>
![csm](https://github.com/user-attachments/assets/3b30ed02-c675-4207-a280-6773eef6d9cd) <br> <br>
*Fast Boot: Disabled* <br>
![fast](https://github.com/user-attachments/assets/9d58d10e-ad91-4101-bd66-156c073d5ec4) <br> <br>
*SVM Enable: Disabled* <br>
![SVM](https://github.com/user-attachments/assets/fa5b047c-77eb-4fd6-b384-f5d191bcee39) <br> <br>
*Initial Display Output: PCIe 1 Slot* <br>
![init](https://github.com/user-attachments/assets/679d06fc-7d9b-4d32-baa5-54a527d913ff) <br> <br>
*Integrated Graphics: Disabled* <br>
![integ](https://github.com/user-attachments/assets/1e254966-5072-4515-945c-2d82f51e27a8) <br> <br>
*Above 4G Decoding: Enabled* <br>
![4g](https://github.com/user-attachments/assets/76d0f867-d24b-41d6-b5bd-07a23f2f194e) <br> <br>
*Legacy USB Support: Disabled* <br>
![usb](https://github.com/user-attachments/assets/bd753ec7-a94d-40e1-b219-2215100b591b) <br> <br>
*IOMMU: Disabled* <br>
![IOMMU](https://github.com/user-attachments/assets/8ca79665-3ac1-4191-bafc-e489b65b6c4a)


### 2. Copy installation files
*Clone this repository to your installation USB's [EFI partition](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/).*
```
git clone https://github.com/akirakani-kei/7950X-6650XT-B650M-Hackintosh
```

## Additional information

#### Table of kexts

| Kext | Optionality |
| :--  | :-- |
| Lilu.kext | *Required*
| AMDRyzenCPUPowerManagenent.kext | *Required*
| IntelMKLFixup.kext | *Required*
| AppleMCEReporterDisabler.kext | *Required*
| AppleALC.kext | *Required* (audio)
| RestrictEvents.kext | *Required*
| LucyRTL8125Ethernet.kext| *Required* (internet)
| VirtualSMC.kext |*Required*
| WhateverGreen.kext | *Required* (GPU acceleration)
| USBToolBox.kext | *Required*
| UTBMap.kext | *Optional* (make your own)
| NVMeFix.kext | *Optional* (depends on your disk)

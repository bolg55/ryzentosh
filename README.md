# AMD Ryzen Hackintosh ... aka "Ryzentosh"
This is an outline of what went into building my new Hackintosh. I built my first hackintosh way back in 2011 or 2012, and things were much different back then. I had lucked out that one of my laptops I had used for school was an HP ProBook - perfect for making a Hackbook pro. 

So I followed the tutorials online at the time, without really knowing what I was doing, but interested all the same. After days of toiling, I finally got it to work. I was PUMPED! That Hackbook lasted me a long time... and then I finally got a real Macbook Pro, so I didn't really have a need to build another one. Follow that up with work-issued Macbooks and I sort of left hackintoshing in the rearview mirror...

Enter: COVID. I was home and bored and decided that I wanted to build a new computer. So that is what I did. I also decided that I wanted to have dual boot functionality - so I could game, but also to hackintosh again. And that is how I ended up here.

![Screenshot of About this Mac](https://res.cloudinary.com/dxghtqpao/image/upload/v1628291669/Screen_Shot_2021-08-06_at_7.06.35_PM_m3gm2l.png)

## Specifications 

|Component|Model|
|---|---|
|CPU|AMD Ryzen 7 3800x @3.9GHz|
|Motherboard|ASRock B550m Pro4|
|GPU|Sapphire Pulse RX580 8gb|
|RAM|G.Skill Ripjaws V Series 32gb DDR4 3200|
|OS1 - MacOS |WD Black SN750 NVMe M.2 1TB|
|OS2 - Windows 10|WD Blue 1TB SSD|
|Ethernet|Realtek RTL8111H|
|Wifi/Bluetooth|Intel AX200NGW|

**macOS version:** Big Sur 11.5.1

**OpenCore version:** 0.7.1

**SMBIOS:** MacPro7,1

## Drivers & Kexts

* [[Bootloader] OpenCore](https://github.com/acidanthera/OpenCorePkg)
* [[Patch] AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla)
* [[Driver] FwRuntimeServices](https://github.com/acidanthera/OpenCorePkg)
* [[Driver] HfsPlus](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)
* [[Driver] OpenCanopy](https://github.com/acidanthera/OpenCorePkg)
* [[Kext] Lilu](https://github.com/acidanthera/Lilu)
* [[Kext] VirtualSMC](https://github.com/acidanthera/VirtualSMC)
* [[Kext] WhateverGreen](https://github.com/acidanthera/WhateverGreen)
* [[Kext] AppleALC](https://github.com/acidanthera/AppleALC)
* [[Kext] RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases)
* [[Kext] AppleMCEReporterDisabler](https://github.com/AMD-OSX/AMD_Vanilla/blob/opencore/Extra/AppleMCEReporterDisabler.kext.zip)
* [[Kext] RestrictEvents](https://github.com/acidanthera/RestrictEvents)
* [[Kext] NVMeFix](https://github.com/acidanthera/NVMeFix)
* [[Kext] AirportItlwm](https://github.com/OpenIntelWireless/itlwm/releases)
* [[Kext] IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases)
* [[Kext] USBPorts](https://dortania.github.io/OpenCore-Post-Install/usb/manual/manual.html#usb-mapping-the-manual-way)

## Working
* **Sleep/Wake**
* **Restart/Shutdown**
  * This was a bit tricky, and caused a lot of issues. At first, restart / shutdown would not work correctly and a power cycle was needed to make the computer functional again. Narrowing this down was a lot of trial and error and Googling.
  * The solution was with USB mapping, specifically, disabling the onboard LED USB controller. I did this with the help of [Hackintool](https://ce05a305-2bad-44e3-9149-3538386d84d9.filesusr.com/archives/191c4b_c0fa53593ddb40c6beae7002a211d8b0.zip?dn=Hackintool.zip). I followed the steps outlined in the OpenCore post-install guide to generate a new USBPort kext, excluding the port that was causing issue. This solved the problem. 
* Ethernet
* Wifi / Bluetooth

## Not Working
* Mic > [[See Details]](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#no-mic-on-amd)
  * This isn't really an issue for me as this is a desktop computer and USB mic's work just fine.

## Tools
* [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)
* [ProperTree](https://github.com/corpnewt/ProperTree)
* [Hackintool](https://ce05a305-2bad-44e3-9149-3538386d84d9.filesusr.com/archives/191c4b_c0fa53593ddb40c6beae7002a211d8b0.zip?dn=Hackintool.zip)

## Building Your Own
If you want to build your own Hackintosh, the best place to start is with the [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/). Another great resource, if you are choosing to build an AMD-based computer is the [AMD-OSX forum/discord server](https://forum.amd-osx.com/index.php).  

### This was a frustrating / rewarding / interesting experience, and I am very pleased with the end result. Compared to my 2015 Macbook Pro, this computer performs incredibly well, and the build has been very stable after I ironed out all of the kinks. 

Disclaimer: This is for informational and entertainment purposes only - even using the same hardware and software patches does not guarantee an operational machine, and I am not held responsible should you follow along and brick your machine. 

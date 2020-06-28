# Clover_EFI-For-DELL-G5-5587

###Thanks to [Len](http://i.pcbeta.com/space-uid-4532202.html) and [黑果小兵(daliansky)](https://daliansky.net)

##Machine Details(may be specific)
*CPU：Intel i5-8300H
*Graphic card：Intel UHD630
*Screen：1920ｘ1080
*Audio card：ALC256(ALC3246 by Dell)
*Wireless：Use Broadcom DW1820A/BCM94356_096JNT instead (Good bye, Int-hell!!!)
----
##EFI Details
####The EFI folder is based on [Len's Dmg](http://bbs.pcbeta.com/viewthread-1858946-1-1.html)，made “八代笔记本UHD630” adapted. Available for mac OS 10.15.5，Big Sur not tested.
    ###Audio
    1. No VoodooHDA (Not compatible with audio plugs).
    2. AppleALC - Inject ID 97
    3. Known issue: You've got to unplug your earphone from the laptop during boot, or the internal speaker won't work.
   
    ###Wireless
    1. Thanks to [黑果小兵's tutorial](https://blog.daliansky.net/DW1820A_BCM94350ZAE-driver-inserts-the-correct-posture.html)。
    2. WiFi&Blutooth config for DW1820A/BCM94356 included. You may have to reject some pins of the card if you come across system blue-screen issues while booting into Windows.
    3. Airdrop works well. Sidecar works well with USB, but iPad gives a black screen if you use wireless mode. Handoff should also work well. 

    ###Some Others
    1. ACPI Error xxxxx method xxxxx Namespace lookup failure xxxxx etc.，in config.plist, turn off EC0 to EC,H_EC to EC and ECDV to EC(set true to "disabled").
    2. If it Stucks at ApplePS2TrakPad, put SSDT-EC.aml into /ACPI/Patched/ and don't blame the trackpad.
    3. If you use Clover Configurator to make macOS show Memory Info in system, you may lose audio driver and I don't know why...
    4. Plus also the TrackPad is "I2C", not "PS2"(I didn't make the I2C driver).
    5. Sleep, and wake up, and the system reboots.
    6. why can't i use ntfs for mac from seagate while the hdd IS from seagate

----

##ummmmmmm
Maybe I'm not going to fix the issues mentioned above due to my laziness and ignorance...I didn't do the trackpad which needs DSDT...
May have some mistakes because I'm not using macOS these days 'cause it's not very VOCALOID friendly...But this EFI should work well!
And sorry for my poor English...I havn't been doing this for ages.

Any other things that I can do, just leave a message:)
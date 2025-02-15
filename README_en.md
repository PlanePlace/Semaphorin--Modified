<div align="center">
<img src="https://files.catbox.moe/x7b0e2.png" height="128" width="128" style="border-radius:25%">
   <h1> Semaphorin 
      <br/> 64-Bit Downgrade, Dualboot & Jailbreak Utility
   </h1>
</div>

<h4 align="center"> Uses seprmvr64 by mineek<h4>
<h6 align="center"> Supports* iOS 7.0.6-12.1 as well as A7-A11 devices </h6>
<h6 align="center"> This is a fork of the tool with some updates </h6>

## IF YOUR DEVICE SUPPORTS [LEGACY-IOS-KIT](https://github.com/LukeZGD/Legacy-iOS-Kit), YOU SHOULD REALLY USE THAT OVER THIS.

## This modified Semaphorin has changed the method of obtaining IVKey and the download version of ramdisk.

## Support

If you encounter any problems, please report them on Issues.

I’m still just a high school student with little ability, but I’ll do everything I can! 😭

The Semaphorin project has been abandoned, but everyone still wants to use it because it’s the only tool that can bypass SEP forced downgrades, so I’m doing my part to fix it.

I hope the 64-bit downgrade path will have more possibilities in the future. Please go easy on me, experts!

It may be better for someone to rewrite the entire thing, and/or just create or use another tool

## Chart of compatibility

| iOS         | App Store | Cydia       | Tweaks    | Respring| Cellular | Sideloadly | iTunes     |
|-------------|-----------|-------------|-----------|---------|----------|------------|------------|
| 7.0.6       | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9745;    | &#9745;    | 
| 7.1.2       | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9745;    | &#9745;    |
| 8.4.1       | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9744;  | &#9745;    | &#9745;    |
| 9.3         | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |
| 10.3.3      | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |
| 11.3        | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |
| 12.1        | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |

Other iOS versions not listed in the chart may also work but they might have unexpected broken features/jailbreak

## Before using

1. Install Python： visit https://www.python.org/downloads/macos/ .

2. Install Homebrew： visit https://brew.sh .

3. Install openssl@3 ： Open Terminal, type `brew install openssl@3`.

4. Create the symbol file for openssl@3.： Open Terminal, type

    `ln -s /usr/local/opt/openssl@3/lib/libcrypto.3.dylib /usr/local/lib/libcrypto.3.dylib`
    
    `ln -s /usr/local/opt/openssl@3/lib/libssl.3.dylib /usr/local/lib/libssl.3.dylib`
    
## How do I use this?

This script deletes everything on your phone, including the main OS if you are not downgrading to iOS 10.3 or later. Make sure to backup all of your data before using this script as **anything on the device prior to running this script will be unrecoverable afterwards**. Use this script at your own risk. We are not responsible for any damages caused by you using this script.

This script will automatically set up a dualboot for iOS 10.3 and later.

To use this app, you need to downgrade to a supported version, and have a supported device.

`xcode-select install` to install `git` on macos

`git clone https://github.com/PlanePlace/Semaphorin--Modified && cd Semaphorin--Modified`

Connect device in DFU mode

`sudo ./semaphorin.sh <the version you are downgrading to> --restore`

For example you may write `sudo ./semaphorin.sh 9.3 --restore`

The script has to backup important files from your current iOS version before you can downgrade.

When the script asks `[*] Please enter the iOS version that is currently installed on your device.`, type your current iOS version and then hit the Enter key to continue.

It should then begin the process of downgrading your device. Please follow the on screen instructions. This might take a while. Your device will reboot multiple times.

If you downgraded to iOS 9 or later, please use the jailbreak app on your home screen to begin jailbreaking your device.

For iOS 7 and 8, see below troubleshooting steps for jailbreaking.

## IVKey

The IVKey issue will not affect users who want to downgrade iOS 11 and above, as iOS 11 and newer versions do not require decrypting the Root Filesystem.

For some strange reason, the IVKey obtained by FirmwareKeysDl-1.0-SNAPSHOT.jar is incorrect, causing OS.dmg to fail to generate properly, which results in a failed downgrade.

Therefore, this version of Semaphorin has modified the method of obtaining the IVKey, changing it to require the user to manually input the IVKey.

link: https://www.theiphonewiki.com/wiki/Firmware_Keys

Here’s an example:

If you want to downgrade the iOS 8.3 version of iPad Air 2 (iPad 5,3), you need to visit this website.

Then scroll down to find Firmware Versions and click on 8.x.

Continue scrolling down, find iPad Air 2, and click on iPad 5,3 under 8.3.

The Key value in the Root Filesystem section is your IVKey.

When Semaphorin.sh prompts you to enter the IVKey during the downgrade process, just paste it in. 😉

## Subsequent runs after downgrade is finished

Connect device in DFU mode

`sudo ./semaphorin.sh <the version you downgraded to previously> --boot`

For example, if you downgraded to iOS 9.3, you would run `sudo ./semaphorin.sh 9.3 --boot`.

It should just boot to your requested iOS version normally.

## Requirements

macOS Catalina or later, or Linux. The script only officially supports these versions.

Hackintoshes with AMD CPUs will **NOT** work with this.

Stable internet connection. Please don't try using this with dial up...

At least 20GB of free space on your computer

USB Type-A port and Lightning cable. USB Type-C ports will **NOT** work with this script. If you're using a Mac that only has a USB-C port (such as 12" MacBooks, and late Intel MacBook Airs) a dongle/dock with a USB-A port should work just fine with a standard USB-A to Lightning cable.

Working iDevice: The script has to backup `apticket.der`, `sep-firmware.img4`, `Baseband`, and `keybags` from your device before you can downgrade to an older iOS version.

## Setup.app bypass

We will not be providing any support for any method of deleting `/Applications/Setup.app` with our script.

This is only to comply with [r/jailbreak](https://www.reddit.com/r/jailbreak/) and [r/LegacyJailbreak](https://www.reddit.com/r/LegacyJailbreak/) rules and guidelines.

The script will downgrade your iOS version and jailbreak the downgraded OS very easily, but will not allow for bypassing **any** sort of Activation Lock.

We back up the `activation_records` from your main OS prior to downgrading your device, so please make sure your main OS is activated before using this tool.

## Troubleshooting
   
   ### Deep sleep, device won't turn on after locking it, have to reboot.
   The issue that causes deep sleep is unfortunately **unfixable**. There is, however, a workaround to this:

   Install the tweak "Insomnia" from BigBoss repo or "Fiona" from the repo https://julioverne.github.io
      
   *Note: This does slightly affect battery life due to the way it works. You probably aren't using this script for battery life though, are you.

   ### Unable to connect to WiFi networks, incorrect password.
   This is caused by an issue that's *impossible* to fix. You need to connect to an open WiFi network

   You can create one using the Internet Sharing feature on macOS or [linux-wifi-hotspot](https://github.com/lakinduakash/linux-wifi-hotspot) on, you guessed it, Linux if you prefer using another computer for this. 

   Be careful when doing this since *anyone* can connect to the open network you created. We are not responsible for **any** damages caused by doing this.

   ### Jailbreak/tweaks and other apps do not work (iOS 7 and 8)
   Open Terminal, type `su` -> `alpine` (input is invisible but still being typed) -> `reload`

   This is to be done every (re)boot

   It may fail the first time due to a malloc error, just close out of Terminal and re open the app. Do the same process over again and it should respring the device. All the apps on your device should now be working properly if you follow these steps.

   ### Safari does not work (iOS 10)
   Use the FileManager app on the home screen instead. It is a drop in replacement for Safari, and has a built in download manager also.

## Credits

- [PsychoTea](https://github.com/PsychoTea/) for [MeridianJB](https://github.com/PsychoTea/MeridianJB/) which we use for iOS 10.3.3 downgrades
- [coolstar](https://github.com/coolstar) for [Electra](https://www.coolstar.org/electra/) and [Chimera](https://chimera.coolstar.org/) jailbreaks which we use on iOS 11 and 12 downgrades
- [edwin170](https://github.com/edwin170) for a ton of help with fixing cell service, icloud, audio, 3d touch, gyroscope, microphone and other issues
- [johndoe123](https://twitter.com/iarchiveml) for the a7 ios 7 [downgrade guide](https://ios7.iarchive.app/downgrade/) which made this entire project possible
- [LukeZGD](https://github.com/LukeZGD/) for the updated [cydia.tar](https://github.com/LukeZGD/Legacy-iOS-Kit/raw/main/resources/jailbreak/freeze.tar) for jailbreaking older ios versions
- [TheRealClarity](https://github.com/TheRealClarity) for wtfis.app which we [repurposed](https://github.com/y08wilm/wtfis/blob/ios7/wtfis/ViewController.m#L27) to run [evasi0n7](https://ios.cfw.guide/installing-evasi0n7/) for sandbox patch on ios 7 to allow cydia substrate to not break apps
- [Nathan](https://github.com/verygenericname) for the ssh ramdisk and [iBoot64Patcher fork](https://github.com/verygenericname/iBoot64Patcher)
- [Mineek](https://github.com/mineek) for [seprmvr64](https://github.com/mineek/seprmvr64) and other patches. I want to give a very special thanks to [Mineek](https://github.com/mineek), if it werent for them this entire project would have not been possible. you are amazing and i appreciate all that you do, thank you so much
- [nyuszika7h](https://github.com/nyuszika7h) for the script to help get into DFU
- [tihmstar](https://github.com/tihmstar) for [pzb](https://github.com/tihmstar/partialZipBrowser)/original [iBoot64Patcher](https://github.com/tihmstar/iBoot64Patcher)/original [liboffsetfinder64](https://github.com/tihmstar/liboffsetfinder64)/[img4tool](https://github.com/tihmstar/img4tool)
- [Tom](https://github.com/guacaplushy) for a couple patches and bugfixes
- [xerub](https://github.com/xerub) for [img4lib](https://github.com/xerub/img4lib) and [restored_external](https://github.com/xerub/sshrd) in the ramdisk
- [Cryptic](https://github.com/Cryptiiiic) for [iBoot64Patcher](https://github.com/Cryptiiiic/iBoot64Patcher) fork, and [liboffsetfinder64](https://github.com/Cryptiiiic/liboffsetfinder64) fork
- [libimobiledevice](https://github.com/libimobiledevice) for several tools used in this project (irecovery, ideviceenterrecovery etc), and [nikias](https://github.com/nikias) for keeping it up to date
- [Nick Chan](https://github.com/asdfugil) general help with patches and iBoot payload stuff
- [Serena](https://github.com/SerenaKit) for helping with boot ramdisk.
- [planetbeing](https://github.com/planetbeing/) for dmg tool from [xpwn](https://github.com/planetbeing/xpwn)
- [exploit3dguy](https://github.com/exploit3dguy/) for [iPatcher](https://github.com/exploit3dguy/iPatcher) which is used for patching iBoot on ios 7
- [dora2-ios](https://github.com/dora2-iOS) for [iPwnder](https://iarchive.app/Download/ipwnder_macosx)
- [NyanSatan](https://github.com/NyanSatan) for [fixkeybag](https://github.com/NyanSatan/fixkeybag)

### English Version of README.md

[Click here](https://github.com/PlanePlace/Semaphorin-Modified/blob/Modified/README_en.md)

### 分支说明
本分支对 **FirmwareIVKey.jar** 进行了修改：  
通过从本人 GitHub 仓库中提取并读取已存储的 **IVKey**，以规避 **Cloudflare 防护机制**导致的 IVKey 获取失败问题。

### 设备与系统限制
- **支持设备**：A7 / A7X / A8 / A8X  
- **支持目标系统版本**：iOS 7.x – iOS 9.x  
- 暂无增添计划。

### macOS 兼容性说明
- 本分支的 **Semaphorin 仅适用于 macOS 15 及以下版本** (同时适用于Linux平台。)
- 针对 **macOS 26（Tahoe）**，已创建单独适配分支  
  → 请前往 **`macOS Tahoe`** 分支使用

### 测试情况
已在以下环境完成实测：
- MacBook Pro（M3 Pro）
- macOS 26.1
- 将 *iPad Air 2* 从 **iOS 15.8.5** 降级至 **iOS 8.1**

- Lenovo XiaoXinPro 13 2019
- Linux Mint 22.3
- 将 *iPad Air 2* 从 **iOS 15.8.5** 降级至 **iOS 9.0**

<div align="center">
<img src="https://files.catbox.moe/x7b0e2.png" height="128" width="128" style="border-radius:25%">
   <h1> Semaphorin 
      <br/> 64-Bit 降级, 双启动 & 越狱工具
   </h1>
</div>

<h4 align="center"> Uses seprmvr64 by mineek<h4>
<h6 align="center"> 支持* iOS 7.0.6-12.1 且为 A7-A11 设备 </h6>
<h6 align="center"> This is a fork of the tool with some updates </h6>

## 如果你的设备支持 [LEGACY-IOS-KIT](https://github.com/LukeZGD/Legacy-iOS-Kit), 那么你应该使用Legacy-iOS-Kit.

## 脚本来源

https://github.com/LukeZGD/Semaphorin 

## 兼容性图表

| iOS         | App Store | Cydia       | Tweaks    | Respring| Cellular | Sideloadly | iTunes     |
|-------------|-----------|-------------|-----------|---------|----------|------------|------------|
| 7.0.6       | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9745;    | &#9745;    | 
| 7.1.2       | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9745;    | &#9745;    |
| 8.4.1       | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9744;  | &#9745;    | &#9745;    |
| 9.3         | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |
| 10.3.3      | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |
| 11.3        | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |
| 12.1        | &#9745;   | &#9745;     | &#9745;   | &#9745; | &#9745;  | &#9744;    | &#9744;    |

其他没有在表格中列出的 iOS 版本可能会成功降级，但是可能存在问题，例如 App 启动崩溃、插件无法生效等。

## 脚本需求

macOS Catalina 或更新的版本, 或 Linux。

使用 AMD CPU 的黑苹果电脑 将 **不会** 正常工作。

稳定的互联网连接。

至少20 GB的可用磁盘空间。

USB-A 转 Lightning 的数据线。

USB-C 转 Lightning 的数据线将 **不会** 正常工作。

如果您正在使用只有 USB-C 的设备，请使用拓展坞，用 USB-A 转 Lightning 的数据线连接设备。

在降级前，脚本将会从设备备份 `apticket.der`, `sep-firmware.img4`, `Baseband`, 和 `keybags` ，所以请确保设备已经激活。

## 使用脚本之前

！！！ 一定要做 ！！！ 真的很重要

1. 安装 Python： 访问 https://www.python.org/downloads/macos/
    嗯，我用的是 Python 3.11.11。

2. 安装 Homebrew： 访问 https://brew.sh
    安装方法在里面。

3. 安装 openssl@3 ： 打开终端，输入 `brew install openssl@3`。

4. 设置 openssl@3 的符号文件 ： 打开终端，输入

    `ln -s /usr/local/opt/openssl@3/lib/libcrypto.3.dylib /usr/local/lib/libcrypto.3.dylib`
    
    `ln -s /usr/local/opt/openssl@3/lib/libssl.3.dylib /usr/local/lib/libssl.3.dylib`
    
## 我该如何使用它？

Semaphorin 将会删除您手机上的所有数据，包括设备原有的 iOS 系统， 确保您在降级之前已经备份了设备的所有数据。 **任何在使用脚本之前的操作将会在运行该脚本后无法恢复**. 请为自己的操作负责，我们不为由于此脚本造成的任何损失负责。

为了使用 Semaphorin，你应该选择一个受支持的降级版本，并使用受支持的降级设备.

1. 在 macOS 上，打开终端，输入 `xcode-select install` 来安装 `git` 。

2. 输入 `git clone https://github.com/PlanePlace/Semaphorin-Modified && cd Semaphorin-Modified` 来获取 Semaphorin。

3. 连接处于 DFU 模式的设备。

4. 输入 `sudo ./semaphorin.sh <你要降级的版本> --restore`。

举个例子，如果您要为设备降级 iOS 9.3，请输入 `sudo ./semaphorin.sh 9.3 --restore`。

在 Semaphorin 正式开始降级操作前，脚本将会于当前设备的 iOS 系统备份必要的文件。

当 Semaphorin 提示您 `[*] Please enter the iOS version that is currently installed on your device.`, 输入您设备当前的 iOS 版本并按回车。

Semaphorin 此时应该开始下载必要文件，请跟随屏幕上的指示，这可能需要一些时间，您的设备将会重启多次。

## 越狱

如果您选择降级到 iOS 9 及以后的版本，请点击设备主屏幕上的越狱工具来越狱设备。

对于降级到 iOS 7 和 iOS 8 的设备，请详见疑难解答部分。

## 重启后，再次引导设备

连接处于 DFU 模式的设备

打开终端，输入`sudo ./semaphorin.sh <the version you downgraded to previously> --boot`

举个例子，如果您降级到了 iOS 9.3，您应该输入`sudo ./semaphorin.sh 9.3 --boot`。

设备将会自动启动到您降级的版本。

## 绕过 Setup.app

在 Semaphorin 中，我们不提供任何删除 `/Applications/Setup.app` 的方法。

相关事宜，请查看 [r/jailbreak](https://www.reddit.com/r/jailbreak/) 和 [r/LegacyJailbreak](https://www.reddit.com/r/LegacyJailbreak/) 的规则

Semaphorin 不会绕过任何**种类**的激活锁

## 疑难解答

   ### 恢复不成功，设备一直重启不进入系统。
   查看终端的log，看看有没有下载失败的字样，如果出现下载失败，一定要 Control+C 关闭进程，并重新运行脚本。
   
   （ Control+C 关闭进程很重要，不要直接关闭窗口，进程可能还在后台运行，我就深受其害😭）
   
   查看终端的log，如果出现了备份激活文件或抹除设备的相关字样，恢复不成功的话一定要重新刷机，并激活设备再重新降级。
   
   （激活设备很重要，没有激活文件的话降级不一定会成功不说，降级后有可能还会无法激活！）
   
   ### 设备锁屏后，将会自动重启，不进入深度睡眠。
   这个问题很不幸 **无法修复**。但是有一个方法可以来**解决**这个问题：

   于 Bigboss 源中，安装插件 "Insomnia"  或于 https://julioverne.github.io 源中，安装插件 "Fiona" 。
      
   *备注: 这会影响电池使用时间，设备将在锁屏后保持 Wi-Fi 连接。

   ### 无法连接加密的 Wi-Fi 网络。
   这个问题很不幸 **无法修复**。 你需要连接到开放网络。

   你可以在 macOS 上分享网络 或 使用 [linux-wifi-hotspot](https://github.com/lakinduakash/linux-wifi-hotspot)。

   注意，任何人都可以连接到您创建的开放网络。 我们不为由于此操作造成的任何损失负责。

   ### 越狱/插件 或其他的 App 不工作 (iOS 7 and 8)
   打开 Terminal，输入 `su` -> `alpine` (此时无法查看您输入的内容) -> `reload`

   每次重启后都要做这样的操作。

   第一次操作可能会失败，重新打开 Terminal 并操作。再次操作后设备会注销，进入主桌面后所有的 插件/App 应该正常工作。

   ### Safari 不工作 (iOS 10)
  使用主屏幕上的 FileManager. 这是 Safari 的替代品。

## 致谢

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






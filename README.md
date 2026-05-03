<!--
Talk about Windhawk
add both unubdles and ps1 files download
[USB Latency Analyzer](https://tools.mariusheier.com/cpudirect.html)
Windwak
    - mouse acceleration disable
    - Classic context menu on Windows 11
    - Alt+Tab per monitor
    - Turn off change file extension warning
    - F1 Blocker
```cmd
irm "https://christitus.com/win" | iex
```
- change DNS
-->

# Windows 11 IoT Enterprise LTSC Install Guide
My personal guide to installing Windows 11 IoT Enterprise LTSC and packages.

Who is this for, well mostly only for myself since I doubt anyone will like my packages that I have listed down here.
# Prepparations
- Create a Windows installation media. Ventoy is preferred. 
- Rename the `C:/` drive to a recognizable name so you can easly overwrite during the Windows installation.
- Check the size of you drive to verify that aren't installing it on the wrong drive
- If you plan dual boot Linux and Windows, install Windows first then Linux because some motherboards delete EFI boot entries after a windows install
- Download Wi-Fi Driver if using Ethernet isn't a option
    - make sure to place the Wi-Fi driver on a USB 

## Windows 11 ISO installation
1. Select `Windows 11 IoT Enterprise LTSC` option on which derivative  install.
2. Click on the `I Don't have a Activation Code` link at the bottom left of the screen.
3. Select the drive with the recognizable name from before.
4. When the computer reboots unplug the USB
5. The computer will reboot and check for update once it done checking for updates up plug the Ethernet if you want to use a local account instead of a Microsoft account.
6. Connect to Wifi or install wifi driver from before so you can sign into your Microsoft account.
    - to install the driver press `SHIFT` + `F10` then type `explorer` in the cmd window. Then go install the exe.
7. Sign in or make a account
8. Connect Ethernet.
8. The computer will reboot into Windows

## Windows
1. Connect to Wifi
2. Activate Windows
    ```bash
    irm https://get.activated.win | iex
    ```

3. Install Microsoft Store
Microsoft Store will be installed in the background. Look the notification menu for progress. It sometimes takes a long time to install.
    ```bash
    wsreset -i
    ```

4. Install drivers

    - [AMD Adrenalin](https://www.amd.com/en/support/download/drivers.html)
    - Intel Driver & Support Assistant
    ```bash
    winget install -e --id Intel.IntelDriverAndSupportAssistant
    ```
    - [Nvidia App](https://www.nvidia.com/en-us/software/nvidia-app/)
    - Ethernet or WiFi
    - Sound
    - Chipset

5. install [Xbox App](https://aka.ms/xboxinstaller)
    - install xbox deps in the nofication menu in the xbox app

6. install winget and packages
    Microsoft [Winget store](https://apps.microsoft.com/detail/9nblggh4nns1) page
    ```bash
    Install-Module -Name Microsoft.WinGet.Client
    ```
    `9MSMLRH6LZF3` is Microsoft's new notepad. NanaZip is 7zip but update gui and context menu support for win 11
    ```bash
    winget install LibreWolf.LibreWolf M2Team.NanaZip 9MSMLRH6LZF3 Google.Chrome 7zip.7zip MartiCliment.UniGetUI Valve.Steam Discord.Discord Gyan.FFmpeg
    ```

    Installing image\video extensions `jxl, AVC, Raw, webp, ~~HEIF~~, webm, MPEG-2, av1, vp9, AC-3/E-AC3` missing HEVC (HEIF) and AC-4. [Link](https://www.codecguide.com/media_foundation_codecs.htm)
    ```bash
    winget install 9MZPRTH5C0TB 9PB0TRCNRHFX 9NCTDW2W1BH8 9PG2DK419DRG 9PMMSR1CGPWG 9N5TDP8VCMHS 9N95Q1ZZPMH4 9MVZQVXJBQ9V 9N4D0MSMP0PT 9NVJQJBDKN97
    ```

7. install [Microsoft Office 365](https://gravesoft.dev/office_c2r_links)
    - Activate Microsoft Office 365

    ```bash
      irm https://get.activated.win | iex
    ```

Configuration
---
##### Disable windows groups in alt + tab
disable
```
Show my snapped windows when I hover over taskbar apps, in Task View, and when I press Alt + Tab.
```
 in Multitasking system settings

##### Disable Fast Startup and disable hibernation
Only needed if you plan to share drives both on Windows and linux when dual booting

With administrator privileges
```bash
powercfg /H off
```

##### Edit starup apps
Might want to wait until winget and scoop install everything first

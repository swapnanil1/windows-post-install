# Windows Optimization and Software Setup Guide

## 1. Disable Hibernation & Reserved Space for Windows Updates

Open PowerShell (as admin) and run the following commands:
```
    powercfg /hibernate off
    dism /Online /Set-ReservedStorageState /State:Disabled
```
## 2. System Configuration

- Press Windows+R to open Run and enter "SystemPropertiesAdvanced.exe" for System Properties.
  
  ### Computer Name Tab:
  - Change your PC/laptop name for better recognition.

  ### Advanced Tab:
  - Navigate to **Performance -> Advanced -> Change Virtual Memory (VM)**:
    - Untick "Automatically manage paging."
    - Select your C: drive.
    - Choose "System Managed Size."
    - Click Set, then OK repeatedly.

  ### Remote Tab:
    - Uncheck "Allow remote assistance to this computer."
    - Click OK and restart later.
    

## 3. Disable Windows Defender and Automatic Driver Updates

If you prefer to use a third-party antivirus and want to control driver updates, follow these steps:

### Disable Windows Defender

1. Press Windows+R to open Run and run `gpedit.msc`, then click OK.
2. Navigate to Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus.
3. Double-click the "Turn off Microsoft Defender Antivirus" policy.
4. Select the Enabled option to disable Microsoft Defender Antivirus permanently.
5. Click OK and exit the Group Policy Editor.
6. Restart your PC.

**Note:** Performing this before connecting to Ethernet will prevent Windows from downloading Defender security patches, saving time if you plan to use a third-party antivirus.

### Disable Automatic Driver Updates
If You want to stop windows form automatically download your drivers 

#### In Windows 11:

1. Inside Computer Configuration, go to Administrative Templates > Windows Components > Windows Update > Manage updates offered from Windows Updates.
2. Double-click on "Do not include drivers with Windows Updates."
3. Select the Enabled option and click OK.
4. Restart your PC.

#### In Windows 10:

1. Inside Computer Configuration, go to Administrative Templates > Windows Components > Windows Update.
2. Double-click on "Do not include drivers with Windows Updates."
3. Select the Enabled option and click OK.
4. Restart your PC.

**Note:** This will prevent automatic installation of old drivers that Windows updates install by default, which can cause performance slowdowns due to incompatibility with games.

## 4. Windows Updates

Connect to Ethernet and check for updates until none remain.
This can take some time and multiple restarts.

## 4. Download and Install AME Wizards & AME Playbooks

Explore the following options for AME Wizards and AME Playbooks, each tailored to different preferences and use cases:

- [AME Wizards](https://git.ameliorated.info/Styris/trusted-uninstaller-cli/releases): This package, known as "The Installer," streamlines the installation process for your convenience.

- [AME 11 Book](https://git.ameliorated.info/Styris/AME-11/releases): Featuring a modern design with enhanced effects, this version is designed for faster setup, ease of use, and is especially recommended for beginners. Ideal for work laptops.

- [AME 10 Book](https://git.ameliorated.info/yoh/AME-10): This option provides a rock-solid, stable performance with a minimal resource footprint. It ensures a faster setup and easy operation, making it perfect for beginners using older hardware.

- [AtlasOS](https://github.com/Atlas-OS/Atlas/releases): For a completely barebones experience, specifically tailored for gamers and recommended for desktop use.

- [ReviOS](https://github.com/meetrevision/playbook/releases): Offering frequent updates, this version is designed for gaming enthusiasts seeking a mix of both enhanced security features and functionality.

Refer to [Syrm Install Tutorial](https://youtu.be/GoO36Tj5TGE?si=OrfAb30e19kXMneR) for installation guidance.

## 5. Installing Scoop & Chocolatey 
Scoop and Chocolatey serve as package managers for Windows, akin to a Google Play Store for app installations, all managed through straightforward commands within the terminal.
Open PowerShell normally and paste the following 
### Scoop
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```
### Chocolatey
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

## 6. Installing Applications with Scoop or Chocolatey

To set up your system with essential applications, follow these steps in PowerShell:

### Scoop
#### Add Buckets/Repos to Scoop Config
```powershell
scoop install git
scoop bucket add extras
scoop bucket add nerd-fonts

```
#### Recommended apps & fonts
```
scoop install git
scoop bucket add extras
scoop bucket add nerd-fonts
scoop install onlyoffice-desktopeditors discord telegram bleachbit everything keepassxc nomacs notepadplusplus obs-studio powertoys qbittorrent simplewall sumatrapdf mpv yt-dlp vcredist vcredist2022 openrgb avidemux vscode windows-terminal windowsdesktop-runtime chromium JetBrainsMono-NF-Mono
```
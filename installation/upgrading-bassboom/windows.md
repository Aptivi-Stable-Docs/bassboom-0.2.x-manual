---
description: Upgrading BassBoom on Windows!
icon: windows
---

# Windows

Upgrading BassBoom on Windows is pretty simple, depending on the way you've installed it. To upgrade it, choose a method.

## Method 1: Windows Installer

You can update BassBoom using the Windows Installer method.

1. Download the latest BassBoom EXE file from [this page](https://github.com/Aptivi/BassBoom/releases).
2. Double-click on the EXE file and follow the instructions
3. Double-click on `BassBoom` in your desktop.

## Method 2: Using Chocolatey

Any updates to the BassBoom Chocolatey package can be done using a built-in Chocolatey command. To update the kernel, follow these steps:

1. Open your favorite terminal emulator, like ConEmu
2. Run `choco upgrade bassboom`
3. Once the upgrade is done, run BassBoom like you normally would

## Method 3: Manually unpacking

BassBoom can also be manually updated in case the automatic updater failed to update. To update BassBoom, perform the same steps as in installing it.

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/BassBoom/releases).
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like ConEmu, and change the working directory to a folder containing the BassBoom executable
5. Execute `bassboom` or `BassBoom.Cli.exe` to start the kernel

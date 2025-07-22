---
description: Installing BassBoom on Windows!
icon: windows
---

# Windows

Before performing the installation, your Windows system must meet the following requirements:

| System     | Framework                                                          | Terminal                                                  |
| ---------- | ------------------------------------------------------------------ | --------------------------------------------------------- |
| Windows 7+ | [.NET 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) | [ConEmu](https://conemu.github.io/) or Windows 10 cmd.exe |

We advice you to use the terminal emulation software capable of displaying the VT sequences on systems older than Windows 10. BassBoom uses Terminaux to render its elements in the CLI music player.

## Installation

There are several ways to install BassBoom on Windows systems. We recommend installing BassBoom using the Chocolatey package manager or the Windows installer for simplicity.

### Method 1: Windows Installer

The Windows Installer method allows you to easily install BassBoom.

1. Download the latest Windows Installer EXE file from [this page](https://github.com/Aptivi/BassBoom/releases)
2. Double-click on a single EXE file, and follow the instructions
3. Double-click on `BassBoom` in your desktop.

### Method 2: Chocolatey

This step-by-step guide shows you how to install BassBoom using the package manager, [Chocolatey](https://chocolatey.org/install), assuming that you already have it on your system.

1. Ensure that Chocolatey is installed to your system PATH
2. Open your favorite terminal emulator, like ConEmu, and execute the following command: `choco install bassboom`
3. Start BassBoom using `bassboom`

### Method 3: Manual unpack

If you like to manually unpack the BassBoom packages, follow these steps:

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/Kernel-Simulator/releases).
3. Unpack the ZIP archive to any folder of your choice using [7-Zip](https://7-zip.org/)
4. Open your favorite terminal emulator, like ConEmu, and change the working directory to a folder containing the BassBoom executable
5. Execute `bassboom` or `BassBoom.Cli.exe` to start the kernel

## Notice for SmartScreen

SmartScreen may detect that BassBoom and its associated executables may not pass the SmartScreen attestation. If this happens, you'll see the below page:

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

BassBoom will not put your PC at risk (except if you downloaded a copy from an unofficial software distributor, or from an unofficial source other than our official releases, our Chocolatey page found [here](https://community.chocolatey.org/packages/bassboom), and our NuGet page found [here](https://www.nuget.org/packages/BassBoom.Basolia/)). Click on `More Info`, then click on `Run anyways`.

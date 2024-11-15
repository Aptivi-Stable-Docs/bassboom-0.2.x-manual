---
description: Installing BassBoom on Linux!
icon: linux
---

# Linux

Before performing the installation, your Linux system must meet the following requirements:

| System            | Framework                                                          | Terminal                      |
| ----------------- | ------------------------------------------------------------------ | ----------------------------- |
| Supported distros | [.NET 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) | Konsole, GNOME Terminal, etc. |

We advice you to use the terminal emulation software capable of displaying the VT sequences on systems older than Windows 10. BassBoom uses Terminaux to render its elements in its CLI music player.

## Installation

To install GRILO to your Windows system, follow these steps:

1. Ensure that you have all the required software installed
2. Download the latest core ZIP file from this page
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like ConEmu, and change the working directory to a folder containing the BassBoom executable.
   * .NET 8.0 version of BassBoom is located at `net8.0`
5. Execute `dotnet BassBoom.Cli.exe` for .NET 8.0 to start the music player

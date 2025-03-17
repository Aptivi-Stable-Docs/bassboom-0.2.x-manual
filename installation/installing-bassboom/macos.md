---
description: How to install BassBoom on macOS
icon: apple
---

# macOS

To run BassBoom in the absolute minimum requirements, your computer needs to have the following installed:

| System                   | Framework                                                          | Terminal                                       |
| ------------------------ | ------------------------------------------------------------------ | ---------------------------------------------- |
| macOS Catalina or higher | [.NET 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) | [iTerm 2.0](https://iterm2.com/downloads.html) |

## Installation

There is one way to install BassBoom on macOS systems. Follow these steps to get started:

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/BassBoom/releases).
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like iTerm2, and change the working directory to a folder containing the BassBoom executable
5. Execute `dotnet BassBoom.Cli.dll` to start the kernel

## Bleeding-edge

Bleeding-edge builds usually come from building the development branch of BassBoom, and they usually contain bugs and other untested features.

If you're a tester to such software, please follow the steps on your macOS machine. Please be sure that you're signed in to your GitHub account.

1. Open the [canary release preparation workflow](https://github.com/Aptivi/BassBoom/actions/workflows/release-canary.yml)
2. Select the most recent build
3. Scroll down to Artifacts and click on the `bb-build` button to download the ZIP file.
4. Extract the file. Be sure that you have the latest version of your favorite archive manager installed.
5. Open your favorite terminal emulator, like iTerm 2, and change the working directory to a folder containing the BassBoom executable
6. Execute `bassboom` or `dotnet BassBoom.Cli.dll` to start the kernel

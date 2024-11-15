---
description: Installing BassBoom to Android!
icon: android
---

# Android

The tricky part is getting BassBoom to run on Android phones and tablets, especially those that run the latest version of Android. The trickier part is getting PulseAudio to work.

## Installation

To install BassBoom on your phone or tablet, install the following dependencies:

* [Termux](https://termux.dev/en/)
* [Ubuntu PRoot](https://wiki.termux.com/wiki/PRoot#Installing\_Linux\_distributions)
* PulseAudio on your Termux environment

Ensure that your Android version is compatible with Termux. You need at least 8 GB of free storage and Android 7.0 or higher.

Once you're done, follow the steps:

1. Install Termux
2. Install `proot-distro` using the following command:
   * `pkg install proot-distro`
3. Install the Ubuntu proot and PulseAudio
   * `proot-distro install ubuntu`
   * `pkg install pulseaudio`
4. Start PulseAudio. Note that you'll have to repeat this each time you exit and re-open Termux.
   1. `pulseaudio --start --load="module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" --exit-idle-time=-1`
5. Log in to the Ubuntu proot and set the PulseAudio server environment variable
   * `proot-distro login ubuntu`
   * `export PULSE_SERVER=127.0.0.1`
6. Ensure that you've updated the package cache
   * `apt update`
   * `apt dist-upgrade`
7. Install the .NET 8.0 runtime
   * `apt install dotnet-runtime-8.0`
8. Install `wget` to download the latest release from [this page](https://github.com/Aptivi/GRILO/releases).
   * `apt install wget`
   * `wget https://github.com/Aptivi/BassBoom/releases/download/vx.x.x/x.x.x-bin.zip`
9. Install `unzip` to extract the files
   * `apt install unzip`
   * `unzip x.x.x-bin.zip`
10. Execute `dotnet BassBoom.Cli.dll`
11. Once you specify the music path, press Space and music should be playing from your phone or your tablet.

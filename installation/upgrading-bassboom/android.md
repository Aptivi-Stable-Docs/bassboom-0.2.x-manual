---
description: Upgrading BassBoom on Android!
icon: android
---

# Android

The only way to upgrade BassBoom in Android is to unpack the updated files manually. This method also works for bleeding-edge builds, though you have to use unzip instead. This assumes that you've already set up PulseAudio and that it's working on your Android device.

In case it's not running, execute the following command outside your proot environment:

```shell-session
$ pulseaudio --start --load="module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" --exit-idle-time=-1
```

To upgrade, follow these steps:

1. Log in to the Ubuntu proot
   * `proot-distro login ubuntu`
2. Install `wget` to download the latest release from [this page](https://github.com/Aptivi/GRILO/releases).
   * `apt install wget`
   * `wget https://github.com/Aptivi/BassBoom/releases/download/vx.x.x/x.x.x-bin.zip`
3. Install `unzip` to extract the files
   * `apt install unzip`
   * `unzip x.x.x-bin.zip`
4. Execute `dotnet BassBoom.Cli.dll`

---
description: Installing BassBoom to Android!
icon: android
---

# Android

The tricky part is getting BassBoom to run on Android phones and tablets, especially those that run the latest version of Android. The trickier part is getting PulseAudio to work.

## Installation

To install BassBoom on your phone or tablet, install the following dependencies:

* [Termux](https://termux.dev/en/)
* [Ubuntu PRoot](https://wiki.termux.com/wiki/PRoot#Installing_Linux_distributions)
* PulseAudio on your Termux environment

Ensure that your Android version is compatible with Termux. You need at least 8 GB of free storage and Android 7.0 or higher.

Once you're done, follow the steps:

1. Install Termux
2. Install `proot-distro` using the following command:
   * `pkg install proot-distro`
3. Install the Ubuntu proot and PulseAudio
   * `proot-distro install ubuntu`
   * `pkg install pulseaudio`
4. Append the following text at the end of the `$PREFIX/etc/pulse/default.pa` like this:
   1. `echo "load-module module-simple-protocol-tcp source=OpenSL_ES_sink.monitor port=12345 record=true" >> $PREFIX/etc/pulse/default.pa`
5. Start PulseAudio. Note that you'll have to repeat this each time you exit and re-open Termux.
   1. `pulseaudio --start --load="module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" --exit-idle-time=-1`
   2. If you get no audio input and you're using a Samsung device with **One UI 6.1** or higher, kill PulseAudio with `pkill pulseaudio`, then append `LD_PRELOAD=/system/lib64/libskcodec.so` before the above command like this:
      1. `LD_PRELOAD=/system/lib64/libskcodec.so pulseaudio --start --load="module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" --exit-idle-time=-1`
6. Log in to the Ubuntu proot and set the PulseAudio server environment variable
   * `proot-distro login ubuntu`
   * `export PULSE_SERVER=127.0.0.1`
7. Ensure that you've updated the package cache
   * `apt update`
   * `apt dist-upgrade`
8. Install the .NET 8.0 runtime
   * `apt install dotnet-runtime-8.0`
9. Install `wget` to download the latest release from [this page](https://github.com/Aptivi/GRILO/releases).
   * `apt install wget`
   * `wget https://github.com/Aptivi/BassBoom/releases/download/vx.x.x/x.x.x-bin.zip`
10. Install `unzip` to extract the files
    * `apt install unzip`
    * `unzip x.x.x-bin.zip`
11. Execute `dotnet BassBoom.Cli.dll`
12. Once you specify the music path, press Space and music should be playing from your phone or your tablet.

## Bleeding-edge

Bleeding-edge builds usually come from building the development branch of the kernel, and they usually contain bugs and other untested features.

If you're a tester to such software, please follow the steps on your Windows machine. Please be sure that you're signed in to your GitHub account.

1. Open the [canary release preparation workflow](https://github.com/Aptivi/BassBoom/actions/workflows/release-canary.yml)
2. Select the most recent build
3. Scroll down to Artifacts and click on the `nks-build` button to download the ZIP file.
4. Repeat steps 1-7 in the `Installation` section
5. Now, use the `termux-setup-storage` command. Follow the instructions [here](https://wiki.termux.com/wiki/Termux-setup-storage).
6. Copy the `nks-build.zip` file from `~/storage/downloads/nks-build.zip` to your home directory
   * `cp ~/storage/downloads/nks-build.zip ~/`
7. Still in the home directory, install unzip to extract the files
   * `apt install unzip`
   * `unzip nks-build.zip`
8. Execute `dotnet Nitrocid.dll`

## Important notes

Here are important notes to consider when trying to run Nitrocid KS on Android:

{% hint style="warning" %}
Trying to run or build Nitrocid KS on an ARM64 Android device (e.g. Android devices with Qualcomm Snapdragon 8 Gen 2 as SoC) with Termux emits two error messages. The first one is:

<pre class="language-shell-session"><code class="lang-shell-session">$ dotnet build
<strong>GC heap initialization failed with error 0x8007000E
</strong><strong>Failed to create CoreCLR, HRESULT: 0x8007000E
</strong></code></pre>

and the second one is:

<pre class="language-shell-session"><code class="lang-shell-session">$ DOTNET_GCHeapHardLimit=1C0000000 dotnet build
(...)
<strong>error MSB6006: "csc.dll" exited with code 139.
</strong><strong>Build FAILED.
</strong></code></pre>

In order to fix the first message, append the below environment variable before each `dotnet build` command like this:

<pre class="language-shell-session"><code class="lang-shell-session"><strong>$ DOTNET_GCHeapHardLimit=1C0000000 dotnet build
</strong></code></pre>

However, to fix the second message, download the fixed version of `proot` using [this link](https://drive.google.com/file/d/1J9euzuGB5w6WGLVNVxTFVnrauTEzISAV/view?usp=sharing) ([mirror if down](https://mega.nz/file/6dYT2YrY#IPKfJRx3Rt8xql1ggyQ95rgEkpDd_vksP02vnnaOPd4)) and run these commands outside the Ubuntu `proot-distro` environment:

<pre class="language-shell-session"><code class="lang-shell-session"><strong># dpkg -i proot_5.1.107-50_aarch64.deb
</strong><strong># apt-mark hold proot
</strong></code></pre>
{% endhint %}

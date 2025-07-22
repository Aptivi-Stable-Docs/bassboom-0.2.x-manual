---
description: Installing BassBoom on Linux!
icon: linux
---

# Linux

Before performing the installation, your Linux system must meet the following requirements:

| System            | Framework                                                          | Terminal                      |
| ----------------- | ------------------------------------------------------------------ | ----------------------------- |
| Supported distros | [.NET 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) | Konsole, GNOME Terminal, etc. |

## Installation

There are several ways to install BassBoom on Linux systems.

### Method 1: Manual unpack

If you like to manually unpack the BassBoom packages, follow these steps:

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/BassBoom/releases).
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like Konsole, and change the working directory to a folder containing the BassBoom executable
5. Execute `dotnet BassBoom.Cli.dll` to start the kernel

### Method 2: Ubuntu PPA

{% hint style="info" %}
This only applies to Ubuntu and its derivatives. However, we only support the vanilla Ubuntu distribution. <mark style="color:red;">**Don't try this method on**</mark> [<mark style="color:red;">**Debian**</mark>](https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian)<mark style="color:red;">**.**</mark>
{% endhint %}

If you're running Ubuntu, you can install BassBoom using the Ubuntu PPA. Just follow these steps:

1. Open your terminal emulator and execute the following:
   * `sudo add-apt-repository ppa:eofla/bassboom`
   * `sudo apt update`
2. Install the `bassboom` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `2`)
   * `sudo apt install bassboom-2`
3. Start `bassboom` (appending the same suffix above, like `bassboom-2`), or use your app drawer to find `BassBoom` corresponding to your installed API version

You can choose between the version series that you want to upgrade in the output of the `apt` command when it prompts you to select one of them, as `bassboom` is a virtual package.

### Method 3: Arch Linux AUR

{% hint style="info" %}
This only applies to vanilla Arch Linux. We don't officially support Arch's derivatives, such as Manjaro and EndeavourOS.
{% endhint %}

If you're running Arch, you can install BassBoom using the Arch Linux AUR. Just follow these steps:

1. Open your terminal emulator and install your preferred AUR helper. Further steps assume that you have [Yay](https://github.com/Jguer/yay) installed.
2. Install the `bassboom-2` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `2`)
   * `yay -Sy bassboom-2`
3. Start `bassboom` (appending the same suffix above, like `bassboom-2`), or use your app drawer to find `BassBoom` corresponding to your installed API version

You can't install the release version and the cutting-edge (those with the `-git` suffix) version at the same time, since files conflict.

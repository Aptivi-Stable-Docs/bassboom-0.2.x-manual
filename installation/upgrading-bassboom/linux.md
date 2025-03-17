---
description: How to upgrade BassBoom on Linux!
icon: linux
---

# Linux

Upgrading BassBoom on Linux is simple, depending on the way you've installed it. To upgrade it, choose your preferred method.

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

If you're running Ubuntu, you can upgrade BassBoom using the Ubuntu PPA. Just follow these steps:

1. Open your terminal emulator and execute the following:
   * `sudo add-apt-repository ppa:eofla/bassboom`
   * `sudo apt update`
2. Upgrade the `bassboom` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `2`)
   * `sudo apt install bassboom-2`
3. Start `bassboom` (appending the same suffix above, like `bassboom-2`), or use your app drawer to find `BassBoom` corresponding to your installed API version

You can choose between the version series that you want to upgrade in the output of the `apt` command when it prompts you to select one of them, as `bassboom` is a virtual package.

### Method 3: Arch Linux AUR

{% hint style="info" %}
This only applies to vanilla Arch Linux. We don't officially support Arch's derivatives, such as Manjaro and EndeavourOS.
{% endhint %}

If you're running Arch, you can upgrade BassBoom using the Arch Linux AUR. Just follow these steps:

1. Open your terminal emulator and install your preferred AUR helper. Further steps assume that you have [Yay](https://github.com/Jguer/yay) installed.
2. Upgrade the `bassboom-2` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `2`)
   * `yay -Sy bassboom-2`
3. Start `bassboom` (appending the same suffix above, like `bassboom-2`), or use your app drawer to find `BassBoom` corresponding to your installed API version

You can't install the release version and the cutting-edge (those with the `-git` suffix) version at the same time, since files conflict.

## Bleeding-edge

Bleeding-edge builds usually come from building the development branch of the kernel, and they usually contain bugs and other untested features.

If you're a tester to such software, please follow the steps on your Linux machine. Please be sure that you're signed in to your GitHub account.

1. Open the [canary release preparation workflow](https://github.com/Aptivi/BassBoom/actions/workflows/release-canary.yml)
2. Select the most recent build
3. Scroll down to Artifacts and click on the `bb-build` button to download the ZIP file.
4. Extract the file. Be sure that you have the latest version of 7-Zip or your favorite archive manager installed.
5. Open your favorite terminal emulator, like Konsole, and change the working directory to a folder containing the BassBoom executable
6. Execute `dotnet BassBoom.Cli.dll` to start the kernel

{% hint style="info" %}
For Arch users, just follow the above steps, but upgrade the `-git` suffix package like this:

* `yay -Sy bassboom-2-git`

You don't need to sign in to your GitHub account in this case.
{% endhint %}

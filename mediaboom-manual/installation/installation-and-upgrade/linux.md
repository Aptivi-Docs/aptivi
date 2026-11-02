---
description: Installing MediaBoom on Linux!
icon: linux
---

# Linux

Before performing the installation, your Linux system must meet the following requirements:

| System            | Framework                                                            | Terminal                      |
| ----------------- | -------------------------------------------------------------------- | ----------------------------- |
| Supported distros | [.NET 10.0](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) | Konsole, GNOME Terminal, etc. |

***

## <mark style="color:$primary;">Installation</mark>

There are several ways to install MediaBoom on Linux systems.

<details>

<summary>Method 1: Manually unpacking</summary>

If you'd like to manually unpack the MediaBoom packages, follow these steps:

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/MediaBoom/releases).
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like Konsole, and change the working directory to a folder containing the MediaBoom executable
5. Execute `dotnet MediaBoom.Cli.dll` to start the kernel

</details>

<details>

<summary>Method 2: Ubuntu PPA</summary>

If you're running Ubuntu, you can install MediaBoom using the Ubuntu PPA. Just follow these steps:

1. Open your terminal emulator and execute the following:
   * `sudo apt update`
2. Install the `mediaboom` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `3`)
   * `sudo apt install mediaboom-3`
3. Start `mediaboom` (appending the same suffix above, like `mediaboom-3`), or use your app drawer to find `MediaBoom` corresponding to your installed API version

You can choose between the version series that you want to upgrade in the output of the `apt` command when it prompts you to select one of them, as `mediaboom` is a virtual package.

{% hint style="danger" %}
This only applies to Ubuntu and its derivatives. However, we only support the vanilla Ubuntu distribution. <mark style="color:red;">**Don't try this method on**</mark> [<mark style="color:red;">**Debian**</mark>](https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian)<mark style="color:red;">**.**</mark>
{% endhint %}

</details>

<details>

<summary>Method 3: Arch Linux AUR</summary>

If you're running Arch, you can install MediaBoom using the Arch Linux AUR. Just follow these steps:

1. Open your terminal emulator and install your preferred AUR helper. Further steps assume that you have [Yay](https://github.com/Jguer/yay) installed.
2. Install the `mediaboom-3` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `3`)
   * `yay -Sy mediaboom-3`
3. Start `mediaboom` (appending the same suffix above, like `mediaboom-3`), or use your app drawer to find `MediaBoom` corresponding to your installed API version

{% hint style="info" %}
This only applies to vanilla Arch Linux. We don't officially support Arch's derivatives, such as Manjaro and EndeavourOS.
{% endhint %}

{% hint style="danger" %}
You can't install the release version and the cutting-edge (those with the `-git` suffix) version at the same time, since files conflict.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Upgrade</mark>

Upgrading MediaBoom on Linux is simple, depending on the way you've installed it. To upgrade it, choose your preferred method.

<details>

<summary>Method 1: Manually unpacking</summary>

If you like to manually unpack the MediaBoom packages, follow these steps:

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/MediaBoom/releases).
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like Konsole, and change the working directory to a folder containing the MediaBoom executable
5. Execute `dotnet MediaBoom.Cli.dll` to start the kernel

</details>

<details>

<summary>Method 2: Ubuntu PPA</summary>

If you're running Ubuntu, you can upgrade MediaBoom using the Ubuntu PPA. Just follow these steps:

1. Open your terminal emulator and execute the following:
   * `sudo apt update`
2. Upgrade the `mediaboom` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `3`)
   * `sudo apt install mediaboom-3`
3. Start `mediaboom` (appending the same suffix above, like `mediaboom-3`), or use your app drawer to find `MediaBoom` corresponding to your installed API version

You can choose between the version series that you want to upgrade in the output of the `apt` command when it prompts you to select one of them, as `mediaboom` is a virtual package.

{% hint style="danger" %}
This only applies to Ubuntu and its derivatives. However, we only support the vanilla Ubuntu distribution. <mark style="color:red;">**Don't try this method on**</mark> [<mark style="color:red;">**Debian**</mark>](https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian)<mark style="color:red;">**.**</mark>
{% endhint %}

</details>

<details>

<summary>Method 3: Arch Linux AUR</summary>

If you're running Arch, you can upgrade MediaBoom using the Arch Linux AUR. Just follow these steps:

1. Open your terminal emulator and install your preferred AUR helper. Further steps assume that you have [Yay](https://github.com/Jguer/yay) installed.
2. Upgrade the `mediaboom-3` package and follow the instructions (appending the `-XX` suffix to indicate the third API version part, such as `3`)
   * `yay -Sy mediaboom-3`
3. Start `mediaboom` (appending the same suffix above, like `mediaboom-3`), or use your app drawer to find `MediaBoom` corresponding to your installed API version

You can't install the release version and the cutting-edge (those with the `-git` suffix) version at the same time, since files conflict.

{% hint style="info" %}
This only applies to vanilla Arch Linux. We don't officially support Arch's derivatives, such as Manjaro and EndeavourOS.
{% endhint %}

</details>

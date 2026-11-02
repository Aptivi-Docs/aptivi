---
description: Installing MediaBoom on Windows!
icon: windows
---

# Windows

Before performing the installation, your Windows system must meet the following requirements:

| System      | Framework                                                            | Terminal                                                  |
| ----------- | -------------------------------------------------------------------- | --------------------------------------------------------- |
| Windows 10+ | [.NET 10.0](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) | [ConEmu](https://conemu.github.io/) or Windows 10 cmd.exe |

{% hint style="info" %}
We advise you to use the terminal emulation software capable of displaying the VT sequences on systems older than Windows 10. MediaBoom uses Terminaux to render its elements in the CLI player.
{% endhint %}

***

## <mark style="color:$primary;">Installation</mark>

There are several ways to install MediaBoom on Windows systems. We recommend installing MediaBoom using the Chocolatey package manager or the Windows installer for simplicity.

<details>

<summary>Method 1: Using WinGet</summary>

This step-by-step guide shows you how to install MediaBoom using the package manager, [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/winget/#install-winget), assuming that you already have it on your system.

1. Ensure that Chocolatey is installed to your system PATH
2. Open your favorite terminal emulator, like ConEmu, and execute the following command: `winget install --id Aptivi.MediaBoom --source winget`
3. Double-click on `MediaBoom` in your desktop.

</details>

<details>

<summary>Method 2: Using Windows Installer</summary>

The Windows Installer method allows you to easily install MediaBoom.

1. Download the latest Windows Installer EXE file from [this page](https://github.com/Aptivi/MediaBoom/releases)
2. Double-click on a single EXE file, and follow the instructions
3. Double-click on `MediaBoom` in your desktop.

</details>

<details>

<summary>Method 3: Using Chocolatey</summary>

This step-by-step guide shows you how to install MediaBoom using the package manager, [Chocolatey](https://chocolatey.org/install), assuming that you already have it on your system.

1. Ensure that Chocolatey is installed to your system PATH
2. Open your favorite terminal emulator, like ConEmu, and execute the following command: `choco install mediaboom`
3. Start MediaBoom using `mediaboom`

</details>

<details>

<summary>Method 4: Manually unpacking</summary>

If you like to manually unpack the MediaBoom packages, follow these steps:

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/MediaBoom/releases).
3. Unpack the ZIP archive to any folder of your choice using [7-Zip](https://7-zip.org/)
4. Open your favorite terminal emulator, like ConEmu, and change the working directory to a folder containing the MediaBoom executable
5. Execute `mediaboom` or `MediaBoom.Cli.exe` to start the app

</details>

***

## <mark style="color:$primary;">Upgrade</mark>

Upgrading MediaBoom on Windows is pretty simple, depending on the way you've installed it. To upgrade it, choose a method.

<details>

<summary>Method 1: Using WinGet</summary>

Any updates to the MediaBoom WinGet package can be done using a built-in WinGet command. To update the app, follow these steps:

1. Open your favorite terminal emulator, like ConEmu
2. Run `winget upgrade Aptivi.MediaBoom`
3. Once the upgrade is done, run MediaBoom like you normally would

</details>

<details>

<summary>Method 2: Using Windows Installer</summary>

You can update MediaBoom using the Windows Installer method.

1. Download the latest MediaBoom EXE file from [this page](https://github.com/Aptivi/MediaBoom/releases).
2. Double-click on the EXE file and follow the instructions
3. Double-click on `MediaBoom` in your desktop.

</details>

<details>

<summary>Method 3: Using Chocolatey</summary>

Any updates to the MediaBoom Chocolatey package can be done using a built-in Chocolatey command. To update the app, follow these steps:

1. Open your favorite terminal emulator, like ConEmu
2. Run `choco upgrade mediaboom`
3. Once the upgrade is done, run MediaBoom like you normally would

</details>

<details>

<summary>Method 4: Manually unpacking</summary>

MediaBoom can also be manually updated in case the above methods failed. To update MediaBoom, perform the same steps as in installing it.

1. Ensure that you have all the required software installed
2. Download the latest release ZIP file from [this page](https://github.com/Aptivi/MediaBoom/releases).
3. Unpack the ZIP archive to any folder of your choice
4. Open your favorite terminal emulator, like ConEmu, and change the working directory to a folder containing the MediaBoom executable
5. Execute `mediaboom` or `MediaBoom.Cli.exe` to start the kernel

</details>

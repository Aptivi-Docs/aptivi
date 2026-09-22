---
description: How to install BassBoom on FreeBSD
icon: freebsd
---

# FreeBSD

To run BassBoom in the absolute minimum requirements, your computer needs to have the following installed:

| System       | Framework                                                                                      | Terminal                      |
| ------------ | ---------------------------------------------------------------------------------------------- | ----------------------------- |
| FreeBSD 15.0 | [.NET 10.0](https://github.com/sec/dotnet-core-freebsd-source-build/releases/tag/10.0.102-vmr) | Konsole, GNOME Terminal, etc. |

***

## <mark style="color:$primary;">Installation</mark>

There is one way to install BassBoom on FreeBSD systems. Follow these steps to get started:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Check your dependencies</mark>

Ensure that you have all the required software installed
{% endstep %}

{% step %}
### <mark style="color:$primary;">Download the latest ZIP</mark>

Download the latest release ZIP file from [this page](https://github.com/Aptivi/BassBoom/releases).
{% endstep %}

{% step %}
### <mark style="color:$primary;">Extract the archive</mark>

Unpack the ZIP archive to any folder of your choice
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open the terminal emulator</mark>

Open your favorite terminal emulator, like Konsole, and change the working directory to a folder containing the BassBoom executable
{% endstep %}

{% step %}
### <mark style="color:$primary;">Execute BassBoom on your terminal</mark>

Execute `dotnet BassBoom.Cli.dll` to start the app
{% endstep %}
{% endstepper %}

***

## <mark style="color:$primary;">Upgrade</mark>

The only way to upgrade BassBoom in FreeBSD is to unpack the updated files manually. To upgrade, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Download the latest ZIP</mark>

Download the latest release ZIP file from [this page](https://github.com/Aptivi/BassBoom/releases).
{% endstep %}

{% step %}
### <mark style="color:$primary;">Extract the archive</mark>

Unpack the ZIP archive to any folder of your choice
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open the terminal emulator</mark>

Open your favorite terminal emulator, like Konsole, and change the working directory to a folder containing the BassBoom executable
{% endstep %}

{% step %}
### <mark style="color:$primary;">Execute BassBoom on your terminal</mark>

Execute `dotnet BassBoom.Cli.dll` to start the app
{% endstep %}
{% endstepper %}

---
description: >-
  Learn how to disable bad state tracking for Windows to avoid random
  disconnections
icon: wifi-slash
---

# Fix Windows random disconnections

Network Bad State Tracking for Windows has been implemented in Windows 10 and higher. It allows your computer to automatically disconnect your Internet connection, reset the network adapter, and reconnect to your network when your connection is poor or limited.

This feature is not fool-proof, as it also causes your computer to randomly disconnect from the Internet when you're downloading a huge file at full speed; it can't reach the "network check" servers, and your connection is in a state where it needs resetting, though it doesn't happen as often.

The reason that Windows continuously pings the "network check" servers is that because it needs to know whether you're connected to a network that has access to the entire Internet or not. If it can't reach those servers, then this means that you have limited connectivity.

{% hint style="info" %}
This pinging is not the only reason why Windows randomly disconnects your computer from the Internet. There can be many factors of random disconnection, such as outdated device drivers, loose connection to the Wi-Fi adapter, faulty adapter, or, in case of USB dongles, either a faulty USB Wi-Fi dongle or a faulty port.
{% endhint %}

***

## <mark style="color:$primary;">What is NetLimDisable?</mark>

We've implemented a small tool for Windows that allows you to turn off this kind of check to avoid random network disconnections when you're trying to download a huge file at full speed, called NetLimDisable, that is [fully transparent](https://github.com/Aptivi-WPT/NetLimDisable) about the process. It checks for the value of `HKLM\SOFTWARE\Microsoft\WcmSvc\EnableBadStateTracking` in the Windows registry.

* If this value is omitted from the `WcmSvc` key, Windows enables bad state tracking by default.
* If this value is set to `1`, Windows enables bad state tracking.
* If this value is set to `0`, Windows disables bad state tracking.

{% hint style="danger" %}
Before you run this tool or manually edit the registry, ensure that you have backed up the registry as wrong edits to the system registry may damage your system.
{% endhint %}

***

## <mark style="color:$primary;">Usage of NetLimDisable</mark>

To use this program, follow these steps:

{% stepper %}
{% step %}
### <mark style="color:$primary;">Download and extract the tool</mark>

Go to the [releases page](https://github.com/Aptivi-WPT/NetLimDisable/releases) and download the binary ZIP file. Then, extract the ZIP file with your favorite decompression tool (7-Zip, WinRAR, etc.).
{% endstep %}

{% step %}
### <mark style="color:$primary;">Open the executable file</mark>

Open the `NetLimDisable.exe` executable file (requires UAC to be granted)
{% endstep %}

{% step %}
### <mark style="color:$primary;">Set and apply</mark>

Check or uncheck the checkbox that is shown in the below window:

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Then, click on Apply, and you should see the below dialog box:

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### <mark style="color:$primary;">Verify the changes (optional)</mark>

Open the registry editor (`Windows + R` -> `regedit.exe` -> `ENTER`), open the above registry key, and verify that `EnableBadStateTracking` is set to `1` or `0`.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you're still experiencing connection drops, restart your computer and try to perform the same operation.
{% endhint %}

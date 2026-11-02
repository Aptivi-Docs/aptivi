---
description: How do the kernel arguments work? And how do they affect the kernel?
icon: square-sliders
---

# Kernel Arguments

<figure><img src="../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

Kernel Arguments are command-line parameters to the simulator that changes the behavior of the kernel.

The arguments are parsed each time the kernel starts up or gets rebooted. If there are any switches or argument parameters, they'll get parsed using the `ProvidedArgumentsInfo` class.

<details>

<summary>Available arguments</summary>

You can take a look at the available arguments, `--argument`, listed below:

<table><thead><tr><th width="210">Argument</th><th>Description</th></tr></thead><tbody><tr><td><code>help</code></td><td>Shows a list of arguments.</td></tr><tr><td><code>version</code></td><td>Shows the kernel version.</td></tr><tr><td><code>apiversion</code></td><td>Shows the kernel mod API version.</td></tr><tr><td><code>versioncode</code></td><td>Shows the kernel version code.</td></tr><tr><td><code>apiversioncode</code></td><td>Shows the kernel mod API version code.</td></tr><tr><td><code>lang</code></td><td>Chooses a language prior to boot.</td></tr><tr><td><code>attach</code></td><td>Attaches a Visual Studio debugger to the current instance of the kernel (Windows only).</td></tr><tr><td><code>quiet</code></td><td>Starts the kernel quietly.</td></tr><tr><td><code>maintenance</code></td><td>Starts the kernel in maintenance mode which behaves like safe mode but with additional features turned off.</td></tr><tr><td><code>safe</code></td><td>Starts the kernel in safe mode which disables all mods.</td></tr><tr><td><code>testInteractive</code></td><td>Opens the interactive test facade selection.</td></tr><tr><td><code>debug</code></td><td>Enables debug mode.</td></tr><tr><td><code>terminaldebug</code></td><td>Enables terminal debug mode.</td></tr><tr><td><code>reset</code></td><td>Wipes all settings and resets the kernel to factory settings</td></tr><tr><td><code>bypasssizedetection</code></td><td>Bypasses the 80x24 console size detection</td></tr><tr><td><code>noaltbuffer</code></td><td>Prevents the kernel from using the alternative buffer</td></tr><tr><td><code>noprebootsplash</code></td><td>Prevents the kernel from displaying the pre-boot splash</td></tr><tr><td><code>lang &#x3C;lang></code></td><td>Selects a pre-boot environment language</td></tr><tr><td><code>verbosepreboot</code></td><td>Shows extra pre-boot messages</td></tr></tbody></table>

</details>

{% hint style="info" %}
To learn more about `ProvidedArgumentsInfo`, click on the below link:

[Command-Line Arguments](https://app.gitbook.com/s/G0KrE9Uk2AiblqjWtpAo/usage/input-reader/shells/command-line-arguments "mention")
{% endhint %}

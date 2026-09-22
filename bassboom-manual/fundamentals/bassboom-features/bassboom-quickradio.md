---
description: A tiny radio player, just for you.
icon: radio
---

# BassBoom QuickRadio

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

In addition to the fully-fledged radio player, QuickRadio provides you with a tiny command-line program that allows you to specify a path to your radio station. This allows you to quickly play a radio station without having to open any radio player, straight from your terminal emulator.

***

## <mark style="color:$primary;">Usage</mark>

To start using BassBoom.QuickRadio, you'll need to open the terminal emulator and run:

{% code expandable="true" %}
```shellsession
$ dotnet /path/to/BassBoom.QuickRadio.dll --path https://radio.station.com/live
```
{% endcode %}

{% hint style="info" %}
For Ubuntu PPA installations, you can simply execute `bb-radioplay`, providing it with the same arguments.
{% endhint %}

Here are some of the more advanced usages:

<details>

<summary>More switches</summary>

<table><thead><tr><th width="349.666748046875">Switch</th><th>Description</th></tr></thead><tbody><tr><td><code>--path https://radio.station.com/live</code></td><td>Specifies a path to the radio station you wish to play.</td></tr><tr><td><code>--quiet</code></td><td>Specifies whether to hide song information or not.</td></tr></tbody></table>

</details>

<details>

<summary>Keybindings</summary>

<table><thead><tr><th width="125">Keybinding</th><th>Description</th></tr></thead><tbody><tr><td><code>Q</code></td><td>Stops the radio stream and exits the quick player.</td></tr></tbody></table>

</details>


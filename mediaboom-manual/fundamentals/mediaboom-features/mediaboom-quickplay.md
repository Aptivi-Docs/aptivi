---
description: A tiny player, just for you.
icon: play
---

# MediaBoom QuickPlay

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

In addition to the fully-fledged media player, QuickPlay provides you with a tiny command-line program that allows you to specify a path to your media file. This allows you to quickly play a media file without having to open any player, straight from your terminal emulator.

***

## <mark style="color:$primary;">Usage</mark>

To start using MediaBoom.QuickPlay, you'll need to open the terminal emulator and run:

{% code expandable="true" %}
```shellsession
$ dotnet /path/to/MediaBoom.QuickPlay.dll --path /path/to/media_file
```
{% endcode %}

{% hint style="info" %}
For Ubuntu PPA installations, you can simply execute `mb-sndplay`, providing it with the same arguments.
{% endhint %}

Here are some of the more advanced usages:

<details>

<summary>More switches</summary>

<table><thead><tr><th width="249.666748046875">Switch</th><th>Description</th></tr></thead><tbody><tr><td><code>--path /path/to/media_file</code></td><td>Specifies a path to the media file you wish to play.</td></tr><tr><td><code>--quiet</code></td><td>Specifies whether to hide media information or not.</td></tr></tbody></table>

</details>

<details>

<summary>Keybindings</summary>

<table><thead><tr><th width="125">Keybinding</th><th>Description</th></tr></thead><tbody><tr><td><code>Q</code></td><td>Stops media and exits the quick player.</td></tr></tbody></table>

</details>

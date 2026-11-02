---
description: Media player in your console!
icon: music
---

# MediaBoom CLI

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

MediaBoom provides you its CLI version that allows you to play any media using just your terminal emulator. You can use this version if you need no GUI and just want to play media using just the textual UI.

{% hint style="info" %}
Since the TUI version uses Terminaux to render its elements, you need to have a terminal emulator which supports VT sequences out of the box.
{% endhint %}

***

## <mark style="color:$primary;">Usage</mark>

You can run this program by either double-clicking an executable file, which will prompt you for the full path to a music file, or by opening the command prompt to the MediaBoom.Cli binaries directory and writing the command like this:

* For Windows, `MediaBoom.Cli.exe --path path/to/media_file`
* For Linux, `dotnet MediaBoom.Cli.dll --path path/to/media_file`

<details>

<summary>What about radio?</summary>

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Additionally, you can use this program to run it as a radio station player using the `--radio` switch without providing any argument.

* For Windows, `MediaBoom.Cli.exe --radio`
* For Linux, `dotnet MediaBoom.Cli.dll --radio`

Alternatively, you can specify a path to a radio station like this:

* For Windows, `MediaBoom.Cli.exe --radio --path https://radio.station.com/live`
* For Linux, `dotnet MediaBoom.Cli.dll --radio --path https://radio.station.com/live`

Once done, MediaBoom opens your radio station to be ready for playing. Just play your favorite radio station by pressing the spacebar.

</details>

***

## <mark style="color:$primary;">Controls</mark>

You can use the following keys to navigate through the entire music player or the radio player. However, there are keys that don't do anything in modes that don't define such keys. You can consult a list of keys available to you by pressing the `H` key.

<details>

<summary>Idle mode (player)</summary>

When MediaBoom.Cli is in idle mode (media not playing, media paused, etc.), you can use the following controls:

<table><thead><tr><th width="120.33331298828125">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>SPACE</code></td><td>Plays media</td></tr><tr><td><code>B</code></td><td>Goes back to the previous media in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next media in the playlist and plays it</td></tr><tr><td><code>H</code></td><td>Shows the help menu</td></tr><tr><td><code>I</code></td><td>Shows the media information.</td></tr><tr><td><code>A</code></td><td>Adds a single media to the playlist</td></tr><tr><td><code>SHIFT + A</code></td><td>Adds multiple media from a playlist file</td></tr><tr><td><code>S</code></td><td>Adds songs from a media library directory to the playlist</td></tr><tr><td><code>R</code></td><td>Removes the current media</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the media</td></tr><tr><td><code>Z</code></td><td>Shows MediaBoom and platform information</td></tr><tr><td><code>C</code></td><td>Sets the repeat checkpoint (a.k.a. seek point)</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>F2</code></td><td>Play test sound</td></tr><tr><td><code>Q</code></td><td>Exits the program</td></tr></tbody></table>

</details>

<details>

<summary>Playing mode (player)</summary>

When MediaBoom.Cli goes into this mode by playing any media, you can use these controls:

<table><thead><tr><th width="130">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>RIGHT</code></td><td>Seeks the media forward by the set seek rate</td></tr><tr><td><code>CTRL + RIGHT</code></td><td>Increases the seek rate by 50 milliseconds</td></tr><tr><td><code>LEFT</code></td><td>Seeks the media backward by the set seek rate</td></tr><tr><td><code>CTRL + LEFT</code></td><td>Decreases the seek rate by 50 milliseconds</td></tr><tr><td><code>B</code></td><td>Goes back to the previous media in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next media in the playlist and plays it</td></tr><tr><td><code>SPACE</code></td><td>Pauses media</td></tr><tr><td><code>R</code></td><td>Removes the currently playing media</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the media</td></tr><tr><td><code>ESC</code></td><td>Stops the media</td></tr><tr><td><code>H</code></td><td>Shows the help screen</td></tr><tr><td><code>I</code></td><td>Shows the media info</td></tr><tr><td><code>D</code></td><td>Displays video (if any)</td></tr><tr><td><code>Z</code></td><td>Shows MediaBoom and platform information</td></tr><tr><td><code>S</code></td><td>Selectively seeks to the selected position</td></tr><tr><td><code>F</code></td><td>Seeks to the previous lyric</td></tr><tr><td><code>G</code></td><td>Seeks to the next lyric</td></tr><tr><td><code>J</code></td><td>Seeks to the current lyric</td></tr><tr><td><code>K</code></td><td>Seeks to the selected lyric</td></tr><tr><td><code>L</code></td><td>Disco mode!</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>Q</code></td><td>Exits BassBoom.Cli</td></tr></tbody></table>

</details>

<details>

<summary>Idle mode (radio)</summary>

When MediaBoom.Cli is in idle mode (radio station not playing, radio station paused, etc.), you can use the following controls:

<table><thead><tr><th width="120.33331298828125">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>SPACE</code></td><td>Plays the radio station</td></tr><tr><td><code>B</code></td><td>Goes back to the previous radio station in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next radio station in the playlist and plays it</td></tr><tr><td><code>H</code></td><td>Shows the help menu</td></tr><tr><td><code>I</code></td><td>Shows the radio station information</td></tr><tr><td><code>CTRL + I</code></td><td>Shows the extended radio station information</td></tr><tr><td><code>A</code></td><td>Adds a single radio station to the playlist</td></tr><tr><td><code>SHIFT + A</code></td><td>Adds multiple radio stations from a playlist file</td></tr><tr><td><code>R</code></td><td>Removes the current radio station</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the radio stations</td></tr><tr><td><code>Z</code></td><td>Shows MediaBoom and platform information</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>Q</code></td><td>Exits the program</td></tr></tbody></table>

</details>

<details>

<summary>Playing mode (radio)</summary>

When MediaBoom.Cli goes into this mode by playing any radio station, you can use these controls:

<table><thead><tr><th width="140">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>B</code></td><td>Goes back to the previous radio station in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next radio station in the playlist and plays it</td></tr><tr><td><code>SPACE</code></td><td>Pauses the radio station</td></tr><tr><td><code>R</code></td><td>Removes the currently playing radio station</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the radio stations</td></tr><tr><td><code>ESC</code></td><td>Stops the radio station</td></tr><tr><td><code>H</code></td><td>Shows the help screen</td></tr><tr><td><code>I</code></td><td>Shows the radio station info</td></tr><tr><td><code>D</code></td><td>Displays video (if any)</td></tr><tr><td><code>L</code></td><td>Disco mode!</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>Q</code></td><td>Exits MediaBoom.Cli</td></tr></tbody></table>

</details>

***

## <mark style="color:$primary;">Other screens</mark>

The MediaBoom CLI application provides other screens for you to use, with the following screens available:

<details>

<summary>Video display screen</summary>

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

If you're playing a video file, you can make it display a video in the terminal.

The following controls are available:

<table><thead><tr><th width="110.3333740234375">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>Q</code></td><td>Goes back to the player</td></tr></tbody></table>

</details>

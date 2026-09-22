---
description: Music player in your console!
icon: music
---

# BassBoom CLI

<figure><img src="../../.gitbook/assets/music.png" alt=""><figcaption></figcaption></figure>

BassBoom provides you its CLI version that allows you to play any music using just your terminal emulator. You can use this version if you need no GUI and just want to play music using just the textual UI.

{% hint style="info" %}
Since the TUI version uses Terminaux to render its elements, you need to have a terminal emulator which supports VT sequences out of the box.
{% endhint %}

***

## <mark style="color:$primary;">Usage</mark>

You can run this program by either double-clicking an executable file, which will prompt you for the full path to a music file, or by opening the command prompt to the BassBoom.Cli binaries directory and writing the command like this:

* For Windows, `BassBoom.Cli.exe --path path/to/music.mp3`
* For Linux, `dotnet BassBoom.Cli.dll --path path/to/music.mp3`

<details>

<summary>What about radio?</summary>

<figure><img src="../../.gitbook/assets/radio.png" alt=""><figcaption></figcaption></figure>

Additionally, you can use this program to run it as a radio station player using the `--radio` switch without providing any argument.

* For Windows, `BassBoom.Cli.exe --radio`
* For Linux, `dotnet BassBoom.Cli.dll --radio`

Alternatively, you can specify a path to a radio station like this:

* For Windows, `BassBoom.Cli.exe --radio --path https://radio.station.com/live`
* For Linux, `dotnet BassBoom.Cli.dll --radio --path https://radio.station.com/live`

Once done, BassBoom opens your radio station to be ready for playing. Just play your favorite radio station by pressing the spacebar.

{% hint style="warning" %}
If you found a radio station that only uses AAC, AAC+, or any other non-MPEG streams, try to consult the radio station host for an MPEG stream, if available.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Controls</mark>

You can use the following keys to navigate through the entire music player or the radio player. However, there are keys that don't do anything in modes that don't define such keys. You can consult a list of keys available to you by pressing the `H` key.

<details>

<summary>Idle mode (player)</summary>

When BassBoom.Cli is in idle mode (music not playing, music paused, etc.), you can use the following controls:

<table><thead><tr><th width="120.33331298828125">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>SPACE</code></td><td>Plays the music</td></tr><tr><td><code>B</code></td><td>Goes back to the previous song in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next song in the playlist and plays it</td></tr><tr><td><code>H</code></td><td>Shows the help menu</td></tr><tr><td><code>I</code></td><td>Shows the song information, including the bit rate, artist, genre, etc.</td></tr><tr><td><code>A</code></td><td>Adds a single song to the playlist</td></tr><tr><td><code>SHIFT + A</code></td><td>Adds multiple songs from a playlist file</td></tr><tr><td><code>S</code></td><td>Adds songs from a music library directory to the playlist</td></tr><tr><td><code>R</code></td><td>Removes the current song</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the songs</td></tr><tr><td><code>E</code></td><td>Opens the interactive equalizer</td></tr><tr><td><code>Z</code></td><td>Shows BassBoom and platform information</td></tr><tr><td><code>SHIFT + Z</code></td><td>Shows BassBoom and platform information, with extra debug info</td></tr><tr><td><code>D</code></td><td>Shows all devices and drivers probed by MPG123</td></tr><tr><td><code>CTRL + D</code></td><td>Sets a device and driver</td></tr><tr><td><code>SHIFT + D</code></td><td>Resets a device and driver selection</td></tr><tr><td><code>C</code></td><td>Sets the repeat checkpoint (a.k.a. seek point)</td></tr><tr><td><code>SHIFT + C</code></td><td>Seeks to the repeat checkpoint (a.k.a. seek point)</td></tr><tr><td><code>V</code></td><td>Opens the visualizer</td></tr><tr><td><code>SHIFT + V</code></td><td>Enables volume boost</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>F2</code></td><td>Play test sound</td></tr><tr><td><code>Q</code></td><td>Exits the program</td></tr></tbody></table>

</details>

<details>

<summary>Playing mode (player)</summary>

When BassBoom.Cli goes into this mode by playing any music, you can use these controls:

<table><thead><tr><th width="130">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>RIGHT</code></td><td>Seeks the music forward by the set seek rate</td></tr><tr><td><code>CTRL + RIGHT</code></td><td>Increases the seek rate by 50 milliseconds</td></tr><tr><td><code>LEFT</code></td><td>Seeks the music backward by the set seek rate</td></tr><tr><td><code>CTRL + LEFT</code></td><td>Decreases the seek rate by 50 milliseconds</td></tr><tr><td><code>B</code></td><td>Goes back to the previous song in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next song in the playlist and plays it</td></tr><tr><td><code>SPACE</code></td><td>Pauses the music</td></tr><tr><td><code>R</code></td><td>Removes the currently playing song</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the songs</td></tr><tr><td><code>ESC</code></td><td>Stops the song</td></tr><tr><td><code>H</code></td><td>Shows the help screen</td></tr><tr><td><code>I</code></td><td>Shows the song info</td></tr><tr><td><code>E</code></td><td>Opens the interactive equalizer</td></tr><tr><td><code>D</code></td><td>Shows all devices and drivers probed by MPG123</td></tr><tr><td><code>CTRL + D</code></td><td>Sets a device and driver</td></tr><tr><td><code>SHIFT + D</code></td><td>Resets a device and driver selection</td></tr><tr><td><code>Z</code></td><td>Shows BassBoom and platform information</td></tr><tr><td><code>SHIFT + Z</code></td><td>Shows BassBoom and platform information, with extra debug info</td></tr><tr><td><code>S</code></td><td>Selectively seeks to the selected position</td></tr><tr><td><code>F</code></td><td>Seeks to the previous lyric</td></tr><tr><td><code>G</code></td><td>Seeks to the next lyric</td></tr><tr><td><code>J</code></td><td>Seeks to the current lyric</td></tr><tr><td><code>K</code></td><td>Seeks to the selected lyric</td></tr><tr><td><code>C</code></td><td>Sets the repeat checkpoint (a.k.a. seek point)</td></tr><tr><td><code>SHIFT + C</code></td><td>Seeks to the repeat checkpoint (a.k.a. seek point)</td></tr><tr><td><code>V</code></td><td>Opens the visualizer</td></tr><tr><td><code>SHIFT + V</code></td><td>Enables volume boost</td></tr><tr><td><code>L</code></td><td>Disco mode!</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>Q</code></td><td>Exits BassBoom.Cli</td></tr></tbody></table>



</details>

<details>

<summary>Idle mode (radio)</summary>

When BassBoom.Cli is in idle mode (radio station not playing, radio station paused, etc.), you can use the following controls:

<table><thead><tr><th width="120.33331298828125">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>SPACE</code></td><td>Plays the radio station</td></tr><tr><td><code>B</code></td><td>Goes back to the previous radio station in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next radio station in the playlist and plays it</td></tr><tr><td><code>H</code></td><td>Shows the help menu</td></tr><tr><td><code>I</code></td><td>Shows the radio station information, including the bit rate, artist, genre, etc.</td></tr><tr><td><code>CTRL + I</code></td><td>Shows the extended radio station information</td></tr><tr><td><code>A</code></td><td>Adds a single radio station to the playlist</td></tr><tr><td><code>SHIFT + A</code></td><td>Adds multiple songs from a playlist file</td></tr><tr><td><code>R</code></td><td>Removes the current radio station</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the radio stations</td></tr><tr><td><code>E</code></td><td>Opens the interactive equalizer</td></tr><tr><td><code>Z</code></td><td>Shows BassBoom and platform information</td></tr><tr><td><code>SHIFT + Z</code></td><td>Shows BassBoom and platform information, with extra debug info</td></tr><tr><td><code>D</code></td><td>Shows all devices and drivers probed by MPG123</td></tr><tr><td><code>CTRL + D</code></td><td>Sets a device and driver</td></tr><tr><td><code>SHIFT + D</code></td><td>Resets a device and driver selection</td></tr><tr><td><code>V</code></td><td>Opens the visualizer</td></tr><tr><td><code>SHIFT + V</code></td><td>Enables volume boost</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>Q</code></td><td>Exits the program</td></tr></tbody></table>

</details>

<details>

<summary>Playing mode (radio)</summary>

When BassBoom.Cli goes into this mode by playing any music, you can use these controls:

<table><thead><tr><th width="140">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>UP</code></td><td>Raises the volume</td></tr><tr><td><code>DOWN</code></td><td>Lowers the volume</td></tr><tr><td><code>RIGHT</code></td><td>Seeks the music forward by the set seek rate</td></tr><tr><td><code>CTRL + RIGHT</code></td><td>Increases the seek rate by 50 milliseconds</td></tr><tr><td><code>LEFT</code></td><td>Seeks the music backward by the set seek rate</td></tr><tr><td><code>CTRL + LEFT</code></td><td>Decreases the seek rate by 50 milliseconds</td></tr><tr><td><code>B</code></td><td>Goes back to the previous song in the playlist and plays it</td></tr><tr><td><code>N</code></td><td>Goes to the next song in the playlist and plays it</td></tr><tr><td><code>SPACE</code></td><td>Pauses the music</td></tr><tr><td><code>R</code></td><td>Removes the currently playing song</td></tr><tr><td><code>CTRL + R</code></td><td>Removes all the songs</td></tr><tr><td><code>ESC</code></td><td>Stops the song</td></tr><tr><td><code>H</code></td><td>Shows the help screen</td></tr><tr><td><code>I</code></td><td>Shows the song info</td></tr><tr><td><code>E</code></td><td>Opens the interactive equalizer</td></tr><tr><td><code>D</code></td><td>Shows all devices and drivers probed by MPG123</td></tr><tr><td><code>CTRL + D</code></td><td>Sets a device and driver</td></tr><tr><td><code>SHIFT + D</code></td><td>Resets a device and driver selection</td></tr><tr><td><code>Z</code></td><td>Shows BassBoom and platform information</td></tr><tr><td><code>SHIFT + Z</code></td><td>Shows BassBoom and platform information, with extra debug info</td></tr><tr><td><code>V</code></td><td>Opens the visualizer</td></tr><tr><td><code>SHIFT + V</code></td><td>Enables volume boost</td></tr><tr><td><code>L</code></td><td>Disco mode!</td></tr><tr><td><code>F1</code></td><td>Save the current playlist to a playlist file (M3U or M3U8)</td></tr><tr><td><code>Q</code></td><td>Exits BassBoom.Cli</td></tr></tbody></table>

</details>

***

## <mark style="color:$primary;">Other screens</mark>

The BassBoom CLI application provides other screens for you to use, with the following screens available:

<details>

<summary>Equalizer screen</summary>

<figure><img src="../../.gitbook/assets/equalizer.png" alt=""><figcaption></figcaption></figure>

You can also modify how your song or your radio station plays like in real-time using the interactive equalizer.

The following controls are available:

<table><thead><tr><th width="110.3333740234375">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>&#x3C;-</code> / <code>-></code></td><td>Changes the current equalizer band's value</td></tr><tr><td><code>UP</code> / <code>DOWN</code></td><td>Selects the equalizer band</td></tr><tr><td><code>R</code></td><td>Resets all values</td></tr><tr><td><code>D</code></td><td>Shows or hides device bands</td></tr><tr><td><code>Q</code></td><td>Goes back to the player</td></tr></tbody></table>

</details>

<details>

<summary>Visualizer screen</summary>

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

You can visualize how a song is played, with different kinds of visualizers that are available, starting from BassBoom v1.0.1.

The following controls are available:

<table><thead><tr><th width="110.3333740234375">Control</th><th>Action</th></tr></thead><tbody><tr><td><code>&#x3C;-</code> / <code>-></code></td><td>Changes the current visualizer</td></tr><tr><td><code>M</code></td><td>Changes the current visualizer's behavior</td></tr><tr><td><code>Q</code></td><td>Goes back to the player</td></tr></tbody></table>

</details>

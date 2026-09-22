---
description: Play your music!
icon: play
---

# Playback

The playback tools in the Basolia library contains two separate sections: the actual playback tools and the playback positioning tools.

***

## <mark style="color:$primary;">Playback tools</mark>

The playback tools shipped with the Basolia library is a key feature for every single music player.

<details>

<summary>Playing music</summary>

There are two ways to play the music: synchronously and asynchronously. For normal console applications, you'd typically use `Play()` for a single audio player, or this function in a thread for a music player, such as BassBoom.Cli.

```csharp
public void Play() { }
```

However, for GUI applications, it's best to use the asynchronous version whenever possible, `PlayAsync()`, to avoid blocking the main thread.

```csharp
public async Task PlayAsync() { }
```

</details>

<details>

<summary>Pausing and stopping music</summary>

If you want to pause the music, you can use the `Pause()` function. It'll stop the music, but stays at the current position. If you want to start over, you can use the `Stop()` function.

```csharp
public void Pause() { }
public void Stop() { }
```

</details>

<details>

<summary>Volume Controls</summary>

For controlling the volume that the Basolia library controls, you can use both the `SetVolume()` and the `GetVolume()` functions.

`SetVolume()` allows you to set the current volume to the new volume from 0.0 (0%) to 1.0 (100%). Additionally, if you've enabled the volume boost option, you can set the volume up to 3.0 (300%), though this may cause audio artifacts in some cases where parts of an audio file is loud.

```csharp
public void SetVolume(double volume, bool volBoost = false) { }
```

Getting the current volume using the `GetVolume()` function returns three variables that describe the following:

<table><thead><tr><th width="141">Variable</th><th>Description</th></tr></thead><tbody><tr><td><code>baseLinear</code></td><td>The base linear volume from 0.0 to 1.0</td></tr><tr><td><code>actualLinear</code></td><td>The actual linear volume from 0.0 to 1.0</td></tr><tr><td><code>decibelsRva</code></td><td>The RVA value in decibels (dB)</td></tr></tbody></table>

```csharp
public (double baseLinear, double actualLinear, double decibelsRva) GetVolume() { }
```

</details>

<details>

<summary>Playback states</summary>

When either `Play()`, `Pause()`, or `Stop()` functions are called, the playback state changes, depending on the action. You can get the current playback state by using the `GetState` function.

```csharp
public PlaybackState GetState() { }
```

You can also quickly determine whether Basolia is busy playing a song using the `IsPlaying` function:

```csharp
public bool IsPlaying() { }
```

The playback states are the following:

<table><thead><tr><th width="109">State</th><th>Description</th></tr></thead><tbody><tr><td><code>Stopped</code></td><td>Music has either stopped or not played yet</td></tr><tr><td><code>Playing</code></td><td>Music is playing</td></tr><tr><td><code>Paused</code></td><td>Music has been paused by the user or by the call to the <code>Pause()</code> function</td></tr></tbody></table>

</details>

<details>

<summary>Opening the output</summary>

If you want to open the output to your selected device and driver or to a pre-determined device and driver as selected by your OS, you can use the below function:

```csharp
public void OpenOutput() { }
```

{% hint style="info" %}
You don't usually need to call this function, unless you have a reason to. Playback tools already use this function internally.
{% endhint %}

</details>

<details>

<summary>Starting the output</summary>

If you want to start the output at a selected rate, channel count, and encoding, you can use the below function:

```csharp
public void StartOutput(long rate, ChannelCount channels, int encoding) { }
```

{% hint style="info" %}
You don't usually need to call this function, unless you have a reason to. Playback tools already use this function internally.
{% endhint %}

</details>

<details>

<summary>Closing the output</summary>

If you no longer want to output anything, you can use this function:

```csharp
public void CloseOutput() { }
```

{% hint style="danger" %}
Use this function carefully, as reckless usage could cause the underlying application to crash with an access violation error.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Play'n'Forget</mark>

If you don't want to set up a persistent `BasoliaMedia` instance for every operation, you can use this technique to implement Play'n'Forget in your applications so that you can play either a file or a stream without any difficulty. The below functions can be found in the `BassBoom.Basolia.Media.Independent` namespace.

{% hint style="info" %}
If you want to change a specific setting, you should create a class instance of `PlayForgetSettings` that consists of:

* `Volume` (settable and constructible)
* `VolumeBoost` (settable and constructible)
* `RootLibPath` (constructible, but not modifiable)

Be careful about the `RootLibPath` settings entry, as it gets ignored right after Basolia verifies that the library is loaded for the first time.
{% endhint %}

<details>

<summary>Playing a file</summary>

There are two ways to play a file: synchronously and asynchronously.

```csharp
public static void PlayFile(string path, PlayForgetSettings? settings = null) { }
public static async Task PlayFileAsync(string path, PlayForgetSettings? settings = null) { }
```

Just call one of these functions, passing it either an absolute path or a relative path to your music file, optionally passing it the Play'n'Forget settings instance.

</details>

<details>

<summary>Playing a stream</summary>

There are two ways to play a stream: synchronously and asynchronously.

```csharp
public static void PlayStream(Stream stream, PlayForgetSettings? settings = null) { }
public static async Task PlayStreamAsync(Stream stream, PlayForgetSettings? settings = null) { }
```

Just call one of these functions, passing it a **seekable** stream containing MP3 data of your song file, optionally passing it the Play'n'Forget settings instance.

{% hint style="danger" %}
Radio stations and other non-seekable streams are not supported as Basolia requires a stream to be seekable for non-radio-station streams. In addition to that, radio stations can't be "forgotten" as it's an infinite stream.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Positioning tools</mark>

In addition to the playback tools, you can also get access to the positioning tools to perform seek operations to jump to a specific section of a song, regardless of whether the song is playing or not.

<details>

<summary>Current duration</summary>

You can get the current duration in two units: Samples and time span. If you want to get the current duration using the samples, you can use the `GetCurrentDuration()` function:

```csharp
public int GetCurrentDuration() { }
```

Similarly, you can also get the current duration in the timespan for easier representation by using the `GetCurrentDurationSpan()` function:

```csharp
public TimeSpan GetCurrentDurationSpan() { }
```

</details>

<details>

<summary>Seeking controls</summary>

If you want to seek the music file either to a selected position using a frame number or to the beginning of the song (frame 0), you can simply use one of the two functions:

```csharp
// For seeking to the beginning
public void SeekToTheBeginning() { }

// For seeking to a specific MPEG frame
public void SeekToFrame(int frame) { }

// For seeking to a specific lyric line
public void SeekLyric(LyricLine lyricLine) { }
```

</details>

<details>

<summary>Dropping MPEG frames</summary>

If you want to flush all MPEG frames to the device for any reason, you can use this function:

```csharp
public void Drop() { }
```

</details>

***

## <mark style="color:$primary;">Equalizer tools</mark>

BassBoom's Basolia library also allows you to modify the equalizer settings during playback so that you can listen to enhanced music. It currently supports 32 bands as MPG123 supports.

{% hint style="info" %}
You can run this tool on either left, right, or both speakers.
{% endhint %}

<details>

<summary>Getting current equalizer values</summary>

If you want to get the current equalizer values, you can use the below function:

```csharp
public double GetEqualizer(mpg123_channels channels, int bandIdx) { }
```

</details>

<details>

<summary>Setting equalizer values</summary>

If you want to set the equalizer values for one or more bands to make your music sound better, you can use the below function:

```csharp
// For one band
public void SetEqualizer(mpg123_channels channels, int bandIdx, double value) { }

// For more than one bands
public void SetEqualizerRange(mpg123_channels channels, int bandIdxStart, int bandIdxEnd, double value) { }
```

</details>

<details>

<summary>Resetting equalizer values</summary>

If you want to reset the equalizer values to their natural states (`1.00`), you can use the below function:

```csharp
public void ResetEqualizer() { }
```

</details>

<details>

<summary>Getting native state</summary>

If you want to get the native state of the output stream that represents the currently playing music, you can use this function:

```csharp
public (long, double) GetNativeState(mpg123_state state) { }
```

The `mpg123_state` enumeration has the following states for you to get:

| State                  | Description                  |
| ---------------------- | ---------------------------- |
| `MPG123_ACCURATE`      | Accurate rendering           |
| `MPG123_BUFFERFILL`    | Buffer fill                  |
| `MPG123_DEC_DELAY`     | Decode delay in milliseconds |
| `MPG123_ENC_DELAY`     | Encode delay in milliseconds |
| `MPG123_ENC_PADDING`   | Encoding padding             |
| `MPG123_FRANKENSTEIN`  | Frankenstein stream?         |
| `MPG123_FRESH_DECODER` | Fresh decoder                |

</details>

***

## <mark style="color:$primary;">Visualizer tools</mark>

BassBoom's Basolia library also allows you to listen to the frequency and sample data across all bands, from bass to treble, and to allow you to measure the loudness of the music being played.

<details>

<summary>Listening to frequency band changes</summary>

Basolia provides you with an event called `FrequencyBandsChanged` that allows you to get raw values of 32 frequency bands that range from the lowest to the highest.

This event will get fired during the whole playback, and it will provide you with an array of normalized band frequency values, which you'll then have to use to create a visualizer.

{% hint style="info" %}
We recommend that you cache this value so that your visualizer produces accurate viewing, like in this example:

{% code expandable="true" %}
```csharp
float[] cachedBands = new float[32];
Visualizer.bands.CopyTo(cachedBands, 0);
```
{% endcode %}
{% endhint %}

This allows you to build frequency bars where you get the loudness of each band, such as bass, mid, and treble bands.

</details>

<details>

<summary>Listening to volume changes</summary>

Basolia provides you with an event called `SamplingDataChanged` that allows you to get raw values of sampling data for two channels: left and right.

This event will get fired during the whole playback, and it will provide you with a tuple of sample values for both the left and the right channels, which you'll then have to use to create an oscilloscope.

{% hint style="info" %}
We recommend that you cache this value so that your visualizer produces accurate viewing, like in this example:

{% code expandable="true" %}
```csharp
int width = ConsoleWrapper.WindowWidth;
float[] cachedStereoLeft = new float[Visualizer.sample.left.Length];
float[] cachedStereoRight = new float[Visualizer.sample.right.Length];
Visualizer.sample.left.CopyTo(cachedStereoLeft, 0);
Visualizer.sample.right.CopyTo(cachedStereoRight, 0);
var downsampledLeft = FormatTools.DownsampleSamples(cachedStereoLeft, width);
var downsampledRight = FormatTools.DownsampleSamples(cachedStereoRight, width);
```
{% endcode %}

You'll have to downsample the values yourself, and the format tools will provide you with a function you can call, which is `DownsampleSamples()`.
{% endhint %}

This allows you to build oscilloscopes where you can measure the loudness of the music.

</details>

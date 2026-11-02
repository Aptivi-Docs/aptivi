---
description: Play your music!
icon: play
---

# Playback

The playback tools in the Basolia library contains two separate sections: the actual playback tools and the playback positioning tools.

***

## <mark style="color:$primary;">Playback tools</mark>

The playback tools shipped with the Basolia library is a key feature for every single media player.

<details>

<summary>Playing media</summary>

There are two ways to play media: synchronously and asynchronously. For normal console applications, you'd typically use `Play()` for a single media player, or this function in a thread for a media player, such as MediaBoom.Cli.

```csharp
public void Play() { }
```

However, for GUI applications, it's best to use the asynchronous version whenever possible, `PlayAsync()`, to avoid blocking the main thread.

```csharp
public async Task PlayAsync() { }
```

</details>

<details>

<summary>Pausing and stopping media</summary>

If you want to pause media, you can use the `Pause()` function. It'll stop media, but stays at the current position. If you want to start over, you can use the `Stop()` function.

```csharp
public void Pause() { }
public void Stop() { }
```

</details>

<details>

<summary>Volume Controls</summary>

For controlling the volume that the Basolia library controls, you can use both the `SetVolume()` and the `GetVolume()` functions.

`SetVolume()` allows you to set the current volume to the new volume from 0 (0%) to 100 (100%).

```csharp
public void SetVolume(double volume) { }
```

Getting the current volume using the `GetVolume()` function returns the base linear volume from 0 to 100.

```csharp
public double GetVolume() { }
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

You can also check to see whether the currently playing media is a video or not:

```csharp
public bool IsVideo() { }
```

The playback states are the following:

<table><thead><tr><th width="109">State</th><th>Description</th></tr></thead><tbody><tr><td><code>Stopped</code></td><td>Media has either stopped or not played yet</td></tr><tr><td><code>Playing</code></td><td>Media is playing</td></tr><tr><td><code>Paused</code></td><td>Media has been paused by the user or by the call to the <code>Pause()</code> function</td></tr><tr><td><code>Stopping</code></td><td>Basolia is waiting for media to stop.</td></tr><tr><td><code>Pausing</code></td><td>Basolia is waiting for media to pause.</td></tr></tbody></table>

</details>

***

## <mark style="color:$primary;">Play'n'Forget</mark>

If you don't want to set up a persistent `BasoliaMedia` instance for every operation, you can use this technique to implement Play'n'Forget in your applications so that you can play either a file or a stream without any difficulty. The below functions can be found in the `MediaBoom.Basolia.Media.Independent` namespace.

{% hint style="info" %}
If you want to change a specific setting, you should create a class instance of `PlayForgetSettings` that consists of:

* `Volume` (settable and constructible)
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

Just call one of these functions, passing it either an absolute path or a relative path to your media file, optionally passing it the Play'n'Forget settings instance.

</details>

<details>

<summary>Playing a stream</summary>

There are two ways to play a stream: synchronously and asynchronously.

```csharp
public static void PlayStream(Stream stream, PlayForgetSettings? settings = null) { }
public static async Task PlayStreamAsync(Stream stream, PlayForgetSettings? settings = null) { }
```

Just call one of these functions, passing it a **seekable** stream containing data of your media file, optionally passing it the Play'n'Forget settings instance.

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

If you want to seek the music file either to a selected position using either a number of seconds or to the beginning of the song, you can simply use one of the two functions:

```csharp
// For seeking to the beginning
public void SeekToTheBeginning() { }

// For seeking to a specific second
public void SeekTo(long second) { }
```

</details>

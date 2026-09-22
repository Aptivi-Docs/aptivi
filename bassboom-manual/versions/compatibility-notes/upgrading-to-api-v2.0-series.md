---
description: >-
  Follow the compatibility notes when upgrading BassBoom.Basolia to API v2.0
  series
icon: up
---

# Upgrading to API v2.0 series

If you are an app developer, and you plan to upgrade BassBoom.Basolia to API v2.0 version series, you'll need to consider the following breaking changes:

***

## <mark style="color:$primary;">From 0.2.1.x to v1.0.0.x</mark>

When upgrading BassBoom from 0.2.1.x to 1.0.0.x, you need to consider the following changes:

<details>

<summary>Moved classes and enumerations to <code>BassBoom.Basolia.Media</code></summary>

As part of the BassBoom.Basolia library restructure that happened in v1.0.0, we've decided to move the following classes and enumerations to `BassBoom.Basolia.Media`:

* `Albums.MusicFileLabeler`
* `Enumerations.FrameFlags`
* `Enumerations.FrameMode`
* `Enumerations.FrameVbr`
* `Enumerations.FrameVersion`
* `Enumerations.PlaybackChannels`
* `Enumerations.PlaybackStateType`
* `File.FileType`
* `Format.ChannelCount`
* `Format.FormatInfo`
* `Format.FormatTools`
* `Format.FrameInfo`
* `Format.IdV1Genre`
* `Format.IdV1Metadata`
* `Format.IdV2Metadata`
* `Independent.PlayForget`
* `Independent.PlayForgetSettings`
* `Lyrics.Lyric`
* `Lyrics.LyricLine`
* `Lyrics.LyricLineWord`
* `Lyrics.LyricReader`
* `Playback.Playlists.Enumerations.SongType`
* `Playback.Playlists.Instances.TrackInfo`
* `Playback.Playlists.Playlist`
* `Playback.Playlists.PlaylistConstants`
* `Playback.Playlists.PlaylistParser`
* `Playback.PlaybackState`
* `Radio.IcecastServer`
* `Radio.IRadioServer`
* `Radio.RadioServerType`
* `Radio.RadioTools`
* `Radio.ShoutcastServer`
* `Radio.ShoutcastVersion`
* `Radio.StreamInfo`
* `BasoliaMedia`

{% hint style="info" %}
Update your `using` statements to include the new namespace locations.
{% endhint %}

</details>

<details>

<summary>Moved media functions to <code>BasoliaMedia</code></summary>

We've managed to utilize partial classes to reduce complexity when it comes to `BasoliaMedia`'s implementation. As a result, the codebase is now cleaner and more concise; the `BasoliaMedia` class is no longer a tabloid class.

As a result, we have to remove the following tools classes:

* `Devices.DeviceTools`
* `File.FileTools`
* `Format.AudioInfoTools`
* `Format.DecodeTools`
* `Playback.PlaybackTools`
* `Playback.PlaybackPositioningTools`

Their functions now no longer require supplying a BasoliaMedia instance. However, they must be called from that instance.

However, `Format.FormatTools` was moved to `BassBoom.Basolia.Media` as the functions that are defined on that class don't depend on `BasoliaMedia`.

{% hint style="info" %}
Update all your function calls to point to a `BasoliaMedia` instance while removing the BasoliaMedia instance argument.
{% endhint %}

</details>

---
description: Play this before this...
icon: piano-keyboard
---

# Playlists

Playlists are a group of music files or URLs that allow you to play them sequentially without having to manually add them to the queue. This is crucial for any music player that offers the queuing feature, and helps you organize them music according to your rules, such as an album, an artist, etc.

Usually, the playlists come in the `.m3u` or the `.m3u8` formats, but there are other formats that define a playlist.

{% hint style="warning" %}
All M3U playlists that are going to be used in BassBoom have to specify all the files that are in the MPEG format. BassBoom doesn't currently support non-MP3 audio files, such as AAC.
{% endhint %}

***

## <mark style="color:$primary;">Usage</mark>

You can use the following functions to manage your playlists:

<details>

<summary>Functions for playlist parsing</summary>

BassBoom's Basolia offers you a way to parse your M3U playlists either as a file or as an M3U representation. You have two functions that do this:

<table><thead><tr><th width="200.333251953125">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>ParsePlaylist()</code></td><td>Parses a playlist file</td></tr><tr><td><code>ParsePlaylistFrom()</code></td><td>Parses a playlist representation</td></tr></tbody></table>

</details>

<details>

<summary>Playlist instance properties</summary>

You'll get a `Playlist` instance that specifies a list of tracks that define the order of which music plays first before the others. This list is an array of `TrackInfo` instances that allow you to get the following properties:

<table><thead><tr><th width="109.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Duration</code></td><td>Specifies how long in seconds does this track play. It can be -1 for infinite streams, such as radio stations or auditory livestreams.</td></tr><tr><td><code>Name</code></td><td>Specifies the name of the track as it appears in an M3U file. It'll be overridden by the music file's name tag property.</td></tr><tr><td><code>Path</code></td><td>Specifies the absolute path of the track local to your computer, or a full URL to a remote audio resource.</td></tr><tr><td><code>Type</code></td><td>Specifies one of the three track types, be it either a file, a radio station, or a normal URL that points to an audio resource.</td></tr></tbody></table>

</details>

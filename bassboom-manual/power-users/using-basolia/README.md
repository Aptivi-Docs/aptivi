---
description: How to use BassBoom.Basolia
icon: laptop
---

# Using Basolia

Usage of the Basolia library may not look easy at first, but they will look easy once you get used to it and its syntax.

This allows you to initialize the Basolia library either using your default executable directory or using your customized directory that contains the `runtimes` folder that contains the mpg123 libraries, such as in the case of Nitrocid.BassBoom addon.

This is an easy way to create a new instance of `BasoliaMedia`.

{% code title="Somewhere in your code" lineNumbers="true" %}
```csharp
basoliaMedia = new BasoliaMedia();
```
{% endcode %}

{% hint style="info" %}
In order to be able to use BassBoom Basolia functions, you need to make a new instance of the `BasoliaMedia` class.

You'll need to give an instance of `BasoliaMedia` to the Basolia functions that require it.
{% endhint %}

***

## <mark style="color:$primary;">Basolia Categories</mark>

The Basolia library is categorized to seven categories:

* [**Devices**](devices.md): Provides you functions that manipulate with the sound devices probed by the MPG123 library.
* [**File**](file.md): Provides you functions that allow you to open and close the music file.
* [**Format**](format.md): Provides you audio format tools, audio metadata tools, and audio decode tools.
* [**Lyrics**](lyrics.md): Provides you basic lyrics (.LRC) support.
* [**Playback**](playback.md): Provides you playback functions, such as playing, pausing, and stopping the music.
* [**Albums**](albums.md): Provides you functions that are able to help you more quickly prepare your studio album for your music collection.
* [**Radio**](radio.md): Provides you functions that let you play and query Internet radio stations.

Each category has its own page, so click on one of the pages in the left side pane.

***

## <mark style="color:$primary;">General Basolia tools</mark>

You can get the MPG123 version and the BassBoom Basolia's version using the following properties located in `InitBasolia`:

<table><thead><tr><th width="159.99993896484375">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>MpgLibVersion</code></td><td>Gives you the MPG123 version shipped with the <code>BassBoom.Native</code> NuGet package.</td></tr><tr><td><code>OutLibVersion</code></td><td>Gives you the OUT123 version shipped with the <code>BassBoom.Native</code> NuGet package.</td></tr><tr><td><code>SynLibVersion</code></td><td>Gives you the SYN123 version shipped with the <code>BassBoom.Native</code> NuGet package.</td></tr><tr><td><code>BasoliaVersion</code></td><td>Gives you the <code>BassBoom.Basolia</code> version.</td></tr></tbody></table>

{% hint style="info" %}
In case you need to manually initialize the Basolia library, you can use the `InitBasolia.Init()` function.
{% endhint %}

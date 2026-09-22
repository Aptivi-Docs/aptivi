---
description: What's being said in your song?
icon: microphone-stand
---

# Lyrics

BassBoom knows not only what music is playing, but also the words of the song by themselves. However, you'll need to provide a way for BassBoom to be able to synchronize the music with the lyrics, such as subtitling.

{% hint style="info" %}
BassBoom supports two types of `.lrc` or `.txt` lyrics:

* Standard: Time in lines
* Extended: Time in lines and words
{% endhint %}

***

## <mark style="color:$primary;">Usage</mark>

You can use the lyrics reader class to manage the lyrics and to make your app synchronize the lyrics with the music.

<details>

<summary>Usage of the <code>LyricReader</code> class</summary>

Just use the `LyricReader` class that contains:

<table><thead><tr><th width="189.3333740234375">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetLyrics(string)</code></td><td>Obtains a list of lyrics from a <code>.lrc</code> or <code>.txt</code> file</td></tr></tbody></table>

{% hint style="info" %}
The string in this function must be a complete path to your `.lrc` or `.txt` file containing lyric information about your music.
{% endhint %}

</details>

***

## <mark style="color:$primary;">Parsing of the lyrics</mark>

Basolia starts working on your provided lyric file by reading all the lines and verifies that all lines are valid lyric lines. Then, it processes the line according to the following:

<details>

<summary>Simple lyric line</summary>

In case the lyric line contains just the time span and the lyrics, Basolia parses it to a `TimeSpan` and takes the lyrics from the line. Below shows the clarification of this process:

```
[01:13.40]Don't believe me, just watch!
 ~~~~~~~~ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  |        |
  |        \- Lyric line
  \---------- Time of the lyric
```

</details>

<details>

<summary>Complex lyric line</summary>

In case the lyric line contains time spans of when the words are said, defined like below:

```
[02:55.75]<02:55.75> Uptown <02:56.75> funk <02:56.95> you <02:57.05> up!
 ~~~~~~~~ ~~~~~~~~~~ ~~~~~~
  |        |          |
  |        |          \- Word to be said
  |        \------------ Time of when the word is said
  \--------------------- Time of when the line is said
```

Basolia will attempt to split these words to their time spans, or `00:00` if these time spans can't be found in the line.

</details>

Once this is done, Basolia will install all the lyric lines (`LyricLine` class) to the list of lines in a new `Lyric` class instance, therefore returning it for usage in your applications.

***

## <mark style="color:$primary;">Structure of the lyrics</mark>

The structure of the lyrics, which the lyrics reader class uses, is defined by Basolia to simplify the process of processing the lyrics.

<details>

<summary>Lyric class properties</summary>

The function returns a `Lyric` that contains information about your lyric, including a list of lyric lines defined with the `LyricLine` class. It contains:

<table><thead><tr><th width="119.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Line</code></td><td>A lyric line</td></tr><tr><td><code>LineSpan</code></td><td>Time of when a lyric line gets played</td></tr><tr><td><code>LineWords</code></td><td>Group of words from the lyric line</td></tr></tbody></table>

`LyricLineWord` also contains these variables:

<table><thead><tr><th width="119.6666259765625">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Word</code></td><td>A lyric word</td></tr><tr><td><code>WordSpan</code></td><td>Time of when a word gets said</td></tr></tbody></table>

</details>

<details>

<summary>Lyric class functions</summary>

A `Lyric` instance contains several functions that allow you to get various lyric lines, such as getting them from the start to the current duration, and from current duration to the end. These functions allow you to perform these operations:

<table><thead><tr><th width="239.6666259765625">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetLinesCurrent()</code></td><td>Gets all the lines from the start to the current music duration</td></tr><tr><td><code>GetLinesUpcoming()</code></td><td>Gets all the lines from the current music duration to the end</td></tr><tr><td><code>GetLastLineCurrent()</code></td><td>Gets the last lyric line from the current music duration</td></tr><tr><td><code>GetLastLineWordsCurrent()</code></td><td>Gets the last lyric line words from the current music duration</td></tr><tr><td><code>GetLinesToSpan()</code></td><td>Gets all the lines from the start to the current span</td></tr><tr><td><code>GetLinesFromSpan()</code></td><td>Gets all the lines from the current span to the end</td></tr><tr><td><code>GetLastLineAtSpan()</code></td><td>Gets the last lyric line from the given time span</td></tr><tr><td><code>GetLastLineWordsAtSpan()</code></td><td>Gets the last lyric line words from the given time span</td></tr></tbody></table>

{% hint style="info" %}
While the first four functions require you to specify a working Basolia media instance to deal with the current duration, the last four functions don't require this instance, but require specifying a time span representing the target duration.
{% endhint %}

</details>

<details>

<summary>Example of lyrics processing</summary>

If you want a simple console app that lets you print the lyric lines as they play to simulate the lyric player feature usually found in your music player, the most minimal example of such an application is this:

```csharp
string path = "path/to/music.lrc";
var lyric = LyricReader.GetLyrics(path);
var lyricLines = lyric.Lines;
var shownLines = new List<LyricLine>();
var sw = new Stopwatch();
​
sw.Start();
foreach (var ts in lyricLines)
{
    while (sw.Elapsed < ts.LineSpan)
        Thread.Sleep(1);
​
    if (sw.Elapsed > ts.LineSpan)
    {
        Console.WriteLine(ts.Line);
        shownLines.Add(ts);
        if (shownLines.Count == lyricLines.Count)
            return;
    }
}
```

{% hint style="danger" %}
Radio stations and other non-seekable streams never support lyrics, since positioning requires the stream to be seekable.
{% endhint %}

</details>

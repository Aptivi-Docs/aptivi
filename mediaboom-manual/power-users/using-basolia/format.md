---
description: Formatting tools for your music files
icon: cassette-tape
---

# Format

Formatting tools for your music files in the Basolia library allow you to get information about your music file, such as getting a total duration, getting frame size and length, and getting ID3v2 metadata.

***

## <mark style="color:$primary;">Audio information tools</mark>

The formatting tools include the audio information tools, which allows you to get information about a music file that you've opened using the `OpenFile()` function.

<details>

<summary>Getting a duration</summary>

You can get a duration of the whole music file using either the samples count or the time span using one of the below functions:

```csharp
// Total samples count
public int GetDuration(bool scan) { }

// Time span
public TimeSpan GetDurationSpan(bool scan) { }
```

</details>

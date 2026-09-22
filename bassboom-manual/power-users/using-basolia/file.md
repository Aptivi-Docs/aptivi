---
description: File management for BassBoom
icon: file-audio
---

# File

The file tools shipped with the BassBoom.Basolia library allows you to open and close a music file so that you can play music and get its information, such as the ID3v2 metadata information.

***

## <mark style="color:$primary;">Usage</mark>

You can use the following functions to manage your sound devices:

<details>

<summary>Checking for open file or URL</summary>

If you want to check to see if there is a file being open in a `BasoliaMedia` instance, you can use the below function.

```csharp
public bool IsOpened() { }
```

</details>

<details>

<summary>Checking for radio station</summary>

If you want to check to see if an open file is a radio station, you can use this function, passing it your `BasoliaMedia` instance.

```csharp
public bool IsRadioStation() { }
```

</details>

<details>

<summary>Getting current file</summary>

If you want to get some information about a current file being played, you can use this function.

```csharp
public FileType? CurrentFile() { }
```

</details>

<details>

<summary>Opening a music file</summary>

To be able to get the most out of the Basolia library, like playing MP3 files, you should call the `OpenFile()` function, pointing it to a path to a music file.

```csharp
public void OpenFile(string path) { }
```

</details>

<details>

<summary>Opening a music stream</summary>

To play MPEG streams, excluding radio stations, you should call the `OpenFrom()` function, pointing it to an open stream.

```csharp
public void OpenFrom(Stream? audioStream) { }
public async Task OpenFromAsync(Stream? audioStream) { }
```

{% hint style="info" %}
To open radio stations, open a URL file as this function doesn't parse radio metadata.
{% endhint %}

</details>

<details>

<summary>Opening a URL file</summary>

To play remote files, such as radio stations, you should call the `OpenUrl()` function, pointing it to a URL that provides an MPEG stream.

```csharp
public void OpenUrl(string path) { }
public async Task OpenUrlAsync(string path) { }
```

</details>

<details>

<summary>Closing a music file</summary>

If you're done playing a music file or performing a specific operation on it, you can call the `CloseFile()` function to close the file.

```csharp
public void CloseFile() { }
```

</details>

---
description: >-
  Follow the compatibility notes when upgrading BassBoom.Basolia to API v1.1
  series
icon: up
---

# Upgrading to API v1.1 series

If you are an app developer, and you plan to upgrade BassBoom.Basolia to API v1.1 version series, you'll need to consider the following breaking changes:

***

## <mark style="color:$primary;">From 0.1.4.x to 0.2.0.x</mark>

When upgrading BassBoom from 0.1.4.x to 0.2.0.x, you need to consider the following changes:

<details>

<summary><code>BasoliaMedia</code> introduced</summary>

{% code title="PlaybackTools.cs" lineNumbers="true" %}
```csharp
public static void Play() { }
public static void Pause() { }
public static void Stop() { }
```
{% endcode %}

We've introduced a brand new class, `BasoliaMedia`, that stores the states and the appropriate native library handles to ensure simultaneous operation. As a result, we had to edit all the Basolia functions so that you'd need to provide an instance of `BasoliaMedia` that you'd want to perform an action on.

We also had to edit the following properties:

* `Playing` -> `IsPlaying()`
* `State` -> `GetState()`
* `RadioIcy` -> `GetRadioIcy()`
* `RadioNowPlaying` -> `GetRadioNowPlaying()`
* `Decoder` -> `GetCurrentDecoder()` and `SetCurrentDecoder()`

{% hint style="info" %}
You'll need to create a new instance of `BasoliaMedia` before being able to use this library to its fullest extent.
{% endhint %}

</details>

***

## <mark style="color:$primary;">From 0.2.0.x to 0.2.1.x</mark>

When upgrading BassBoom from 0.2.0.x to 0.2.1.x, you need to consider the following changes:

<details>

<summary><code>BasoliaMedia</code> expanded</summary>

{% code title="DeviceTools.cs" lineNumbers="true" %}
```csharp
public static (string? driver, string? device) GetCurrentCached() { }
public static void Reset() { }
```
{% endcode %}

We've expanded the `BasoliaMedia` class that stores the states and the appropriate native library handles to ensure simultaneous operation. We had to edit some more Basolia functions so that you'd need to provide an instance of `BasoliaMedia` that you'd want to perform an action on.

We also had to edit the following properties:

* `IsOpened` -> `IsOpened()`
* `IsRadioStation` -> `IsRadioStation()`
* `CurrentFile` -> `CurrentFile()`

{% hint style="info" %}
You'll need to create a new instance of `BasoliaMedia` before being able to use this library to its fullest extent.
{% endhint %}

</details>

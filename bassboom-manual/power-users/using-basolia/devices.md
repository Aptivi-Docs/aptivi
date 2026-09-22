---
description: Sound device management in your hands!
icon: speaker
---

# Devices

The device tools shipped with the Basolia library allow you to manage your sound devices and your available sound drivers for MPG123.

***

## <mark style="color:$primary;">Usage</mark>

You can use the following functions to manage your sound devices:

<details>

<summary>Getting drivers</summary>

To get a list of drivers with their descriptions, you can call the `GetDrivers()` function to get a read-only dictionary with driver names as the key and their descriptions as their values.

```csharp
public ReadOnlyDictionary<string, string> GetDrivers() { }
```

</details>

<details>

<summary>Getting devices</summary>

To get a list of available sound devices from a sound driver, you can use the `GetDevices()` function to get all the available sound devices that the specified sound driver detected. The second argument is a string output variable that describes the active device.

```csharp
public ReadOnlyDictionary<string, string> GetDevices(string driver, ref string activeDevice) { }
```

</details>

<details>

<summary>Setting active driver</summary>

To set the active driver for the application's lifetime, you can use the `SetActiveDriver()` function.

```csharp
public void SetActiveDriver(string driver) { }
```

</details>

<details>

<summary>Setting active device</summary>

To set the active device for a specified driver, you can use the `SetActiveDevice()` function.

```csharp
public void SetActiveDevice(string driver, string device) { }
```

</details>

<details>

<summary>Getting current driver and device</summary>

```csharp
// Non-cached
public (string driver, string device) GetCurrent() { }

// Cached
public (string driver, string device) GetCurrentCached() { }
```

If you want to know your current device and driver that are being used by MPG123 to play music from, you'll need to use one of the following functions:

* `GetCurrent()`: Gets the current driver and device that MPG123 reports
* `GetCurrentCached()`: Gets the cached current driver and device that Basolia reports

</details>

<details>

<summary>Resetting current driver and device</summary>

```csharp
public void Reset() { }
```

If you want to reset the current driver and device to their default values, you can use this function. This resets to your primary output device determined by your operating system.

</details>

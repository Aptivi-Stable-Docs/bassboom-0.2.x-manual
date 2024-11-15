---
description: Sound device management in your hands!
icon: speakers
---

# Devices

The device tools shipped with the Basolia library allow you to manage your sound devices and your available sound drivers for MPG123.

### Getting drivers

To get a list of drivers with their descriptions, you can call the `GetDrivers()` function to get a read-only dictionary with driver names as the key and their descriptions as their values.

```csharp
public static ReadOnlyDictionary<string, string> GetDrivers(BasoliaMedia? basolia)
```

### Getting devices

To get a list of available sound devices from a sound driver, you can use the `GetDevices()` function to get all the available sound devices that the specified sound driver detected. The second argument is a string output variable that describes the active device.

```csharp
public static ReadOnlyDictionary<string, string> GetDevices(BasoliaMedia? basolia, string driver, ref string activeDevice)
```

### Setting active driver

To set the active driver for the application's lifetime, you can use the `SetActiveDriver()` function.

```csharp
public static void SetActiveDriver(BasoliaMedia? basolia, string driver)
```

### Setting active device

To set the active device for a specified driver, you can use the `SetActiveDevice()` function.

```csharp
public static void SetActiveDevice(BasoliaMedia? basolia, string driver, string device)
```

### Getting current driver and device

```csharp
// Non-cached
public static (string driver, string device) GetCurrent(BasoliaMedia? basolia)

// Cached
public static (string driver, string device) GetCurrentCached(BasoliaMedia? basolia)
```

If you want to know your current device and driver that are being used by MPG123 to play music from, you'll need to use one of the following functions:

* `GetCurrent()`: Gets the current driver and device that MPG123 reports
* `GetCurrentCached()`: Gets the cached current driver and device that Basolia reports

### Resetting current driver and device

```csharp
public static void Reset(BasoliaMedia? basolia)
```

If you want to reset the current driver and device to their default values, you can use this function. This resets to your primary output device determined by your operating system.

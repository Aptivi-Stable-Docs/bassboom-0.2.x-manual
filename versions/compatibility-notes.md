---
description: If you want to upgrade, here's your guide to update your apps.
icon: notebook
---

# Compatibility Notes

When you upgrade BassBoom to a version that contains a higher API version that you have, you'll need to follow the compatibility notes.

## From 0.0.2.x to 0.0.3.x

When upgrading BassBoom from 0.0.2.x to 0.0.3.x, you need to consider the following changes:

### Removed fugitive mode

{% code title="InitBasolia.cs" lineNumbers="true" %}
```csharp
public static void Init(string root = "", bool Fugitive = false)
```
{% endcode %}

The Fugitive mode was implemented to enable dangerous operations, such as an ability to get music info while the music is playing. However, these operations cause MPG123 to error out with random errors, causing playback to be distorted.

As a result, we've removed fugitive mode.

{% hint style="danger" %}
We advise you to stop using this mode.
{% endhint %}

## From 0.0.3.x to 0.1.0.x

When upgrading BassBoom from 0.0.3.x to 0.1.0.x, you need to consider the following changes:

### Removed CachedSongInfo

{% code title="CachedSongInfo.cs" lineNumbers="true" %}
```csharp
public class CachedSongInfo
```
{% endcode %}

This class wasn't meant to be in the Basolia library, but it was put there as a temporary placeholder for the playlist system, which was going to be introduced to the Basolia library. However, Basolia didn't get this system, so we had to remove this while thinking of better ways to implement this class.

{% hint style="info" %}
For now, you can host your own `CachedSongInfo` class while we come up with better ways to implement the caching system.
{% endhint %}

### Internalized the native part of the library

For security reasons, we've made [this commit](https://github.com/Aptivi/BassBoom/commit/a9286743928217d0f03955f4476b34bc5827e0af#diff-20357a26bcea3043b9175a19fc3be3f849b3d4011cec3633e63ff71495d5f0d6) that internalizes the sensitive parts of the library (the ones with the P/Invoke signatures). This is so that Basolia stays the best way to use the whole BassBoom library and the program.

{% hint style="danger" %}
It's advisable that you stop making direct calls to the MPG123 library functions and start using the Basolia library. If you still want a feature that Basolia doesn't provide, head to the [Issues](https://github.com/Aptivi/BassBoom/issues) tab.

This commit serves as a stepping stone to the full extensibility and flexibility to the library.
{% endhint %}

### SHOUTcast exceptions cleanup

{% code title="Affected classes" lineNumbers="true" %}
```csharp
public class ShoutcastStreamParseException : Exception
public class ShoutcastServerException : Exception
```
{% endcode %}

`ShoutcastServerException` has been renamed to `BasoliaMiscException` to cover all the possible exceptions that don't require or provide the MPG123 error code that is provided by the native part of the library.

Likewise, `ShoutcastStreamParseException` has been removed for the introduction of the IceCast radio querying feature.

{% hint style="info" %}
If you want to continue handling these exceptions, you must update your handler to catch the `BasoliaMiscException` instances, though it might also catch all the unrelated instances of the same exception.
{% endhint %}

### Removed extra Basolia initialization checking function

{% code title="InitBasolia.cs" lineNumbers="true" %}
```csharp
public static bool IsInited()
```
{% endcode %}

This function was accidentally implemented during the alpha stages of Basolia, which led to the implementation of the `BasoliaInitialized` property to make users aware that properties to query the status of the library's initialization state are better than single-line functions in terms of semantics.

As a result, the above function was removed to reduce confusion.

{% hint style="info" %}
You need to replace calls to this function with the `BasoliaInitialized` property as both of them exhibit the same behavior.
{% endhint %}

## From 0.1.0.x to 0.1.4.x

When upgrading BassBoom from 0.1.0.x to 0.1.4.x, you need to consider the following changes:

### Exception classes have been rearranged

{% code title="Basolia*Exception.cs" lineNumbers="true" %}
```csharp
namespace BassBoom.Basolia
```
{% endcode %}

The Basolia exceptions have been moved to `BassBoom.Basolia.Exceptions` to better arrange the exception classes.

{% hint style="info" %}
You need to change the imports clause to `BassBoom.Basolia.Exceptions`. If you're still using functions found in the `BassBoom.Basolia` namespace, you need to add an extra imports clause pointing to the `Exceptions` namespace.
{% endhint %}

## From 0.1.4.x to 0.2.0.x

When upgrading BassBoom from 0.1.4.x to 0.2.0.x, you need to consider the following changes:

### `BasoliaMedia` introduced

{% code title="PlaybackTools.cs" lineNumbers="true" %}
```csharp
public static void Play()
public static void Pause()
public static void Stop()
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

## From 0.1.4.x to 0.2.1.x

When upgrading BassBoom from 0.1.4.x to 0.2.1.x, you need to consider the following changes:

### `BasoliaMedia` expanded

{% code title="DeviceTools.cs" lineNumbers="true" %}
```csharp
public static (string? driver, string? device) GetCurrentCached()
public static void Reset()
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

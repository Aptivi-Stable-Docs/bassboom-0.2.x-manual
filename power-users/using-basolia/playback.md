---
description: Play your music!
icon: play
---

# Playback

The playback tools in the Basolia library contains two separate sections: the actual playback tools and the playback positioning tools.

## Playback tools

The playback tools shipped with the Basolia library is a key feature for every single music player.

### Playing music

There are two ways to play the music: synchronously and asynchronously. For normal console applications, you'd typically use `Play()` for a single audio player, or this function in a thread for a music player, such as BassBoom.Cli.

```csharp
public static void Play(BasoliaMedia? basolia)
```

However, for GUI application, it's best to use the asynchronous version whenever possible, `PlayAsync()`, to avoid blocking the main thread.

```csharp
public static async Task PlayAsync(BasoliaMedia? basolia)
```

### Pausing and stopping music

If you want to pause the music, you can use the `Pause()` function. It'll stop the music, but stays at the current position. If you want to start over, you can use the `Stop()` function.

```csharp
public static void Pause(BasoliaMedia? basolia)
public static void Stop(BasoliaMedia? basolia)
```

### Volume Controls

For controlling the volume that the Basolia library controls, you can use both the `SetVolume()` and the `GetVolume()` functions. `SetVolume()` allows you to set the current volume to the new volume from 0.0 (0%) to 1.0 (100%). Additionally, if you've enabled the volume boost option, you can set the volume up to 3.0 (300%), though this may cause audio artifacts in some cases where parts of an audio file is loud.

```csharp
public static void SetVolume(BasoliaMedia? basolia, double volume, bool volBoost = false)
```

Getting the current volume using the `GetVolume()` function returns three variables that describe the following:

* `baseLinear`: The base linear volume from 0.0 to 1.0
* `actualLinear`: The actual linear volume from 0.0 to 1.0
* `decibelsRva`: The RVA value in decibels (dB)

```csharp
public static (double baseLinear, double actualLinear, double decibelsRva) GetVolume(BasoliaMedia? basolia)
```

### Playback states

When either `Play()`, `Pause()`, or `Stop()` functions are called, the playback state changes, depending on the action. You can get the current playback state by using the `GetState` function.

```csharp
public static PlaybackState GetState(BasoliaMedia? basolia)
```

You can also quickly determine whether Basolia is busy playing a song using the `IsPlaying` function:

```csharp
public static bool IsPlaying(BasoliaMedia? basolia)
```

The playback states are the following:

* `Stopped`: Music has either stopped or not played yet
* `Playing`: Music is playing
* `Paused`: Music has been paused by the user or by the call to the `Pause()` function

### Opening the output

If you want to open the output to your selected device and driver or to a pre-determined device and driver as selected by your OS, you can use the below function:

```csharp
public static void OpenOutput(BasoliaMedia? basolia)
```

{% hint style="info" %}
You don't usually need to call this function, unless you have a reason to. Playback tools already use this function internally.
{% endhint %}

### Starting the output

If you want to start the output at a selected rate, channel count, and encoding, you can use the below function:

```csharp
public static void StartOutput(BasoliaMedia? basolia, long rate, ChannelCount channels, int encoding)
```

{% hint style="info" %}
You don't usually need to call this function, unless you have a reason to. Playback tools already use this function internally.
{% endhint %}

### Closing the output

If you no longer want to output anything, you can use this function:

```csharp
public static void CloseOutput(BasoliaMedia? basolia)
```

{% hint style="danger" %}
Use this function carefully, as reckless usage could cause the underlying application to crash with an access violation error.
{% endhint %}

### Play'n'Forget

If you don't want to set up a persistent `BasoliaMedia` instance for every operation, you can use this technique to implement Play'n'Forget in your applications so that you can play either a file or a stream without any difficulty. The below functions can be found in the `Independent` namespace.

{% hint style="info" %}
If you want to change a specific setting, you should create a class instance of `PlayForgetSettings` that consists of:

* `Volume` (settable and constructible)
* `VolumeBoost` (settable and constructible)
* `RootLibPath` (constructible, but not modifiable)

Be careful about the `RootLibPath` settings entry, as it gets ignored right after Basolia verifies that the library is loaded for the first time.
{% endhint %}

#### Playing a file

There are two ways to play a file: synchronously and asynchronously.

```csharp
public static void PlayFile(string path, PlayForgetSettings? settings = null)
public static async Task PlayFileAsync(string path, PlayForgetSettings? settings = null)
```

Just call one of these functions, passing it either an absolute path or a relative path to your music file, optionally passing it the Play'n'Forget settings instance.

#### Playing a stream

There are two ways to play a stream: synchronously and asynchronously.

```csharp
public static void PlayStream(Stream stream, PlayForgetSettings? settings = null)
public static async Task PlayStreamAsync(Stream stream, PlayForgetSettings? settings = null)
```

Just call one of these functions, passing it a **seekable** stream containing MP3 data of your song file, optionally passing it the Play'n'Forget settings instance.

{% hint style="danger" %}
Radio stations and other non-seekable streams are not supported as Basolia requires a stream to be seekable for non-radio-station streams. In addition to that, radio stations can't be "forgotten" as it's an infinite stream.
{% endhint %}

## Positioning tools

In addition to the playback tools, you can also get access to the positioning tools to perform seek operations to jump to a specific section of a song, regardless of whether the song is playing or not.

### Current duration

You can get the current duration in two units: Samples and time span. If you want to get the current duration using the samples, you can use the `GetCurrentDuration()` function:

```csharp
public static int GetCurrentDuration(BasoliaMedia? basolia)
```

Similarly, you can also get the current duration in the timespan for easier representation by using the `GetCurrentDurationSpan()` function:

```csharp
public static TimeSpan GetCurrentDurationSpan(BasoliaMedia? basolia)
```

### Seeking controls

If you want to seek the music file either to a selected position using a frame number or to the beginning of the song (frame 0), you can simply use one of the two functions:

```csharp
// For seeking to the beginning
public static void SeekToTheBeginning(BasoliaMedia? basolia)

// For seeking to a specific MPEG frame
public static void SeekToFrame(BasoliaMedia? basolia, int frame)

// For seeking to a specific lyric line
public static void SeekLyric(BasoliaMedia? basolia, LyricLine lyricLine)
```

### Dropping MPEG frames

If you want to flush all MPEG frames to the device for any reason, you can use this function:

```csharp
public static void Drop(BasoliaMedia? basolia)
```

## Equalizer tools

BassBoom's Basolia library also allows you to modify the equalizer settings during playback so that you can listen to enhanced music. It currently supports 32 bands as MPG123 supports.

{% hint style="info" %}
You can run this tool on either left, right, or both speakers.
{% endhint %}

### Getting current equalizer values

If you want to get the current equalizer values, you can use the below function:

```csharp
public static double GetEqualizer(BasoliaMedia? basolia, mpg123_channels channels, int bandIdx)
```

### Setting equalizer values

If you want to set the equalizer values for one or more bands to make your music sound better, you can use the below function:

```csharp
// For one band
public static void SetEqualizer(BasoliaMedia? basolia, mpg123_channels channels, int bandIdx, double value)

// For more than one bands
public static void SetEqualizerRange(BasoliaMedia? basolia, mpg123_channels channels, int bandIdxStart, int bandIdxEnd, double value)
```

### Resetting equalizer values

If you want to reset the equalizer values to their natural states (`1.00`), you can use the below function:

```csharp
public static void ResetEqualizer(BasoliaMedia? basolia)
```

### Getting native state

If you want to get the native state of the output stream that represents the currently playing music, you can use this function:

```csharp
public static (long, double) GetNativeState(BasoliaMedia? basolia, mpg123_state state)
```

The `mpg123_state` enumeration has the following states for you to get:

* `MPG123_ACCURATE`: Accurate rendering
* `MPG123_BUFFERFILL`: Buffer fill
* `MPG123_DEC_DELAY`: Decode delay in milliseconds
* `MPG123_ENC_DELAY`: Encode delay in milliseconds
* `MPG123_ENC_PADDING`: Encoding padding
* `MPG123_FRANKENSTEIN`: Frankenstein stream?
* `MPG123_FRESH_DECODER`: Fresh decoder

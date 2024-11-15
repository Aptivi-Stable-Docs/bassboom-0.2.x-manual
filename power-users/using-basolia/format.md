---
description: Formatting tools for your music files
icon: cassette-tape
---

# Format

Formatting tools for your music files in the Basolia library allow you to get information about your music file, such as getting a total duration, getting frame size and length, and getting ID3v2 metadata.

## Audio information tools

The formatting tools include the audio information tools, which allows you to get information about a music file that you've opened using the `OpenFile()` function.

### Getting a duration

You can get a duration of the whole music file using either the samples count or the time span using one of the below functions:

```csharp
// Total samples count
public static int GetDuration(BasoliaMedia? basolia, bool scan)

// Time span
public static TimeSpan GetDurationSpan(BasoliaMedia? basolia, bool scan)
```

Additionally, if you have a number of samples, such as what `GetDuration()` returned, you can use one of the following functions:

```csharp
// Format info is not known
public static TimeSpan GetDurationSpanFromSamples(BasoliaMedia? basolia, int samples)

// Format info is known
public static TimeSpan GetDurationSpanFromSamples(int samples, long rate)
```

### Frame size and length

If you want to know the frame size of your music file and its length, you can use the two functions below:

```csharp
// Frame size
public static int GetFrameSize(BasoliaMedia? basolia)

// Frame length
public static int GetFrameLength(BasoliaMedia? basolia)
```

### Samples per frame

If you want to know the number of MPEG samples per single frame, you can use the below function:

```csharp
public static int GetSamplesPerFrame(BasoliaMedia? basolia)
```

### Getting buffer size

To get the buffer size for your music file, you'll have to call the `GetBufferSize()` function.

```csharp
public static int GetBufferSize(BasoliaMedia? basolia)
```

### ID3v2, ID3v1, and ICY metadata

To gather the ID3v2, ID3v1, and ICY metadata, the two functions provide you information about the music file:

```csharp
public static void GetId3Metadata(BasoliaMedia? basolia, out Id3V1Metadata managedV1, out Id3V2Metadata managedV2)
public static string GetIcyMetadata(BasoliaMedia? basolia)
```

The ID3v2 metadata contains the following information:

* `Title`: Song title
* `Artist`: Song artist
* `Album`: Song album
* `Year`: Song year
* `Comment`: Song comment
* `Genre`: Song genre
* `Comments`: A list of comments
* `Texts`: A list of extra text
* `Extras`: A list of extras
* `Pictures`: A list of pictures

The ID3v1 metadata contains the following information:

* `Tag`: Song tag
* `Title`: Song title
* `Artist`: Song artist
* `Album`: Song album
* `Year`: Song year
* `Comment`: Song comment
* `Genre`: Song genre. You can get its index using the `GenreIndex` property.

### Frame information

To get the complete frame information about your music file, you need to call the `GetFrameInfo()` function:

```csharp
public static FrameInfo GetFrameInfo(BasoliaMedia? basolia)
```

A single `FrameInfo` instance returned by the above function contains the following information:

* `Version`: MPEG version
* `Layer`: Layer 1, 2, or 3
* `Rate`: Bitrate
* `Mode`: MPEG mode. You can get extended info using the ModeExt property.
* `FrameSize`: MPEG frame size
* `Flags`: Flags to indicate the originality of the song
* `Emphasis`: The song emphasis
* `BitRate`: Actual bitrate
* `AbrRate`: Average bitrate
* `Vbr`: Variable bitrate mode

### Safe buffer size

If you want to know the size of a generic buffer, you can use this function.

```csharp
public static int GetGenericBufferSize()
```

### Getting seconds per frame

If you want to get an MPEG frame length in seconds, which can be a fraction of a second, you can make use of this function:

```csharp
public static double GetSecondsPerFrame(BasoliaMedia? basolia)
```

## Format tools

In addition to the audio information tools, this library also ships the formatting tools that allow you to get format info for a song.

### Getting format info

To get format information for a song, you can use the GetFormatInfo() function that allows you to get a bit rate, number of channels, and the encoding used in a song:

```csharp
public static (long rate, int channels, int encoding) GetFormatInfo(BasoliaMedia? basolia)
```

### Getting list of supported formats

In addition to getting a single format information, you can also get a list of supported formats that are supported by the sound device. This can be achieved by calling the `GetFormats()` function:

```csharp
public static FormatInfo[] GetFormats(BasoliaMedia? basolia)
```

A single `FormatInfo` instance contains three properties:

* `Rate`: A bit rate
* `Channels`: Number of channels in a song file
* `Encoding`: Song encoding

### Getting list of supported rates

This function that is defined below allows you to get a list of all the supported rates that your device and your driver can play.

```csharp
public static int[] GetRates()
```

{% hint style="warning" %}
You'll need to cast a value from this array to `long` before being able to use it in Basolia functions that require this value.
{% endhint %}

### Getting list of supported encodings

This function that is defined below allows you to get a list of all the supported encodings that your device and your driver can play.

```csharp
public static int[] GetEncodings()
```

### Getting encoder name and description

If you want to be more elaborate by describing an encoder from an encoder ID for clarity, you can use the two functions that both help you get the name and the description, respectively:

```csharp
public static string GetEncodingName(int encoding)
public static string GetEncodingDescription(int encoding)
```

### Format support check

If you want to check to see if a particular rate and encoding is supported, you can use this function's return value to determine support, along with an out parameter that tells you if it's supported in mono, stereo, or both.

```csharp
public static bool IsFormatSupported(BasoliaMedia? basolia, long rate, int encoding, out ChannelCount channelCount)
```

### Encoding size

If you want to get the encoding size in bytes, you can use this function:

```csharp
public static int GetEncodingSize(int encoding)
```

### Format usage

There are three modes into which the Basolia media instance accepts formats:

* No format: This means that no format will be accepted, and any operation that requires format to be set up, such as playback, will error out.
* All formats: This means that all formats will be accepted, as long as they're one of the supported formats.
* Specific format: This means that only this specific format that you've specified in your code will be accepted.

```csharp
// No format
public static void NoFormat(BasoliaMedia? basolia)

// All formats
public static void AllFormats(BasoliaMedia? basolia)

// Specific format
public static void UseFormat(BasoliaMedia? basolia, long rate, ChannelCount channels, int encoding)
```

### PCM samples

If you want to get generic information about the PCM samples, such as getting a PCM sample size in bytes or a zero sample size, you can use the following two functions:

```csharp
public static int GetSampleSize(int encoding)
public static int GetZeroSample(int encoding, int sampleSize, int lsbOffset)
```

## Decode tools

In order for BassBoom to play songs, they must be decoded before the resulting audio data can be sent to the target device. BassBoom's Basolia offers decoding tools.

### Manually decoding a frame

To manually decode a frame, you must use the `DecodeFrame()` function. Most of the time, you don't need to call it; BassBoom's Basolia will automatically call it for you when playback is commenced.

```csharp
public static int DecodeFrame(BasoliaMedia? basolia, ref int num, ref byte[] audio, ref int bytes)
```

### Get/Set current decoder

If you want to get the current decoder or if you want to set the current decoder to something else, you need to use the `Decoder` property.

```csharp
public static string GetCurrentDecoder(BasoliaMedia? basolia)
public static void SetCurrentDecoder(BasoliaMedia? basolia, string decoderName)
```

{% hint style="info" %}
Make sure that you're using a decoder that's supported for your device. Otherwise, you'll get an error saying that the required decoder is not supported.
{% endhint %}

### Get all decoders

If you want to either get all the decoders that are implemented in the distributed version of MPG123 library, or if you want to get all the decoders that your system can use, you'll need to use the `GetDecoders` function.

```csharp
public static string[] GetDecoders(bool onlySupported)
```

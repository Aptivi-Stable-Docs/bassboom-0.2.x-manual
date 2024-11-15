---
description: File management for BassBoom
icon: file-audio
---

# File

The file tools shipped with the BassBoom.Basolia library allows you to open and close a music file so that you can play music and get its information, such as the ID3v2 metadata information.

### Checking for open file or URL

If you want to check to see if there is a file being open in a `BasoliaMedia` instance, you can use the below function.

```csharp
public static bool IsOpened(BasoliaMedia? basolia)
```

### Checking for radio station

If you want to check to see if an open file is a radio station, you can use this function, passing it your `BasoliaMedia` instance.

```csharp
public static bool IsRadioStation(BasoliaMedia? basolia)
```

### Getting current file

If you want to get some information about a current file being played, you can use this function.

```csharp
public static FileType? CurrentFile(BasoliaMedia? basolia)
```

### Opening a music file

To be able to get the most out of the Basolia library, like playing MP3 files, you should call the `OpenFile()` function, pointing it to a path to a music file.

```csharp
public static void OpenFile(BasoliaMedia? basolia, string path)
```

### Opening a music stream

To play MPEG streams, excluding radio stations, you should call the `OpenFrom()` function, pointing it to an open stream.

```csharp
public static void OpenFrom(BasoliaMedia? basolia, Stream? audioStream)
public static async Task OpenFromAsync(BasoliaMedia? basolia, Stream? audioStream)
```

{% hint style="info" %}
To open radio stations, consult the below function as this function doesn't parse radio metadata.
{% endhint %}

### Opening a URL file

To play remote files, such as radio stations, you should call the `OpenUrl()` function, pointing it to a URL that provides an MPEG stream.

```csharp
public static void OpenUrl(BasoliaMedia? basolia, string path)
public static async Task OpenUrlAsync(BasoliaMedia? basolia, string path)
```

### Closing a music file

If you're done playing a music file or performing a specific operation on it, you can call the `CloseFile()` function to close the file.

```csharp
public static void CloseFile(BasoliaMedia? basolia)
```

---
description: You're now listening to an FM radio station!
icon: radio
---

# Radio

BassBoom provides you with the Internet radio features, such as playing them and getting information about your favorite radio station. You can use the `FileTools.OpenUrl()` function to open the MPG123 handle to the radio station URL, assuming that said station uses MPEG and not AAC or other formats. Use the `PlaybackTools.Play()`, as usual, to play the radio station.

If you want to get your favorite internet radio station's information, you can use the `GetRadioInfo` function from the `RadioTools` class in the `BassBoom.Basolia.Radio` namespace.

Afterwards, you can call either `Refresh()` or `RefreshAsync()` to fetch the following info from the server:

* `ServerHost`
  * Server IP address
* `ServerPort`
  * Server port used by Shoutcast
* `ServerHostFull`
  * Server IP address with port
* `ServerHttps`
  * Whether the Shoutcast server is using HTTPS or not
* `ServerType`
  * Radio server type
* `ServerVersion`
  * \[SHOUTcast] Server version (1.x, 2.x)
* `TotalStreams`
  * Total number of streams in the server
* `ActiveStreams`
  * Active streams in the server
* `CurrentListeners`
  * How many people are listening to the server at this time?
* `PeakListeners`
  * How many listeners did the server ever get at peak times?
* `MaxListeners`
  * \[SHOUTcast] How many people can listen to the server?
* `UniqueListeners`
  * \[SHOUTcast] How many unique listeners are there?
* `AverageTime`
  * \[SHOUTcast] Average time on any active listener connections in seconds
* `AverageTimeSpan`
  * \[SHOUTcast] Average time on any active listener connections in the time span
* `Streams`
  * Available streams and their statistics

Stream information class, `StreamInfo`, contains the following variables:

* `StreamId`
  * Stream ID starting from number one (1)
* `CurrentListeners`
  * How many people are listening to the stream at this time?
* `PeakListeners`
  * How many listeners did the stream ever get at peak times?
* `MaxListeners`
  * \[SHOUTcast] How many people can listen to the stream?
* `UniqueListeners`
  * \[SHOUTcast] How many unique listeners are there?
* `AverageTime`
  * \[SHOUTcast] Average time on any active listener connections in seconds
* `AverageTimeSpan`
  * \[SHOUTcast] Average time on any active listener connections in the time span
* `StreamGenre` -> `StreamGenre5`
  * The stream genre
* `StreamHomepage`
  * Link to the stream homepage
* `StreamTitle`
  * Stream title
* `SongTitle`
  * Song title
* `StreamHits`
  * \[SHOUTcast] Stream hits
* `StreamStatus`
  * \[SHOUTcast] Stream status
* `BackupStatus`
  * \[SHOUTcast] Backup stream status
* `StreamListed`
  * Is the stream listed?
* `StreamPath`
  * Path to stream
* `StreamUptime`
  * \[SHOUTcast] Stream uptime in seconds
* `StreamUptimeSpan`
  * \[SHOUTcast] Stream uptime in the time span
* `BitRate`
  * Stream bitrate in kbps
* `SampleRate`
  * \[SHOUTcast] Sampling rate in Hz
* `MimeInfo`
  * MIME info for stream, usually audio/mpeg.

You can use this library to make an application that fetches info from your Shoutcast server for analytical purposes.

{% hint style="info" %}
For web development and other cases where asynchronous code is acceptable, use the `Async` version of the functions as outlined in the beginning of this page to avoid blocking the main thread.
{% endhint %}

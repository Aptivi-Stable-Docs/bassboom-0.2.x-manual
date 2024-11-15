---
description: Play this before this...
icon: piano-keyboard
---

# Playlists

Playlists are a group of music files or URLs that allow you to play them sequentially without having to manually add them to the queue. This is crucial for any music player that offers the queuing feature, and helps you organize them music according to your rules, such as an album, an artist, etc. Usually, the playlists come in the `.m3u` or the `.m3u8` formats, but there are other formats that define a playlist.

{% hint style="warning" %}
All M3U playlists that are going to be used in BassBoom have to specify all the files that are in the MPEG format. BassBoom doesn't currently support non-MP3 audio files, such as AAC.
{% endhint %}

BassBoom's Basolia offers you a way to parse your M3U playlists either as a file or as an M3U representation. You have two functions that do this:

* `ParsePlaylist()`: Parses a playlist file
* `ParsePlaylistFrom()`: Parses a playlist representation

Both return a `Playlist` instance that specifies a list of tracks that define the order of which music plays first before the others. This list is an array of `TrackInfo` instances that allow you to get the following properties:

* `Duration`: Specifies how long in seconds does this track play. It can be -1 for infinite streams, such as radio stations or auditory livestreams.
* `Name`: Specifies the name of the track as it appears in an M3U file. It'll be overridden by the music file's name tag property.
* `Path`: Specifies the absolute path of the track local to your computer, or a full URL to a remote audio resource.
* `Type`: Specifies one of the three track types, be it either a file, a radio station, or a normal URL that points to an audio resource.

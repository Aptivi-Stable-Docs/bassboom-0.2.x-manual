---
description: Album management in your own hands
icon: disc-drive
---

# Albums

In addition to all of the BassBoom's Basolia features that we've explained in the entire documentation, this library also provides you with the tools necessary to manage your albums.

## Preparing your album

In order to prepare your album with this library, you can perform the below operations to create a successful album CD/DVD in no time.

### Labeling your music files

You can label your music files to sort all your music albums by track numbers. This operation renames all your music files to match the one that such albums come with, such as `01. <Artist> - <Title>`. This tool can be found in the `MusicFileLabeler` class.

```csharp
public static void LabelFiles(string libraryPath)
```

It renames your files to append the track number to their prefixes in their names to make it look like your music album's naming scheme. It's useful for quickly making your music albums.

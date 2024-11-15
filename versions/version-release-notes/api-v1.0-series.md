---
description: This is just the beginning!
icon: gem
---

# API v1.0 series

This series is the first version series that actually defines the multiplatform music player to the .NET environment. The first version of BassBoom, 0.0.1, was out on October 1st, 2023.

## Version 0.0.2

This version was released on November 14th, 2023, as a celebration of the .NET 8.0 release! This version serves as an enhancement release over the previous version.

### Improvements (Basolia)

* Updated MPG123 to 1.32.3
* Updated targeting to .NET 8.0
* Added support for macOS 64-bit (ARM64 support not done yet)
* Added getting frame length and samples per frame
* Added synthesis to Native (currently unused)

### Improvements (CLI music player)

* Updated Terminaux
* Show song name and duration in the music list
* Don't show genre in the titles
* Use music file name instead of "unknown song"
* Only populate music info if necessary
* You can remove songs from the playlist

### Improvements (GUI music player)

* Updated Avalonia
* Show song name and duration in the music list

## Version 0.0.2.1

This version was released on November 15th, 2023 to fix an issue regarding loading the library modules.

### Improvements (Basolia)

* Fixed loading modules

## Version 0.0.3

This version was released on December 14th, 2023 to bring with you improvements.

### Improvements (Basolia)

* Added the music file labeler
* Removed fugitive mode for your sanity
* Hardened `AudioInfoTools` on playback

### Improvements (CLI music player)

* Updated Terminaux
* Made the CLI resizable

## Version 0.0.3.1

This version was released on December 21th, 2023 to facilitate debugging the Basolia library.

### Improvements (Basolia)

* Added support for Source Link

## Version 0.0.4

This version was released on January 18th, 2024 to be able to use BassBoom on .NET Framework applications.

### Improvements (Basolia)

* Added support for .NET Framework applications
* Updated dependencies

## Version 0.0.4.1

This version was released on January 21st, 2024.

### Improvements (Basolia)

* Improved support for 32-bit systems

## Version 0.0.4.2

This version was released on February 6th, 2024.

### Improvements (Basolia)

* Added `.snupkg` symbols

## Version 0.0.5

This version was released on February 20th, 2024.

### Improvements (Basolia)

* Added equalizer
* General improvements

### Removals (GUI music player)

* Removed the GUI music player until we can come up with a better appearance

## Version 0.0.6

This version was released on March 2nd, 2024.

### Improvements (Basolia)

* Added decoder tools
* Added native status tools
* Added version properties
* Band numbers are now titled appropriately
* General improvements

### Improvements (CLI music player)

* Updated Terminaux
* Added an option to show operating system and BassBoom info

## Version 0.1.0

This version was released on May 31st, 2024.

### Improvements (Basolia)

* Added radio station support
* Added support for ARM64 on macOS and Windows
* Fixed some bugs
* General improvements

### Improvements (CLI music player)

* Updated Terminaux
* Added more seeking options

## Version 0.1.1

This version was released on June 29th, 2024.

### Improvements (Basolia)

* Improved Icecast compatibility by IceFixing some bugs

## Version 0.1.2

This version was released on Jul 10th, 2024.

### Improvements (Basolia)

* Updated libraries
* Improved the radio track algorithm

## Version 0.1.3

This version was released on July 22nd, 2024.

### Improvements (Basolia)

* General improvements and bug fixes

## Version 0.1.4

This version was released on July 28th, 2024.

### Improvements (Basolia)

* General improvements

## Version 0.1.4.1

This version was released on July 28th, 2024.

### Improvements (Basolia)

* Root path is now considered when searching for `libwinpthread-1`

## Version 0.1.5

This version was released on August 1st, 2024.

### Improvements (Basolia)

* Used SpecProbe.Loader
* Updated all libraries

## Version 0.1.6

This version was released on August 10th, 2024.

### Improvements (Basolia)

* Updated MPG123
* Improved support for Windows ARM64
* Removed all 32-bit architecture support

## Version 0.1.6.1

This version was released on August 13th, 2024.

### Improvements (Basolia)

* Updated SpecProbe

## Version 0.1.7

This version was released on August 19th, 2024.

### Improvements (Basolia)

* Updated SpecProbe to 3.0.0

## Version 0.1.8

This version was released on September 4th, 2024.

### Improvements (Basolia)

* Added nullable support

## Version 0.1.9

This version was released on October 17th, 2024.

### Improvements (Basolia)

* Fixed a security issue concerning System.Text.Json

## Version 0.1.10.1

This version was released on November 6th, 2024 to bring some improvements and to add some features.

### Improvements (Basolia)

* Updated MPG123 to 1.32.9 that fixes [CVE-2024-10573](https://nvd.nist.gov/vuln/detail/CVE-2024-10573)

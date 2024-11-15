---
description: How to use BassBoom.Basolia
icon: laptop
---

# Using Basolia

Usage of the Basolia library may not look easy at first, but they will look easy once you get used to it and its syntax. In order to be able to use BassBoom Basolia functions, you need to make a new instance of the `BasoliaMedia` class. This allows you to initialize the Basolia library either using your default executable directory or using your customized directory that contains the `runtimes` folder that contains the mpg123 libraries, such as in the case of Nitrocid.BassBoom addon.

{% code title="Somewhere in your code" lineNumbers="true" %}
```csharp
basoliaMedia = new BasoliaMedia();
```
{% endcode %}

A music player built with BassBoom is provided with the base BassBoom source code. You can read its source code [here](https://github.com/Aptivi/BassBoom/blob/main/BassBoom.Cli/CliBase/).

{% hint style="info" %}
You'll need to give an instance of `BasoliaMedia` to the Basolia functions that require it.
{% endhint %}

The Basolia library is categorized to six categories:

* **Devices**: Provides you functions that manipulate with the sound devices probed by the MPG123 library.
* **File**: Provides you functions that allow you to open and close the music file.
* **Format**: Provides you audio format tools, audio metadata tools, and audio decode tools.
* **Lyrics**: Provides you basic lyrics (.LRC) support.
* **Playback**: Provides you playback functions, such as playing, pausing, and stopping the music.
* **Albums**: Provides you functions that are able to help you more quickly prepare your studio album for your music collection.
* **Radio**: Provides you functions that let you play and query Internet radio stations.

Each category has its own page, so click on one of the pages in the left side pane. As for the general tools, you can get the MPG123 version and the BassBoom Basolia's version using the following properties located in `InitBasolia`:

* **MpgLibVersion**: Gives you the MPG123 version shipped with the `BassBoom.Native` NuGet package.
* **OutLibVersion**: Gives you the OUT123 version shipped with the `BassBoom.Native` NuGet package.
* **SynLibVersion**: Gives you the SYN123 version shipped with the `BassBoom.Native` NuGet package.
* **BasoliaVersion**: Gives you the `BassBoom.Basolia` version.

{% hint style="info" %}
In case you need to manually initialize the Basolia library, you can use the `InitBasolia.Init()` function.
{% endhint %}

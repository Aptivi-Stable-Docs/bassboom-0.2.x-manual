---
description: What's being said in your song?
icon: microphone-stand
---

# Lyrics

Just use the `LyricReader` class that contains:

* `GetLyrics(string)`

The string in this function must be a complete path to your `.lrc` or `.txt` file containing lyric information about your music. It can be of a standard form (only time in lines) and an extended form (time in lines and words). Once called, it returns a `Lyric` that contains information about your lyric, including a list of lyric lines defined with the `LyricLine` class. It contains:

* `string Line`: A lyric line
* `TimeSpan LineSpan`: Time of when a lyric line gets played
* `List<LyricLineWord> LineWords`: Group of words from the lyric line

`LyricLineWord` also contains these variables:

* `string Word`: A lyric word
* `TimeSpan WordSpan`: Time of when a word gets said

Basolia starts working on your provided lyric file by reading all the lines. Then, it checks to see if the line isn't one of the following:

* An empty line
* A non-lyric line
* A lyric line without a lyric line

If the line is really a lyric line, then it starts processing it by taking the time span from the line and parsing it to a `TimeSpan` and taking the lyrics from the line. Below shows the clarification of this process:

```
[01:13.40]Don't believe me, just watch!
 ~~~~~~~~ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  |        |
  |        \- Lyric line
  \---------- Time of the lyric
```

In case the lyric line contains time spans of when the words are said, defined like below:

```
[02:55.75]<02:55.75> Uptown <02:56.75> funk <02:56.95> you <02:57.05> up!
 ~~~~~~~~ ~~~~~~~~~~ ~~~~~~
  |        |          |
  |        |          \- Word to be said
  |        \------------ Time of when the word is said
  \--------------------- Time of when the line is said
```

Basolia will attempt to split these words to their time spans, or `00:00` if these time spans can't be found in the line. Once this is done, Basolia will install all the lyric lines (`LyricLine` class) to the list of lines in a new `Lyric` class instance, therefore returning it for usage in your applications.

A `Lyric` instance contains several functions that allow you to get various lyric lines, such as getting them from the start to the current duration, and from current duration to the end. These functions allow you to perform these operations:

* `GetLinesCurrent()`: Gets all the lines from the start to the current music duration
* `GetLinesUpcoming()`: Gets all the lines from the current music duration to the end
* `GetLastLineCurrent()`: Gets the last lyric line from the current music duration
* `GetLastLineWordsCurrent()`: Gets the last lyric line words from the current music duration
* `GetLinesToSpan()`: Gets all the lines from the start to the current span
* `GetLinesFromSpan()`: Gets all the lines from the current span to the end
* `GetLastLineAtSpan()`: Gets the last lyric line from the given time span
* `GetLastLineWordsAtSpan()`: Gets the last lyric line words from the given time span

While the first four functions require you to specify a working Basolia media instance to deal with the current duration, the last four functions don't require this instance, but require specifying a time span representing the target duration.

### An example <a href="#an-example" id="an-example"></a>

If you want a simple console app that lets you print the lyric lines as they play to simulate the lyric player feature usually found in your music player, the most minimal example of such an application is this:

```csharp
string path = "path/to/music.lrc";
var lyric = LyricReader.GetLyrics(path);
var lyricLines = lyric.Lines;
var shownLines = new List<LyricLine>();
var sw = new Stopwatch();
​
sw.Start();
foreach (var ts in lyricLines)
{
    while (sw.Elapsed < ts.LineSpan)
        Thread.Sleep(1);
​
    if (sw.Elapsed > ts.LineSpan)
    {
        Console.WriteLine(ts.Line);
        shownLines.Add(ts);
        if (shownLines.Count == lyricLines.Count)
            return;
    }
}
```

{% hint style="danger" %}
Radio stations never support lyrics, since this requires the radio stream to be seekable, which is impossible for online radio stations as they're audible "livestreams".
{% endhint %}

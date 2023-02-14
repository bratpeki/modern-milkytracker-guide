# A modern guide to MilkyTracker

## Tracker basics

Here, we will be covering the basics of **traditional** trackers.

I hightlight the term "traditional" because you will mainly hear that trackers are split into
traditional and modern trackers. Modern trackers have some neat features like plugin support, mixers and other niceties.

Whenever we refer to something as a "tracker" in this guide, it will be a traditional tracker.

### What are trackers?

Trackers are computer programs that enable users to create music via music samples.
They handle manipulation of one of four sample properties:

1. Volume
2. Pitch
3. Panning
4. Offset

A tracker allows storing the compositions the user creates under some
[module format](https://en.wikipedia.org/wiki/Module_file).
These formats are usually of a much smaller file size than the lossless export,
making trackers optimal for making "small", but good-sounding music.

### Origin of the name

We won't be going into too much history, since it's easy for those interested to find that information online.

What you should know is that the term "tracker", or "sound tracker", comes from the term **"track"**.<br>
A track is a single column in the program which holds musical data.<br>
And the act of placing notes into that track is called **tracking**.<br>
There is some debate on what you call a musician that tracks, since the term "tracker" fits, but is taken.
So more often than not, you'll just hear the term **"tracker musician"**.

### The basics of tracker music

#### Cells

Cells are single elements which make up a track.<br>
They usually contain the following information, most commonly in this exact order:

```
| Note  Octave | Instrument index | Volume | Effect |
| C   - 4      | .1               | 30     | 102    |
| C   # 4      | .1               | ..     | ...    |
```

Notice the second row, instead of the dash, there is a `#`, signifying that the note in that cell is C#.
This saves up on screen space.<br>
The dots are meant to be empty spaces. Some trackers show them, some don't. MT does.

Now, let's get into the individual elements!

##### Note and octave slot

##### Instrument index slot

##### Volume slot

##### Effect slot

## Further links

[>>> TRACKER BASICS](./trackerBasics.md)

[>>> TABLE OF CONTENTS](../README.md)<br>

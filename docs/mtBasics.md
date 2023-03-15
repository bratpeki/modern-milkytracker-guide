<!--
THIS WAS IN THE OTHER DOC AND SHOULD BE PROPERLY FORMATTED HERE

#### Instrument index slot

Here, you input the actual instrument that will be playing back.
We'll be touching on instruments more in another doc, namely the one relating to the XM file format.

#### Volume slot

Here, you will be writing the volume of the currently playing sound in the track.<br>
To save up on screen space, the volume is written in hexadecimal format and ranges from 0 to 64.
In MT's hexadecimal form, that is `00` to `40`.

#### Effect slot

The effects are the modifications to the four sample properties we mentioned earlier.
More on this in another doc.
-->

# MilkyTracker basics

This doc is reserved for explaining the basics of using MT.
It should quickly get you up and running to start making your own music.

Just in case, however, there will be another doc reserved for making a basic
MT track, where everything that's covered here will be used in practice.

## The XM file format

This section is reserved for explaining
what the XM file format is and
what you should know about it.

**This is a very important piece of theory to understand**,
because each tracker format works differently,
so understanding the one you're using is key to mastering it.

Okay, let's get into it.

### Intro to XM

A brief bit of history and introductory trivia about the format.

The XM (**"eXtended Module"**) is a direct decendant of the MOD (**"Module"**) format.<br>
Unlike a MOD, XM has:

- 16-bit sample support
- Instruments
- Sample looping
- The ability to store more than 4 tracks (up to 256 in MT)

and so on.

### Notes

The thing you should be met with are the "limits" of XM when it comes to notes.<br>
XM allows for placing all notes between C0 and B7, so you have 8 octaves of space.

Each note has a corresponding volume assigned to it. By default, it's the volume of the instrment.<br>
You can, of course, specify the volume yourself, in the [third column of the cell](./trackerBasics.md#cells).

Each note might also have an effect applied to it.<br>
They are plentiful and confusing at times, until you get used to them.<br>
The default state depends on what effect was there previously, or if there was any at all.<br>
Effects are, of course, specified in the [last column of the cell](./trackerBasics.md#cells).

### Instruments

Instruments are specified by the XI standard.

### Volume

### Effects

### Patterns

### Songs

[>>> BACK](../README.md)<br>

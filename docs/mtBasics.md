<!--
THIS WAS IN THE OTHER DOC AND SHOULD BE PROPERLY FORMATTED HERE

Notice how in the second row, instead of the dash, there is a `#`, signifying that the note in that cell is C#.
This saves up on screen space.<br>

#### Note and octave slot

What you input here is pretty self-explanatory.
You should, however, know the "limits" of MT when it comes to notes.
MT allows for placing all notes between C0 and B7, so you have 8 octaves of space.

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

This section is reserved for explaining what the XM file format is
and what you should know about it.

**This is a very important piece of theory to understand**,
because each tracker format works differently.

Okay, let's get into it.


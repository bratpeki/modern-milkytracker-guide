This doc is reserved for explaining what the XM file format is and what you should know about it.

**This is a very important piece of theory to understand**, because each tracker format works differently, so understanding the one you're using is key to mastering it.

Okay, let's get into it.

# Intro to XM

First, a brief bit of history and introductory trivia about the format.

The XM (**"eXtended Module"**) is a direct decendant of the MOD (**"MODule"**) format.

Unlike a MOD, XM has:

- 16-bit sample support
- Instruments
- Sample looping
- The ability to store more than 4 tracks (up to 128 in MT)

and so on.

XM is **very** modular.

Tracks, patterns and instruments can be saved and reused, each with their own standard.
The standards are named XT, XP and XI, and stand for **"eXtended Track/Pattern/Instrument"**.
Their file extensions are, as expected, `.xt`, `.xp` and `.xi`, respectively.

# Notes

The thing you should be met with are the "limits" of XM when it comes to notes.
XM allows for placing all notes between C0 and B7, so you have 8 octaves of space.

Each note has a corresponding volume assigned to it. By default, it's the volume of the instrument.
You can, of course, specify the volume yourself, in the [third column of the cell](./basics.md#cells).

Each note might also have an effect applied to it.
They are plentiful and confusing at times, until you get used to them.
The default state depends on what effect was there previously, or if there was any at all.
Effects are, of course, specified in the [last column of the cell](./basics.md#cells).
You can read about them in ["2.1. EFFECT GLOSSARY"](./fx.md).

## Note-off

There is a special kind of note known as **Note-off**, called **Key-off** in MT.
Note-off has special properties which depend on the context it is used in.
In short, it stops the note from playing and, if you have set an envelope
and/or Fadeout, play for a short period of time after the Note-off instruction.

There's more talk about Note-off below.

# Instruments

In one composition, you can have up to 128 XI instruments.

They have plenty of basic tools
that'll help you make the sound you're looking for.

## Volume envelope

Either turned on or off, via the `On` button.
If on, MT will read the slope and interpret its height as volume.

A slope is made out of points, 12 maximum.
The number can be changed with the buttons `Add` and `Del`.

If `Sustain` is on, the envelope will function as normal until the sustain point, after which it
will stay on that volume. Once the note is off (via [Note-off](#note-off)), the envelope will play
on as normal for as long as [Fadeout](#fadeout) is set.

If `Loop` is on, the envelope will continually replay the envelope segment between the loop start
and end points. Once the note is off (via [Note-off](#note-off)), the loop will play
on as normal for as long as [Fadeout](#fadeout) is set.

If the instrument volume is 0, the envelope will not play.

## Panning envelope

The panning envelope behaves exactly the same as the volume envelope, with the exception that MT
reads the slope height as panning instead of volume.

If above the centre, the panning will move right, and vice-versa.

## Volume (Instrument slot)

A hexadecimal value between `00` and `40` which presents the intensity of the sample playback.

The default value is `40`.

It stacks with the volume envelope.

## Panning

A hexadecimal value between `00` and `FF` which presents the intensity of the sample panning.

The default value is `80`.

It stacks with the panning envelope.

## Fine-tune

A value between -128 and 127 which presents microtonal tuning.

-128 is one note below.<br>
127 is one note above.

The default value is 0 (`+000`).

## Fadeout

A value that determines how quickly the volume of the sample drops to 0 after the
[Note-off](#fadeout).

Works only when the volume envelope is on.

You will usually have little use of the Fadeout setting, since the volume fall-off can be
controlled using the volume envelope.

It is, however, useful when you want to set long volume fall-off without moving the envelope points
very far away from the start.

The values range from `000` to `FFF`, including the last value, `cut`.

| Value | Meaning |
| -     | -       |
| `000` | No fall-off in volume, it will play the entire envelope as it is. |
| `FFF` | Fastest possible fall-off. |
| `cut` | Instant fall-off, the envelope will not play after the [Note-off](#note-off). |

As far as values `000`-`FFF` go, they are hexadecimal and range from 0 to 4095.
The Fadeout operates on the following rule, written in pseudocode:

```
FADEOUT_VOLUME = 32678

# Code below happens every tick for as long as VOLUME > 0

FADEOUT_VOLUME = FADEOUT_VOLUME - INSTRUMENT_FADEOUT_VALUE
VOLUME = (VOLUME * FADEOUT_VOLUME) / 32768
```

`cut` **is very specific and is not part of many XM trackers and players.**

You could very reliably simulate the effect of cut by setting the [Fadeout](#fadeout) to `FFF`,
or dropping the volume in the envelope all the way down very quickly. Some, however, would argue
that `cut` if useful when you're using effects that offset where you are on the envelope.

Ultimately, it's up to you.

## Vibrato

Vibrato control consists of 4 properties:

1. `Vibspeed`:

How quickly the vibrato is oscillating within the vibrato depth. Hexadecimal value.
Ranges from `00` (no vibrato) to `FF` (fastest possible vibrato).

2. `Vibdepth`:

How deep/high the vibrato goes. Hexadecimal value. Ranges from `0` (no vibrato depth, even with
`Vibspeed > 00`) to `F` (depth of one tone up/down).

3. `Vibsweep`:

The time, in player ticks, it takes the vibrato to reach the vibrato depth starting from `0`
(no depth). Hexadecimal value. Ranges from `00` (no sweep, the vibrato happens instantly) to `FF`
(255 ticks until the proper vibrato).

4. `Type`:

The oscillator which will govern how the vibrato happens.
Choice-driven value.

The choices are:

    - Sine (Default)
    - Square
    - Reverse sawtooth
    - Sawtooth

## Relative note

Allow you to set which note middle C actually is.

You operate it using the buttons `Octave up/dn` and `Note up/dn`.

The number in the bracket next to the relative note displays how far you are from middle C, for
example `C-5 (+12)` or `C-3 (-12)`.

## Samples

Samples are the most important part of the instrument.

Each instrument holds 16 samples unique to that instrument, meaning you cannot share them between
instruments unless you literally copy them from one instrument onto another. All samples are stored
in so-called sample slots.

All samples are mono. If you want to make stereo audio, you need to place two samples, pan them
far-left and far-right and play them simultaneously.

You can manually set which note plays which sample slow in an instrument. By default, each note
plays sample slot 0. Setting which note plays which sample slot is done with the
[Keyboard](./ui.md#keyboard).

Each sample can be looped between a manually set start and end point.

The possible looping modes are:

1. **No loop**

2. **Forward**:
Playback starts at the beginning of the sample, and plays as normal until the loop end point.
Then the playhead resets itself to the loop start point and playback loops between the loop start
and end points.

3. **Ping-pong**:
Playback starts at the beginning of the sample, and plays as normal until the loop end point.
Then the sample plays backward from the loop end point to the loop start point.
Then the sample plays forward from the loop start point to the loop end point.
This motion loops for as long as the sample is playing.

4. **One shot**:
Playback starts at the beginning of the sample, and plays as normal until the end of the sample.
Then the playhead resets itself to the beginning of the sample, and plays in "Forward" mode between
the loop start and end points. The loop start point is the sample as the sample beginning and any
attempt to change it sets the loop mode to "Forward".

# Volume (Track slot)

Similar to [volume in the XI instrument](#volume-instrument-slot), except that it overrides the
volume set by the instrument.

If no volume is set in the track and a new note is played, the volume is going to be the instrument
volume. If no volume is set in the track and no note is played, the volume is going to be same as
in the track above.

And example of the track slot volume is given below.

```
Instrument volume: 30

| TRACK               | VOLUME
| ------------------- |
| C-4 | .1 | .. | ... | 30
| ... | .. | .. | ... | 30
| ... | .. | 20 | ... | 20
| D#4 | .1 | 10 | ... | 10
| ... | .. | .. | ... | 10
| D#4 | .1 | .. | ... | 30
| ... | .. | 08 | ... | 08
| ... | .. | .. | ... | 08
```

# Effects

Effects allow manipulation of one of the key sample properties at a time.

There are many, so we'll cover them in ["2.1. EFFECT GLOSSARY"](./fx.md).

# Tracks

Tracks in XM are interesting because of one thing, and that is their behaviour when muted.
Upon muting a track in a composition, you are only stopping it from producing a sound.
Any effects that alter the song (such as [`Fxx`](./fx.md#fxx-set-song-speed) or
[`Gxx`](./fx.md#gxx-set-global-volume) will still affect the song.

# Patterns

Patterns are defined by 3 things:

    1. **The pattern number**:<br>
    In the MT GUI, specified as [`Patn.`](./ui.md#pattern-properties-window).
    The ID of the pattern, presented in hexadecimal.
    You can have a maximum of 255 different patterns.

    2. **The pattern length**:<br>
    In the MT GUI, specified as [`Len.`](./ui.md#pattern-properties-window).
    The number of cell rows in the pattern, presented in hexadecimal.
    You can have a maximum of 256 pattern rows per pattern, and a minimum of 1.
    The default value is `40`, 64 in decimal, or 4 bars split into 16th notes in 4/4 meter.

    3. **The pattern content**:<br>
    The actual notes and effects in the pattern.

At any point in the pattern you can change the [SPD and BPM](./basics.md#ticks-spd-and-bpm).

SPD ranges from 1 up to 31, in decimal.

BPM ranges from 32 up to 255, in decimal.

What you cannot change is the number of tracks in all patterns.
You can have at least 2 and at most 32 tracks in each pattern in standard XM.
In MT, you can "unlock" more tracks in the settings, either 64 or 128.

# Songs

A song is structured out of a table of **song order numbers** and **pattern numbers**.
The song order numbers are structured so that the next one is always greater than the previous one
by exactly 1. The pattern numbers can vary however you want.
So, if we want to play the song in the given order of patterns: `00`, `01`, `00`, `02`, the table
of song order numbers and pattern numbers will look like this:

```
ORDER | PATTERN
    0 | 00
    1 | 01
    2 | 00
    3 | 02
```

You can have a maximum of 256 patterns in a song.

By default, the song will loop after it is played in its entirety.
That means that after the song is played from start to finish, the playhead returns to song order
0 and replays the song. You can set which song order you want to return to.
The order that the track returns to is called the **repeating song order**.

## Global song volume

A property of the song which describes the intensity of the volume of the entire song.
By default, this value is `40` (64 in decimal), which is the maximum global volume.
The minimum is, of course, 0.
You can change the global volume using the [Gxx colume effect](./fx.md#gxx-set-global-volume).

## Song title

Each song has a title, which can be left blank.
The maximum title length is 20 characters.

---

[0. INTRODUCTION](./intro.md)

[1. TRACKER BASICS](./basics.md)

**2. THE XM FILE FORMAT**
- [Notes](#notes)
- [Intro to XM](#intro-to-xm)
- [Instruments](#instruments)
	- [Volume envelope](#volume-envelope)
	- [Panning envelope](#panning-envelope)
	- [Volume (Instrument slot)](#volume-instrument-slot)
	- [Panning](#panning)
	- [Fine-tune](#fine-tune)
	- [Fadeout](#fadeout)
	- [Vibrato](#vibrato)
	- [Relative note](#relative-note)
	- [Samples](#samples)
- [Volume (Track slot)](#volume-track-slot)
- [Effects](#effects)
- [Tracks](#tracks)
- [Patterns](#patterns)
- [Songs](#songs)
	- [Global song volume](#global-song-volume)
	- [Song title](#song-title)

[2.1. EFFECT GLOSSARY](./fx.md)

[3. MILKYTRACKER UI REFERENCE](./ui.md)

[3.1. INTERACTIVE UI ELEMENTS](./elems.md)

[3.2. WORKING WITH SAMPLES](./samples.md)

[3.3. WORKING WITH THE PATTERN EDITOR](./playlist.md)

[4. CONFIGURING MILKYTRACKER](./config.md)

[4.1. KEYBIND OPTIONS](./keybind.md)

[5. TIPS AND TRICKS](./tips.md)

[6. GOOD SOURCES](./sources.md)

[7. MAKING AN EXAMPLE SONG IN MILKYTRACKER](./song.md)

[8. THANKS](./thanks.md)

[9. MISSING DOCUMENTATION](./missing.md)

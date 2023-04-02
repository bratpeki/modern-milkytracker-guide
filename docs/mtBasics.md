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

XM is **very** modular.<br>
Tracks, patterns and instruments can be saved and reused, each with their own standard.<br>
The standards are named XT, XP and XI, and stand for **"eXtended Track/Pattern/Instrument"**.<br>
Their file extensions are, as expected, `.xt`, `.xp` and `.xi`, respectively.

### Notes

The thing you should be met with are the "limits" of XM when it comes to notes.<br>
XM allows for placing all notes between C0 and B7, so you have 8 octaves of space.

Each note has a corresponding volume assigned to it. By default, it's the volume of the instrument.<br>
You can, of course, specify the volume yourself, in the [third column of the cell](./trackerBasics.md#cells).

Each note might also have an effect applied to it.<br>
They are plentiful and confusing at times, until you get used to them.<br>
The default state depends on what effect was there previously, or if there was any at all.<br>
Effects are, of course, specified in the [last column of the cell](./trackerBasics.md#cells).

There is a special kind of note known as **Note-off**.
Note-off has special properties which depend on the context it is used in.
In short, it stops the note from playing and, if you have set an envelope
and/or Fadeout, play for a short period of time after the Note-off instruction.

There's more talk about Note-off below.

### Instruments

XI instruments have plenty of basic tools
that'll help you make the sound you're looking for,
so let's get into it!

#### Volume envelope

Either turned on or off, via the `On` button.<br>
If on, MT will read the slope and interpret its height as volume.

A slope is made out of points, 12 maximum.<br>
The number can be changed with the buttons `Add` and `Del`.

If `Sustain` is on, the envelope will function as normal
until the sustain point, after which it will stay on that volume.
Once the note is off (via Note-off), the envelope will play on as normal
for as long as Fadeout is set.

If `Loop` is on, the envelope will continually replay the
envelope segment between the loop start and end points.
Note-off doesn't affect it, it will continue to play the loop
for as long as Fadeout is set.

If the instrument volume is 0, the envelope will not play.

#### Panning envelope

The panning envelope behaves exactly the same as the volume envelope,
with the exception that MT reads the slope height as panning instead of volume.

If above the centre, the panning will move right, and vice-versa.

#### Volume (Instrument slot)

A hexadecimal value between `00` and `40`
which presents the intensity of the sample playback.

The default value is `40`.

It stacks with the volume envelope.

#### Panning

A hexadecimal value between `00` and `FF`
which presents the intensity of the sample panning.

The default value is `80`.

It stacks with the panning envelope.

#### Fine-tune

A value between -128 and 127 which presents microtonal tuning.

-128 is one note below.<br>
127 is one note above.

The default value is 0 (`+000`).

#### Fadeout

A value that determines
how quickly the volume of the sample drops to 0
after the Note-off.

Works only when the volume envelope is on.

You will usually have little use of the Fadeout setting, since the volume
fall-off can be controlled using the volume envelope.

It is, however, useful when you want to set long volume fall-off
without moving the envelope point very far away from the start.

The values range from `000` to `FFF`, including the last value, `cut`.

| Value | Meaning                                                           |
| ----- | ----------------------------------------------------------------- |
| `000` | No fall-off in volume, it will play the entire envelope as it is. |
| `FFF` | Fastest possible fall-off.                                        |
| `cut` | Instant fall-off, the envelope will not play after the Note-off.  |

As far as values `000`-`FFF` go, they are hexadecimal and range from 0 to 4095.
The Fadeout operates on the following rule, written in pseudocode:

```
FADEOUT_VOLUME = 32678

# Code below happens every tick for as long as VOLUME > 0

FADEOUT_VOLUME = FADEOUT_VOLUME - INSTRUMENT_FADEOUT_VALUE
VOLUME = (VOLUME * FADEOUT_VOLUME) / 32768
```

`cut` **is very specific and is not part of many XM trackers and players.**
You could simulate the effect of `cut` by simply not having any points in the volume envelope after the sustain point.
Some, however, would argue that it's useful when you're using effects that offset where you are on the envelope.
Ultimately, it's up to you.

#### Vibrato

Vibrato control consists of 4 properties:

1. `Vibspeed`:<br>
How quickly the vibrato is oscillating within the vibrato depth.<br>
Hexadecimal value.<br>
Ranges from `00` (no vibrato) to `FF` (fastest possible vibrato).

2. `Vibdepth`:<br>
How deep/high the vibrato goes.<br>
Hexadecimal value.<br>
Ranges from `0` (no vibrato depth, even with `Vibspeed > 00`) to `F` (depth of one tone up/down).

3. `Vibsweep`:<br>
The time, in player ticks, it takes the vibrato to reach the vibrato depth
starting from `0` (no depth).<br>
Hexadecimal value.<br>
Ranges from `00` (no sweep, the vibrato happens instantly) to `FF` (255 ticks until the proper vibrato).

4. `Type`:<br>
The oscillator which will govern how the vibrato happens.<br>
Choice-driven value.<br>
The choices are:

- Sine (Default)
- Square
- Reverse sawtooth
- Sawtooth

#### Relative note

Allow you to set which note middle C actually is.

You operate it using the buttons `Octave up/dn` and `Note up/dn`.

The number in the bracket next to the relative note displays how far you are from middle C,
for example `C-5 (+12)` or `C-3 (-12)`.

#### Samples

Samples are, arguably, the most important part of the instrument.

Each instrument holds 16 samples unique to that instrument,
meaning you cannot share them between instruments unless you literally
copy them from one instrument onto another.

**All samples are mono.**
If you want to make stereo audio, you need to place two samples,
pan them far-left and far-right and play them simultaneously.

The graphical keyboard in the instrument tab allows you to choose which sample is played by which note.
You select the sample you want to set, and then click, or hold and drag, on the keys. By default,
all notes play instrument 0.

### Volume (Track slot)

Similar to volume in the XI instrument, except that it overrides the volume set by the instrument.

### Effects

### Patterns

Patterns are specified by 3 things:

1. **The pattern number**:<br>
In the MT GUI, specified as `Patn.`<br>
The ID of the pattern, presented in hexadecimal.<br>
You can have a maximum of 255 different patterns.

2. **The pattern length**:<br>
In the MT GUI, specified as `Len.`<br>
The number of cell rows in the pattern, presented in hexadecimal.<br>
You can have a maximum of 256 pattern rows per pattern.<br>
The default value is `40`, or 4 bars split into 16th notes in 4/4 meter.

3. **The pattern content**:<br>
The actual notes.

### Songs

[>>> BACK](../README.md)<br>

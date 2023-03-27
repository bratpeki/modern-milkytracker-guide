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

There is a special kind of note known as **Note-off**.
Note-off has special properties which depend on the context it is used in.
In short, it stops the note from playing and, if you have set an envelope
and/or Fadeout, play for a short period of time after the Note-off instruction.

There's more talk about Note-off below.

### Instruments

Instruments are specified by their own standard, called XI (**"eXtended Instrument"**).
They can be saved as files, meaning that you can reuse them elsewhere.
XI instruments have plenty of basic tools that'll help you make the sound you're looking for,
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

A hexadecimal value between 0 (`00`) and 64 (`40`)
which presents the intensity of the sample playback.

The default value is 64 (`40`).

It stacks with the volume envelope.

#### Panning

A hexadecimal value between 0 (`00`) and 255 (`FF`)
which presents the intensity of the sample panning.

The default value is 128 (`80`).

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

# this happens every tick

FADEOUT_VOLUME = FADEOUT_VOLUME - INSTRUMENT_FADEOUT_VALUE
VOLUME = (VOLUME * FADEOUT_VOLUME) / 32768
```

`cut` **is very specific and is not part of many XM trackers and players.**
You could simulate the effect of `cut` by simply not having any points in the volume envelope after the sustain point.
Some, however, would argue that it's useful when you're using effects that offset where you are on the envelope.
Ultimately, it's up to you.

#### Vibrato

#### Relative note

#### Samples

### Volume (Track slot)

### Effects

### Patterns

### Songs

[>>> BACK](../README.md)<br>

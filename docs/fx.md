Here, we'll be covering effects you will *commonly* use. I'll leave out some effects which are useful for very specific use-cases.

What you should keep in mind is that some effects "play" differently on MODs, in comparison to how they would play on XMs.
This is called playback mode and can be found by clicking on the `OPTIONS` button in the top-left section of the main UI.
We'll keep in mind that the playback mode is always set to `Fasttracker 2.x` (that is, that you're composing in XM).

We'll also assume your resampling mode (in `SETTINGS > I/O`) is set to a non-Amiga option (ex. `Linear interpolation`).

All effects that we leave out, and specifics relating to the settings mentioned above, can be found in the `/docs/MilkyTracker.html` section of the original MT repo.
You can find that doc **in dark mode** in my fork [here](https://github.com/bratpeki/MilkyTracker/blob/master/docs/MilkyTracker.html).

Some things to note:

- The "(Memory)" added to certain effect syntax sections means that MT "remembers" the last used parameter **for that note**
    - "(Memory - ...)" means that only the parameter "..." is remembered
- Any bracket that looks like "(ex. ...)" shows how the current description relates to the example above

# Effect column effects

## 0xy Arpeggio

**Syntax**:

`0` `OFFSET X` `OFFSET Y`

**Example**:

```
| C-4 | .1 | .. | 037 |
| ... | .. | .. | 037 |
```

**Description**:

Arpeggio quickly alters the note pitch between the base note (ex. `C-4`) and the semitone offsets `X` (ex. 3 = `D#4`) and `Y` (ex. 7 = `G-4`).

Each pitch is played for the duration of 1 tick.
If SPD is higher than 3 (meaning there are more than 3 ticks per row), the sequence is looped.

## 1xx Portamento up

**Syntax**:

`1` `PORTAMENTO SPEED` or<br>
`1` `00` (Memory)

**Example**:

```
| TRACK               | PORTAMENTO (effect equivalent)
| ------------------- |
| C-4 | .1 | .. | 103 | 103
| ... | .. | .. | 100 | 103
| ... | .. | .. | ... | None
| ... | .. | .. | 107 | 107
| ... | .. | .. | 100 | 107
```

**Description**:

Bends the note pitch up.

The greater the speed, the greater the bend.

The bending depends on the frequency table, BPM, SPD, the current note, and some other instrument-related settings, so it's pretty difficult to calculate which note it will "climb" to when you use this effect. So, go by trial and error! :)

## 2xx Portamento down

**Syntax**:

`2` `PORTAMENTO SPEED` or<br>
`2` `00` (Memory)

**Example**:

```
| TRACK               | PORTAMENTO (effect equivalent)
| ------------------- |
| C-4 | .1 | .. | 203 | 203
| ... | .. | .. | 200 | 203
| ... | .. | .. | ... | None
| ... | .. | .. | 207 | 207
| ... | .. | .. | 200 | 207
```

**Description**:

Bends the note pitch down.

The greater the speed, the greater the bend.

The bending depends on the frequency table, BPM, SPD, the current note, and some other instrument-related settings, so it's pretty difficult to calculate which note it will "climb" to when you use this effect. So, go by trial and error! :)

## 3xx Portamento to note

**Syntax**:

`3` `PORTAMENTO SPEED` or<br>
`3` `00` (Memory)

**Example**:

```
| TRACK               | PORTAMENTO (effect equivalent)
| ------------------- |
| C-4 | .1 | .. | ... | None
| ... | .. | .. | ... | None
| D-4 | .. | .. | 301 | 301
| ... | .. | .. | 300 | 301
| ... | .. | .. | ... | None
| ... | .. | .. | 300 | 301
```

**Description**:

Slides from the original note (ex. `C-4`) to the target note (ex. `D-4`).

If the volume envelope on the instrument is on, the new note (ex. `D-4`) will apply it on the sound again, in addition to sliding.

<!-- TODO: Nicely elaborate on 1xx, 2xx and 3xx -->

## 4xy Vibrato

**Syntax**:

`4` `SPEED` `DEPTH` or<br>
`4` `0` `DEPTH` (Memory - `SPEED`) or<br>
`4` `SPEED` `0` (Memory - `DEPTH`) or<br>
`4` `00` (Memory)

**Example**:

```
| TRACK               | VIBRATO (effect equivalent)
| ------------------- |
| C-4 | .1 | .. | ... | None
| ... | .. | .. | 41F | 41F
| ... | .. | .. | 400 | 41F
| ... | .. | .. | ... | None
| ... | .. | .. | 400 | 41F
| ... | .. | .. | ... | None
| ... | .. | .. | 42F | 42F
| ... | .. | .. | 400 | 42F
| ... | .. | .. | ... | None
```

**Description**:

Alters note pitch up and down in the range of a full tone.
Starts by going down.

## 7xy Tremolo

**Syntax**:

`7` `SPEED` `DEPTH` or<br>
`7` `0` `DEPTH` (Memory - `SPEED`) or<br>
`7` `SPEED` `0` (Memory - `DEPTH`) or<br>
`7` `00` (Memory)

**Example**:

```
| TRACK               | TREMOLO (effect equivalent)
| ------------------- |
| C-4 | .1 | .. | 72F | 72F
| ... | .. | .. | 700 | 72F
| ... | .. | .. | ... | None
| ... | .. | .. | 700 | 72F
| ... | .. | .. | 7F0 | 7FF
| ... | .. | .. | 701 | 7F1
| ... | .. | 30 | ... | None, volume reset
```

**Description**:

Alters note volume up and down at a given speed and depth.

The volume is not reset after the effect.

## 8xx Set note panning position

**Syntax**:

`8` `POSITION`

**Example**:

```
| C-4 | .1 | .. | 800 |
| ... | .. | .. | ... |
| ... | .. | .. | 880 |
```

**Description**:

Pans the currently playing tone.
`00` is far left, `80` is center and `FF` is far-right.

This effect overrides the panning value defined by the instrument sample settings.

The effect is not reset if there is no argument on the next pattern line (ex. in the second pattern line, the tone is still panned far-left, and is reset back to the center on the third pattern line).

## 9xx Sample offset

**Syntax**:

`9` `OFFSET MULTIPLIER`

**Example**:

```
| C-4 | .1 | .. | 907 |
| ... | .. | .. | ... |
```

**Description**:

Offsets the sample playback start position by `OFFSET MULTIPLER`*256 bytes.
Keep in mind that `OFFSET MULTIPLER` is read in hex.
So, with `901`, you are offsetting the sample playback start position by 256 (`0x100`) bytes, with `902` by 512 bytes, and so on.

The maximum offset amount is 65280 (0x10000) bytes.
**So, any sample block over 9FF cannot be started from.**

`900`, of course, makes no change to the sample playback.

If you're dealing with a large sample, and intend to chop it using 9xx, consider [resampling the sample](./samples.md#resample).

## Axy Volume slide

**Syntax**:

`A` `VOLUME SLIDE UP VALUE` `VOLUME SLIDE DOWN VALUE`

**Example**

```
| TRACK               | VOLUME (hex)
| ------------------- |
| ... | .. | .. | F03 |
| C-4 | .1 | 30 | A04 | 30 - (3-1)*4 = 28
| ... | .. | .. | ... | 28
| ... | .. | .. | A40 | 28 + (3-1)*4 = 30
```

**Description**:

**After the first tick**, the command does one of the two:

- Increases the volume by `VOLUME SLIDE UP VALUE` each tick of the row
- Decreases the volume by `VOLUME SLIDE DOWN VALUE` each tick of the row

If both are used at the same time, the volume is only increased by `VOLUME SLIDE UP VALUE`.<br>
**I highly advise against using both at the same time, since playback is unpredictable on different players.**

## Cxx Set note volume

**Syntax**:

`C` `VOLUME`

**Example**:

```
| C-4 | .1 | .. | C40 |
| ... | .. | .. | C20 |
| ... | .. | .. | C10 |
| ... | .. | .. | C08 |
| ... | .. | .. | C04 |
| ... | .. | .. | C02 |
| ... | .. | .. | C01 |
```

**Description**:

Sets the sample playback volume, **overriding both the instrument sample volume setting and the volume in the volume column**.

Just like the other two volume settings, the value is a hex number between `00` and `40`.

## Fxx Set song speed

**Syntax**:

`F` `VALUE`

**Example**:

```
| TRACK 1 (BPM)        | TRACK 2 (SPD)        |
| -------------------- | -------------------- |
| ... | .. | ... | F90 | ... | .. | ... | F06 |
```

**Description**:

When `VALUE` is between `01` (1) and `1F` (31), `VALUE` will be the new SPD.<br>
When `VALUE` is between `20` (32) and `FF` (255), `VALUE` will be the new BPM.

## Gxx Set global volume

**Syntax**:

`G` `VALUE`

**Example**:

```
| ... | .. | ... | G40 |
```

**Description**:

Sets the global song volume.

By default, the global song volume will be `40`.

This setting cannot be set graphically, and can only be altered using the `Gxx` command.

# Volume column effects

## xx Set note volume

**Syntax**:

`VALUE`

**Example**:

```
| C-4 | .1 | 3F | ... |
```

**Description**:

Sets the sample playback volume.

Overrides the instrument sample volume setting.

## +x Volume slide up

**Syntax**:

`+` `VALUE`

**Example**:

```
| C-4 | .1 | +2 | ... |
```

**Description**:

Increases the note volume by `VALUE` each tick.<br>
SPD acts as a multilpier (ex. if SPD is 3, for `+2`, the note volume will be increased by 3x2 = 6).

Same as using `A` `VALUE` `0` in the effect column.

## -x Volume slide down

**Syntax**:

`-` `VALUE`

**Example**:

```
| C-4 | .1 | -2 | ... |
```

**Description**:

Decreases the note volume by `VALUE` each tick.<br>
SPD acts as a multilpier (ex. if SPD is 3, for `+2`, the note volume will be decreased by 3x2 = 6).

Same as using `A` `0` `VALUE` in the effect column.

## Ux Fine volume slide up

**Syntax**:

`U` `VALUE`

**Example**:

```
| C-4 | .1 | ▲2 | ... |
```

**Description**:

Similar to [+X VOLUME SLIDE UP](#x-volume-slide-up), except that it changes the volume per row (ex. the volume will increase by 2).

Displayed as `▲x`.

## Dx Fine volume slide down

**Syntax**:

`D` `VALUE`

**Example**:

```
| C-4 | .1 | ▼2 | ... |
```

**Description**:

Similar to [-X VOLUME SLIDE DOWN](#-x-volume-slide-down), except that it changes the volume per row (ex. the volume will decrease by 2).

Displayed as `▼x`.

## Lx Panning slide left

**Syntax**:

`L` `VALUE`

**Example**:

I'm using `L` instead of the `◀` you'll see in the program.<br>
This is because that character is two character widths wide, so this makes the example easier to read.

```
| TRACK               | PAN
| ------------------- |
| C-4 | .1 | .. | F03 | 80 (Center)
| ... | .. | L2 | ... | 80 - 2*3 = 7A
| ... | .. | .. | 300 | 7A
| ... | .. | .. | ... | 7A
| ... | .. | .. | 880 | 80
```

**Description**:

Slides the pan, once per tick, over to the left.
SPD acts like a multiplier.

`3xx` and `◀x` share memory (ex. in the second row we slide the pan over to `7A`, and in the third row the `300` keeps the pan at `7A`).

Displayed as `◀x`.

## Rx Panning slide right

**Syntax**:

`R` `VALUE`

**Example**:

I'm using `R` instead of the `▶` you'll see in the program.<br>
This is because that character is two character widths wide, so this makes the example easier to read.

```
| TRACK               | PAN (hex)
| ------------------- |
| C-4 | .1 | .. | F03 | 80 (center)
| ... | .. | R1 | ... | 80 + 1*3 = 83
| ... | .. | .. | 300 | 83
| ... | .. | .. | ... | 83
| ... | .. | .. | 880 | 80
```

**Description**:

Slides the pan, once per tick, over to the left.
SPD acts like a multiplier.

`3xx` and `▶x` share memory (ex. in the second row we slide the pan over to `83`, and in the third row the `300` keeps the pan at `83`).

Displayed as `▶x`.

## Px Set note panning position

**Syntax**:

`P` `VALUE`

**Example**:

```
| TRACK               | PAN (hex)
| ------------------- |
| C-4 | .1 | P0 | ... | 00
| ... | .. | P3 | ... | 33
| ... | .. | .. | ... | 33
| ... | .. | .. | 880 | 80
```

**Description**:

Pan the note from the volume column.

`P` `VALUE` equates to using `8` `VALUE` `VALUE` in the effect column.

---

[>>> MILKYTRACKER UI](./ui.md)

[>>> BACK TO START](../README.md)

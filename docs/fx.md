# Effect glossary

Here, we'll be covering effects you will *commonly* use. I'll leave out some effects which are useful for very specific use-cases.

<!-- TODO: Axy, Bxx, Dxx, Kxx -->

What you should keep in mind is that some effects play differently on MODs than on XMs.
This is called playback mode and can be found by clicking on the `OPTIONS` button in the top-left section of the main UI.
We'll keep in mind that the playback mode is always set to `Fasttracker 2.x` (that is, that you're composing in XM).

We'll also assume your resampling mode (in `SETTINGS > I/O`) is set to a non-Amiga option (ex. `Linear interpolation`).

All effects that we leave out, and specifics relating to the settings mentioned above, can be found in the `/docs/MilkyTracker.html` section of the original MT repo.
You can find that doc **in dark mode** in my fork [here](https://github.com/bratpeki/MilkyTracker/blob/master/docs/MilkyTracker.html).

## Effect column effects

Some things to note:

- The "(Memory)" added to certain effect syntax sections means that MT "remembers" the last used parameter **for that note**
    - "(Memory - ...)" means that only the parameter "..." is remembered
- Any bracket that looks like "(ex. ...)" shows how the current description relates to the example above

### 0xy Arpeggio

**Syntax:**

`0` `OFFSET X` `OFFSET Y`

**Example:**

```
| C-4 | .1 | .. | 037 |
| ... | .. | .. | 037 |
```

**Description:**

Arpeggio quickly alters the note pitch between the base note (ex. `C-4`) and the semitone offsets `X` (ex. 3 = `D#4`) and `Y` (ex. 7 = `G-4`).

Each pitch is played for the duration of 1 tick.
If SPD is higher than 3 (meaning there are more than 3 ticks per row), the sequence is looped.

### 1xx Portamento up

**Syntax:**

`1` `PORTAMENTO SPEED` or<br>
`1` `00` (Memory)

**Example:**

```
| TRACK               | PORTAMENTO
| ------------------- |
| C-4 | .1 | .. | 103 | 103
| ... | .. | .. | 100 | 103
| ... | .. | .. | ... | None
| ... | .. | .. | 107 | 107
| ... | .. | .. | 100 | 107
```

**Description:**

Bends the note pitch up.

The greater the speed, the greater the bend.

The bending depends on the frequency table, BPM, SPD, the current note, and some other instrument-related settings, so it's pretty difficult to calculate which note it will "climb" to when you use this effect. So, go by trial and error! :)<br>
The same applies for [2xx PORTAMENTO DOWN](#2xx-portamento-down) and [3xx PORTAMENTO TO NOTE](#3xx-portamento-to-note).

### 2xx Portamento down

**Syntax:**

`2` `PORTAMENTO SPEED` or<br>
`2` `00` (Memory)

**Example:**

```
| TRACK               | PORTAMENTO
| ------------------- |
| C-4 | .1 | .. | 203 | 203
| ... | .. | .. | 200 | 203
| ... | .. | .. | ... | None
| ... | .. | .. | 207 | 207
| ... | .. | .. | 200 | 207
```

**Description:**

Bends the note pitch down.

For more information read [1xx PORTAMENTO UP](#1xx-portamento-up).

### 3xx Portamento to note

**Syntax:**

`3` `PORTAMENTO SPEED` or<br>
`3` `00` (Memory)

**Example:**

```
| TRACK               | PORTAMENTO
| ------------------- |
| C-4 | .1 | .. | ... | None
| ... | .. | .. | ... | None
| D-4 | .. | .. | 301 | 301
| ... | .. | .. | 300 | 301
| ... | .. | .. | ... | None
| ... | .. | .. | 300 | 301
```

**Description:**

Bends down from the original note (ex. `C-4`) to the target note (ex. `D-4`).

For more information read [1xx PORTAMENTO UP](#1xx-portamento-up).

### 4xy Vibrato

**Syntax:**

`4` `SPEED` `DEPTH` or<br>
`4` `0` `DEPTH` (Memory - `SPEED`) or<br>
`4` `SPEED` `0` (Memory - `DEPTH`) or<br>
`4` `00` (Memory)

**Example:**

```
| TRACK               | VIBRATO
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

**Description:**

Alters note pitch up and down in the range of a full tone.
Starts by going down.

### 7xy Tremolo

**Syntax:**

`7` `SPEED` `DEPTH` or<br>
`7` `0` `DEPTH` (Memory - `SPEED`) or<br>
`7` `SPEED` `0` (Memory - `DEPTH`) or<br>
`7` `00` (Memory)

**Example:**

```
| TRACK               | TREMOLO
| ------------------- |
| C-4 | .1 | .. | 72F | 72F
| ... | .. | .. | 700 | 72F
| ... | .. | .. | ... | None
| ... | .. | .. | 700 | 72F
| ... | .. | .. | 7F0 | 7FF
| ... | .. | .. | 701 | 7F1
| ... | .. | 30 | ... | None, volume reset
```

**Description:**

Alters note volume up and down at a given speed and depth.

The volume is not reset after the effect.

### 8xx Set note panning position

**Syntax:**

`8` `POSITION`

**Example:**

```
| C-4 | .1 | .. | 800 |
| ... | .. | .. | ... |
| ... | .. | .. | 880 |
```

**Description:**

Pans the currently playing tone.
`00` is far left, `80` is center and `FF` is far-right.

This effect overrides the panning value defined by the instrument sample settings.

The effect is not reset if there is no argument on the next pattern line (ex. in the second pattern line, the tone is still panned far-left, and is reset back to the center on the third pattern line).

### 9xx Sample offset

**Syntax:**

`9` `OFFSET MULTIPLIER`

**Example:**

```
| C-4 | .1 | .. | 907 |
| ... | .. | .. | ... |
```

**Description:**

Offsets the sample playback start position by `OFFSET MULTIPLER`*256 bytes.
Keep in mind that `OFFSET MULTIPLER` is read in hex.
So, with `901`, you are offsetting the sample playback start position by 256 (`0x100`) bytes, with `902` by 512 bytes, and so on.

The maximum offset amount is 65280 bytes.

`900`, of course, makes no change to the sample playback.

### Cxx Set note volume

**Syntax:**

`C` `VOLUME`

**Example:**

```
| C-4 | .1 | .. | C40 |
| ... | .. | .. | C20 |
| ... | .. | .. | C10 |
| ... | .. | .. | C08 |
| ... | .. | .. | C04 |
| ... | .. | .. | C02 |
| ... | .. | .. | C01 |
```

**Description:**

Sets the sample playback volume, **overriding both the instrument sample volume setting and the volume in the volume column**.

Just like the other two volume settings, the value is a hex number between `00` and `40`.

### Fxx Set song speed

**Syntax:**

`F` `VALUE`

**Example:**

```
| TRACK 1 (BPM)        | TRACK 2 (TICK RATE)  |
| -------------------- | -------------------- |
| ... | .. | ... | F90 | ... | .. | ... | F06 |
```

**Description:**

When `VALUE` is between `01` (1) and `1F` (31), `VALUE` will be the new tick rate.

When `VALUE` is between `20` (32) and `FF` (255), `VALUE` will be the new BPM.

### Gxx Set global volume

**Syntax:**

`G` `VALUE`

**Example:**

```
| ... | .. | ... | G40 |
```

**Description:**

Sets the global song volume.

By default, the global song volume will be `40`.

This setting cannot be set graphically, and can only be altered using the `Gxx` command.

## Volume column effects

### xx Set note volume

**Syntax:**
**Example:**
**Description:**

### +x Volume slide up

**Syntax:**
**Example:**
**Description:**

### -x Volume slide down

**Syntax:**
**Example:**
**Description:**

### Ux Fine volume slide up

**Syntax:**
**Example:**
**Description:**

Displayed as `▲x`.

### Dx Fine volume slide down

**Syntax:**
**Example:**
**Description:**

Displayed as `▼x`.

### Lx Panning slide left

**Syntax:**
**Example:**
**Description:**

Displayed as `◀x`.

### Rx Panning slide right

**Syntax:**
**Example:**
**Description:**

Displayed as `▶x`.

[>>> BACK TO START](../README.md)<br>

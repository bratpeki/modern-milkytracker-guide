# Effect glossary

Here, we'll be covering effects you will *commonly* use.

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
**Example:**
**Description:**

### 9xx Sample offset

**Syntax:**
**Example:**
**Description:**

### Axy Volume slide

**Syntax:**
**Example:**
**Description:**

### Bxx Jump to order

**Syntax:**
**Example:**
**Description:**

### Cxx Set note volume

**Syntax:**
**Example:**
**Description:**

### Dxx Pattern break

**Syntax:**
**Example:**
**Description:**

### Gxx Set global volume

**Syntax:**
**Example:**
**Description:**

### Fxx Set song speed

**Syntax:**
**Example:**
**Description:**

### Kxx Key-off

**Syntax:**
**Example:**
**Description:**

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

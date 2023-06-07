# Effect glossary

Here, we'll be covering effects you will *commonly* use.

What you should keep in mind is that some effects play differently on MODs than on XMs.
This is called playback mode and can be found by clicking on the `OPTIONS` button in the top-left section of the main UI.
We'll keep in mind that the playback mode is always set to `Fasttracker 2.x` (that is, that you're composing in XM).

We'll also assume your resampling mode (in `SETTINGS > I/O`) is set to a non-Amiga option (ex. `Linear interpolation`).

All effects that we leave out, and specifics relating to the settings mentioned above, can be found in the `/docs/MilkyTracker.html` section of the original MT repo.
You can find that doc **in dark mode** in my fork [here](https://github.com/bratpeki/MilkyTracker/blob/master/docs/MilkyTracker.html).

## Effect column effects

### 0xy Arpeggio

**Syntax:**

`0` `OFFSET 1` `OFFSET 2`

**Example:**

```
| C-4 | .1 | .. | 037 |
| ... | .. | .. | 037 |
```

**Description:**

Arpeggio quickly alters the note pitch between the base note (`C-4`) and the semitone offsets `x` (3 = `D#4`) and `y` (7 = `G-4`).

Each pitch is played for the duration of 1 tick.
If SPD is higher than 3 (meaning there are more than 3 ticks per row), the sequence is looped.

### 1xx Portamento up

**Syntax:**

`1` `PORTAMENTO SPEED`

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

The bending depends on the frequency table, BPM, SPD, the current note, and some other instrument-related settings, so it's pretty difficult to calculate which note it will "climb" to when you use this effect. So, go by trial and error! :)

The last parameter is remembered, as long as it's used on the same note, so, in the example above, you can use `200` instead of `203`.

The same applies for [2xx PORTAMENTO DOWN](#2xx-portamento-down) and [3xx PORTAMENTO TO NOTE](#3xx-portamento-to-note).

### 2xx Portamento down

**Syntax:**

`2` `PORTAMENTO SPEED`

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

The last parameter is remembered, as long as it's used on the same note, so, in the example above, you can use `200` instead of `203`.

For more information read [1xx PORTAMENTO UP](#1xx-portamento-up).

### 3xx Portamento to note

**Syntax:**

`3` `PORTAMENTO SPEED`

**Example:**

```
| TRACK               | PORTAMENTO
| ------------------- |
| C-4 | .1 | .. | ... | None
| ... | .. | .. | ... | None
| D-4 | .. | .. | 301 | 301
| ... | .. | .. | 300 | 301
| ... | .. | .. | 300 | 301
| ... | .. | .. | 300 | 301
```

**Description:**

Bends down from the original note (in this case `C-4`) to the target note (in this case `D-4`).

The last parameter is remembered, as long as it's used on the same note, so, in the example above, you can use `300` instead of `301`.

For more information read [1xx PORTAMENTO UP](#1xx-portamento-up).

### 4xy Vibrato

**Syntax:**

`4` `SPEED` `DEPTH`

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

The last parameter is remembered, for the note currently being played.

### 7xy Tremolo

**Syntax:**
**Example:**
**Description:**

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

# Effect glossary

Here, we'll be covering effects you will *commonly* use.

What you should keep in mind is
that some effects play differently on MODs than on XMs.
This is called playback mode and can be found
by clicking on the `OPTIONS` button in the top-left section
of the main UI.
We'll keep in mind that the playback mode is always set to `Fasttracker 2.x`
(that is, that you're composing in XM).

We'll also assume you're resampling (in `SETTINGS > I/O`) is set to a non-Amiga option (ex. `Linear interpolation`).

All effects that we leave out, and specifics relating to the settings mentioned above, can be found in the
`/docs/MilkyTracker.html` section of the original MT repo.
You can find that doc **in dark mode** in my fork
[here](https://github.com/bratpeki/MilkyTracker/blob/master/docs/MilkyTracker.html).

## Effect column effects

### 0xy Arpeggio

**Syntax:**

`0` `OFFSET 1` `OFFSET 2`

**Example:**

```
C-4 .1 .. 037
... .. .. 037
```

**Description:**

Arpeggio quickly alters the note pitch between
the base note (`C-4`) and
the semitone offsets `x` (3 = `D#4`) and `y` (7 = `G-4`).

Each pitch is played for the duration of 1 tick.
If speed is higher than 3 (meaning there are more than 3 ticks per row), the sequence is looped.

### 1xx Portamento up

**Syntax:**

`1` `PORTAMENTO SPEED`

**Example:**

```
C-4 .1 .. 103
... .. .. 103
```

**Description:**

Bends the note pitch up, each tick, by the speed.

### 2xx Portamento down

**Syntax:**

`2` `PORTAMENTO SPEED`

**Example:**

```
C-4 .1 .. 203
... .. .. 203
```

**Description:**

Bends the note pitch down, each tick, by the speed.

### 3xx Portamento to note

### 4xy Vibrato

### 5xy Portamento to note with volume slide

### 6xy Vibrato with volume slide

### 7xy Tremolo

### 8xx Set note panning position

### 9xx Sample offset

### Axy Volume slide

### Bxx Jump to order

### Cxx Set note volume

### Dxx Pattern break

### Gxx Set global volume

### Fxx Set song speed

### Kxx Key-off

## Volume column effects

### xx Set note volume

### +x Volume slide up

### -x Volume slide down

### Ux Fine volume slide up

Displayed as `▲x`.

### Dx Fine volume slide down

Displayed as `▼x`.

### Lx Panning slide left

Displayed as `◀x`.

### Rx Panning slide right

Displayed as `▶x`.

[>>> BACK](../README.md)<br>

Let's create a basic electro loop using MilkyTracker!

# Setting the song up

Let's set the BPM to 128 using the [song and editing properties](./ui.md#song-and-editing-properties).
We'll keep the SPD at 6, since it's the standard setting.
We'll also name the song "my first song!", since it feels appropriate! :)

![firstSong_1](../img/firstSong_1.mp4)

---

Now, we'll select instrument 1, and load `kick.wav` into it using the [disk operations window](./ui.md#disk-operations-window),
by selecting the "Type" as "Sample".

We'll select instrument 2 either from the [instrument menu](./ui.md#instrument-menu) or by using the `Sh+DownArrow` keyboard shortcut.

We'll, similarly as for instrument 1, load `snare.wav` in the second instrument slot.

We'll load `closed_hat.wav` into the third instrument slot.

Right-clicking, or double-left-clicking, on the instrument slots in the [instrument menu](./ui.md#instrument-menu), will let us rename the instruments.

Let's name them "Kick", "Snare" and "Closed hat", respectivelly.

![firstSong_2](../img/firstSong_2.mp4)

---

Now, let's generate a synth using the square wave generator.

Let's select instrument 4, open the sample editor using `Ctrl+S`, and [generate](./samples.md#generators) a new square wave.
We'll do this by generating 32 samples, and a square wave of 1 period, at 25% volume.
We'll set the [looping mode to "Forward"](./ui.md#sample-editor).

We'll name it "Synth" in the instrument menu.
Let's also name the sample "Synth" from the sample menu, just so that we know which slot it is occupying.

![firstSong_3](../img/firstSong_3.mp4)

We'll edit instrument 4 in the [instrument editor](./ui.md#instrument-editor), by making the Fadeout set to 000, turning the
volume envelope on, and creating a "plucky" sound using a falloff.
We'll set the volume to 10.

![firstSong_4](../img/firstSong_4.mp4)

---

For the purposes of this example song, we have all the sounds we need!

# Working on pattern 0

Using the [pattern editor](TODO), let's generate a pattern that looks like this:

<!-- TODO -->

# Adding another pattern

Then, let's clone the pattern, using the [`CLN` button in the song arranger](./ui.md#the-song-arranger).

Let's just add a snare to the end, like so.

<!-- TODO -->

# Arranging the song

Now, let's use the [song arranger](TODO) so that we have the following song structure:

```
ORDER | PATTERN
    0 | 00
    1 | 01
    2 | 00
    3 | 01
```

We'll start with this structure:

```
ORDER | PATTERN
    0 | 00
    1 | 01
```

Let's click on the pattern `0 | 00` and then click `Ins.` twice. We'll get the following:

```
ORDER | PATTERN
    0 | 00
    1 | 00
    2 | 00
    3 | 01
```

Then, click on `1 | 00` and the `+` under the `Ins.` button.
We'll get the desired song structure named at the start of the section.

# Saving the song

Now, let's save the song using [the disk operator window]().
We're setting the type to "Module" and saving an XM module.
Let's name the export "my-first-track.xm"!

![firstSong_5](../img/firstSong_5.mp4)

# Exporting the song

Now, let's open the [disk operations window](./ui.md#disk-operations-window).
We're setting the type to "Module" and saving a WAV file.
Let's name the export "my-first-track.wav"!

We'll audo-adjust the mixer volume and export.

![firstSong_6](../img/firstSong_6.mp4)

You've now successfully made and exported your first MilkyTracker song!

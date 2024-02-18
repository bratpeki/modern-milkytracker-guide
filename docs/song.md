Let's create a basic house loop using MilkyTracker!

# Setting the song up

Let's set the BPM to 128 using the [song and editing properties](./ui.md#song-and-editing-properties).
We'll keep the Add at 6, since it's the standard setting.

---

Now, we'll select instrument 1, and load `kick.wav` into it using the [Disk operations window](./ui.md#disk-operations-window),
by selecting the "Sample" as "Type" 

We'll select instrument 2 either from the [instrument menu](./ui.md#instrument-menu) or by using the `Sh+DownArrow` keyboard shortcut.

We'll, similarly as for instrument 1, load `snare.wav` in the second instrument slot.

We'll load `closed_hat.wav` into the third instrument slot.

Right-clicking, or double-left-clicking, on the instrument slots in the [instrument menu](./ui.md#instrument-menu), will let us rename the instruments.

Let's name them "Kick", "Snare" and "Closed hat", respectivelly.

---

Now, let's generate a synth using the square wave generator.

Let's select instrument 4, open the sample editor using `Ctrl+S`, and [generate](./samples.md#generators) a new square wave.
We'll do this by generating 32 samples, and a square wave of 1 period, at 25% volume.
We'll set the [looping mode to "Forward"](./ui.md#sample-editor).

We'll edit instrument 4 in the [instrument editor](./ui.md#instrument-editor), by making the Fadeout set to 000, turning the
volume envelope on, and creating a "plucky" sound using a falloff.
We'll set the volume to 10.

We'll name it "Synth" in the instrument menu.
Its sample will also be named "Synth" from the sample menu.

---

For the purposes of this example song, we have all the sound we need!

# Working on pattern 0

Using the [Pattern editor](TODO), let's generate a pattern that looks like this:

<!-- TODO -->

Then, let's clone the pattern, using the [`CLN` button in the song arranger](./ui.md#the-song-arranger).

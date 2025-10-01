This doc is reserved for covering all the configuration options in MT.

# I/O

## Driver
Allows selection the audio driver you are using.

## Buffer

Allows setting the size of the audio buffer.
Usually, 1.0k to 2.0k is perfectly enough.

## Force 2^n sizes

Force the sizes to be powers of 2 (32, 64, 128, ..., 1.0k, 2.0k, ...).

## Mixervol

A percentage mulitplier of the amplification entire song.
Called the "mixer volume" because it literally changes the volume read from the
[mixer (peak meter)](./ui.md#song-peak-meter-tab).

I would recommend keeping this at 100% at all times.

## Amp

Output amplification of the song.
Not seen on the [peak meter](./ui.md#song-peak-meter-tab), it's just a change that makes the song
quieter for the tracker musician.

## Resampling

Allows setting how the played samples are interpolated.

Usually, you just want "Linear interpolation".

## Volume ramping

In FastTracker II, it was an anti-clicking mechanism in the mixer. I assume the same is true for MT.

Usually, you want this on.

## Mixer resolution

The sample rate of the playback and export.

Usually, you would either go for 44100Hz or 48000Hz.

## Frequency table

Affects how the frequency slides made with the `1xx`, `2xx` and `3xx` effects happen.

Usually, you want to use "Linear frequencies".

## Jam channels

If off, any keyboard playing is done on the current track.

If on, any keyboard playing is done on a virtual "jam channel",
so that your playing does not interrupt the current playback.

You would want this on if you want to experiment with different chords, leads, etc. while the
pattern or song is playing.

## Use

If "Jam channels" is on, sets how many "jam channels" there are.

<!-- MISSING: ## Recording -->

<!-- MISSING: ## Keyjazzing -->

<!-- MISSING: ## Editing -->

## Record key off

When recording notes, record the moment they are let go as well.
Once you let go of the key, a [Note-off](./xm.md#note-off) is placed.

## Rec. note delays

As the name suggests, the moment you play and, if "Record key off" is on, the moment you let go of
the note is recorded in higher precision, using the [`EDx`](./fx.md#edx-note-delay) and
[`Kxx`](./fx.md#kxx-key-off) effect column effects.

## XM channel limit

Set the maximum number of tracks you can have in a song.
In FastTracker II, this was 32.
You can set 32, 64 and 128.

# Layout

## Spacing

The pixel spacing between the [different elements in the cell](./basics.md#cells).

## Hex count

Sets how the [pattern lines](./basics.md#patterns) are counted.

If off, the count is decimal.

## Show zero effect

If on, shows `000` where there are no effects applied, similar to FastTracker II.

## Prospective

If on, shows the next and previous patterns in the song, darkened out.

Can be toggled with `Ctrl+P` or from the
[common MT options toggle window](./ui.md#song-title-length-and-peak-window--common-mt-options-toggle-window).

## Muting opacity

Sets the opacity of the muted tracks.

0% makes them invisible.

I usually keep it at 25%.

## ROW HIGHLIGHT SPACING

Used to highlight each n and m rows, where n and m rows are specified with
the values next to "1st" and "2nd".
The tickboxes next to "Full:" enable the row highlight spacing.

## Colors

The `I` button imports a colorscheme from a file and previews it.

The `E` button exports the currently applied colorscheme to a file.

The `RESTORE` button restores all the colorschemes to defaults.

The `PREVIEW` button previews a colorscheme.
In other words, it sets all the colors to those of the colorscheme without applying the changes.

The section below is used to set the colors of individual UI parts.
The listview contains the element you're currently changing.
The sliders next to "R", "G" and "B" are used for setting the color of the element.
`COPY` copies the RGB values, `PASTE` pastes them.
`<<` halves the values, `>>` doubles them.

The buttons "A"-"F" next to "Predef" are used for quickly loading some stored colorschemes.

To store the current colorscheme, hit `STORE` and then the slot "A"-"F" you want to store to.

## Resolutions

The `CUSTOM` button lets you define a custom resolution.

The `FULL` button sets the resolution to the screen size.

Below those buttons, you can find a listview containing common resolutions, as well as
&lt;Custom&gt;".

The radio buttons next to "Scale" define a multiplier of the resolution.
For example, if you used a resolution like 1000x1000, and a scale multiplier of 2,
the output resolution would be 2000x2000.

## Fullscreen

Self-explanatory.

# Fonts

## Pattern editor

Allows setting the size of the font in the pattern editor.

## Font face config

Allows setting what font face is used for what font size.

# Misc.

## Edit mode

Sets which keybinds you're using.

This guide uses the FastTracker II keybinds, as stated [here](./intro.md).

## Scrolling Style

Sets how the cursor moves across the screen.

The options are:

1. Scroll to end

    - Start at the top of the pattern
    - Move down one pattern line at a time when at the bottom of the pattern

2. Scroll to center

    - Start at the top of the pattern
    - Stay in the center of the pattern editor
    - When the end of the pattern is visible move the cursor down one pattern line at a time

3. Always centered

    - Self-explanatory.

<!-- MISSING: ## Paste autoresize -->
<!-- MISSING: ## Instr. backtrace -->

## TAB to note

If on, hitting the TAB key will move you to the note slot of the cell of the next track.

If off, hitting the TAB key will move you the same slot of the cell of the next track as the one
you were on. For example, if the cursor was in the volume slot of the cell, hitting TAB will move
you to the volume slot of the cell of the next track.

## Click to cursor

If on, clicking on the pattern editor will move the cursor there.

If off, clicking will make a selection, much like left-click dragging.

## Wrap cursor

If on, moving the cursor out of bounds (with the arrow keys) will wrap the cursor around the pattern.

<!-- MISSING: ## Enable undo buff -->
<!-- MISSING: ## AUTO-MIXDOWN STEREO SAMPLES -->
<!-- MISSING: ## Internal browser -->

## Splash screen

Self-explanatory.

You can read about the splash screen as a UI element [here](./ui.md#startup).

## ESTIMATE PLAYTIME AFTER LOAD

Self-explanatory.

You can read about the estimate playtime
[here](./ui.md#song-length-tab).

## Show scopes

Self-explanatory.

Can also be toggled with `Ctrl+Z`.

## Scope Style

Allows setting how the scopes will look.

The options are:

1. DOTS (Not filled, dotted line)
2. SOLID (Filled, full line)
3. SMOOTH LINES (Not filled, full line)

## Inv PatEd scroll

If on, the direction your cursor moves is opposite the direction you move your scrollwheel,
or the direction you move your fingers on the trackpad.

## Invert zoom

If off, you zoom in on the sample by scrolling down.

If on, you zoom in on the sample by scrolling up.

# Tabs

## Load module ... in new Tab

Whenever a module is opened, it will open in a new tab, instead of overriding the current one.

## Stop background

Set how the playback will behave with multiple tabs.
The options include:

1. Never (You can play multiple tabs simultaneously)
2. On Tab switch (When you change the active tab, the playback of the previous tab stops)
3. On Playback (The playback of the previous tab stops only when you play the pattern/song in the new tab)

## Tab switch resume

If on, the playback of the previous tab will continue when you switch back to it.

---

[0. INTRODUCTION](./intro.md)

[1. TRACKER BASICS](./basics.md)

[2. THE XM FILE FORMAT](./xm.md)

[2.1. EFFECT GLOSSARY](./fx.md)

[3. MILKYTRACKER UI REFERENCE](./ui.md)

[3.1. INTERACTIVE UI ELEMENTS](./elems.md)

[3.2. WORKING WITH SAMPLES](./samples.md)

[3.3. WORKING WITH THE PATTERN EDITOR](./playlist.md)

**4. CONFIGURING MILKYTRACKER**
- [I/O](#io)
- [Layout](#layout)
- [Fonts](#fonts)
- [Misc.](#misc)
- [Tabs](#tabs)

[4.1. KEYBIND OPTIONS](./keybind.md)

[5. TIPS AND TRICKS](./tips.md)

[6. GOOD SOURCES](./sources.md)

[7. MAKING AN EXAMPLE SONG IN MILKYTRACKER](./song.md)

[8. THANKS](./thanks.md)

[9. MISSING DOCUMENTATION](./missing.md)

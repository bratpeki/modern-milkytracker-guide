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
##mixer (peak meter)](./ui.md#song-title-length-and-peak-window--common-mt-options-toggle-window).

I would recommend keeping this at 100% at all times.

## Amp

Output amplification of the song.
Not seen on the peak meter, it's just a change that makes the song quieter for the tracker musician.

## Resampling

Allows setting how the played samples are interpolated.
Usually, you just want "Linear interpolation".

## Volume ramping

In FastTracker II, it was an anti-clicking mechanism in the mixer.
I assume the same is true for MT.
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
You would want this on if you want to experiment with different chords, leads, etc. while the pattern or song is playing.

## Use

If "Jam channels" is on, sets how many "jam channels" there are.

## Recording

TODO.

## Keyjazzing

TODO.

## Editing

TODO.

## Record key off

When recording notes, record the moment they are let go as well.
Once you let go of the key, a Note-off is placed.

## Rec. note delays

As the name suggests, the moment you play and, if "Record key off" is on, the moment you let go of the note is recorded in higher precision,
using the `EDx` and `Kxx` effects.

## XM channel limit

Set the maximum number of tracks you can have in a song.
In FastTracker II, this was 32.
You can set 32, 64 and 128.

# Layout

## Spacing

The pixel spacing between the
[different elements in the cell](./basics.md#cells).

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

TODO.

## Resolutions

TODO.

## Fullscreen

Self-explanatory.

# Fonts

## Pattern editor

Allows setting the size of the font in the playlist.
<!-- TODO: Pattern editor or Playlist? -->

## Font face config

Allows setting what font face is used for what font size.

# Misc.

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

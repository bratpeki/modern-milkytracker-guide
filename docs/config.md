This doc is reserved for covering all the configuration options in MT.

# I/O

- "Driver"<br>
Allows selection the audio driver you are using.

- "Buffer"<br>
Allows setting the size of the audio buffer.
Usually, 1.0k to 2.0k is perfectly enough.

- "Force 2^n sizes"<br>
Force the sizes to be powers of 2 (32, 64, 128, ..., 1.0k, 2.0k, ...).

- "Mixervol"<br>
A percentage mulitplier of the amplification entire song.
Called the "mixer volume" because it literally changes the volume read from the
[mixer (peak meter)](./ui.md#song-title-length-and-peak-window--common-mt-options-toggle-window).<br>
I would recommend keeping this at 100% at all times.

- "Amp"<br>
Output amplification of the song.
Not seen on the peak meter, it's just a change that makes the song quieter for the tracker musician.

- "Resampling"<br>
Allows setting how the played samples are interpolated.
Usually, you just want "Linear interpolation".

- "Volume ramping"<br>
In FastTracker II, it was an anti-clicking mechanism in the mixer.
I assume the same is true for MT.
Usually, you want this on.

- "Mixer resolution"<br>
The sample rate of the playback and export.
Usually, you would either go for 44100Hz or 48000Hz.

- "Frequency table"<br>
Affects how the frequency slides made with the `1xx`, `2xx` and `3xx` effects happen.
Usually, you want to use "Linear frequencies".

- "Jam channels"<br>
If off, any keyboard playing is done on the current track.
If on, any keyboard playing is done on a virtual "jam channel",
so that your playing does not interrupt the current playback.
You would want this on if you want to experiment with different chords, leads, etc. while the pattern or song is playing.

- "Use"<br>
If "Jam channels" is on, sets how many "jam channels" there are.

- "Recording"<br>
TODO.

- "Keyjazzing"<br>
TODO.

- "Editing"<br>
TODO.

- "Record key off"<br>
When recording notes, record the moment they are let go as well.
Once you let go of the key, a Note-off is placed.

- "Rec. note delays"<br>
As the name suggests, the moment you play and, if "Record key off" is on, the moment you let go of the note is recorded in higher precision,
using the `EDx` and `Kxx` effects.

- "XM channel limit"<br>
Set the maximum number of tracks you can have in a song.
In FastTracker II, this was 32.
You can set 32, 64 and 128.

# Layout

# Fonts

- "Pattern editor"<br>
Allows setting the size of the font in the playlist.
<!-- TODO: Pattern editor or Playlist? -->

- "Font face config"<br>
Allows setting what font face is used for what font size.

# Misc.

# Tabs

- "Load module ... in new Tab"<br>
Whenever a module is opened, it will open in a new tab, instead of overriding the current one.

- "Stop background"<br>
Set how the playback will behave with multiple tabs.
The options include:

1. Never (You can play multiple tabs simultaneously)
2. On Tab switch (When you change the active tab, the playback of the previous tab stops)
3. On Playback (The playback of the previous tab stops only when you play the pattern/song in the new tab)

- "Tab switch resume"<br>
If on, the playback of the previous tab will continue when you switch back to it.

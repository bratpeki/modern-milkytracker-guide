This doc is reserved for covering all the configuration options in MT.

#I/O

- "Driver"<br>
Allows selection the audio driver you are using.

- "Buffer"<br>
Allows setting the size of the audio buffer.
Usually, 1.0k to 2.0k is perfectly enough.

- "Force 2^n sizes"
Force the sizes to be powers of 2 (32, 64, 128, ..., 1.0k, 2.0k, ...).

- "Mixervol"
A percentage mulitplier of the amplification entire song.
Called the "mixer volume" because it literally changes the volume read from the
[mixer (peak meter)](./ui.md#song-title-length-and-peak-window--common-mt-options-toggle-window).
I would recommend keeping this at 100% at all times.

- "Amp"
Output amplification of the song.
Not seen on the peak meter, it's just a change that makes the song quieter for the tracker musician.

- "Resampling"
Allows setting how the played samples are interpolated.
Usually, you just want "Linear interpolation".

- "Volume ramping"
In FastTracker II, it was an anti-clicking mechanism in the mixer.
I assume the same is true for MT.
Usually, you want this on.

- "Mixer resolution"
The sample rate of the playback and export.
Usually, you would either go for 44100Hz or 48000Hz.

- "Frequency table"
Affects how the frequency slides made with the `1xx`, `2xx` and `3xx` effects happen.
Usually, you want to use "Linear frequencies".

- "Jam channels"
If off, any keyboard playing is done on the current track.
If on, any keyboard playing is done on a virtual "jam channel",
so that your playing does not interrupt the current playback.
You would want this on if you want to experiment with different chords, leads, etc. while the pattern or song is playing.

- "Use"
If "Jam channels" is on, sets how many "jam channels" there are.

This doc is reserved for giving some tips and tricks that will aid you in using MT, as well as trackers in general!

# Mixing

# Chorus

For this one, you would use the [EDx note delay effect]()!

Let's say we have a track playing one instrument, like so:

```
| TRACK 1             |
|---------------------|
| C-4 | .1 | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
| ... | .. | .. | ... |
```

We create a "chorus" like effect by adding more instances of the instrument, spacing them out over a small distance, like so:

```
| TRACK 1             | TRACK 2             | TRACK 3             |
|---------------------|---------------------|---------------------|
| C-4 | .1 | .. | ... | C-4 | .1 | .. | ED1 | C-4 | .1 | .. | ED2 |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
```

You can also just have a high BPM or small Speed and do the following:

```
| TRACK 1             | TRACK 2             | TRACK 3             |
|---------------------|---------------------|---------------------|
| C-4 | .1 | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | C-1 | .1 | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | C-4 | .1 | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... | ... | .. | .. | ... |
```

The first one is a bit more optimal, because with a higher BPM or smaller Speed, you have less "time" in your track.
In Layman's terms, your pattern is 4 times shorter, time-wise, when you lower the Speed from 4 to 1, or increase the BPM from 100 to 400.
In any case, either of the two methods work!

# Delay

Usually, the way you would do delay is to
**create copies of the sound, at a constant distance, making each instance quieter**.

If you have a very short sound, delay could look something like this:

<!-- Do the TRACK 1, 2, ... for each of these! -->

```
| TRACK 1             |
|---------------------|
| C-4 | .1 | 40 | ... |
| ... | .. | .. | ... |
| C-4 | .1 | 30 | ... |
| ... | .. | .. | ... |
| C-4 | .1 | 20 | ... |
| ... | .. | .. | ... |
| C-4 | .1 | 10 | ... |
| ... | .. | .. | ... |
| C-4 | .1 | 08 | ... |
| ... | .. | .. | ... |
| C-4 | .1 | 04 | ... |
| ... | .. | .. | ... |
```

If an instrument is longer, this might cut the previous sound off.
In that case, you can space these out like this:

```
| TRACK 1             | TRACK 2             |
|-------------------------------------------|
| C-4 | .1 | 40 | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | C-4 | .1 | 30 | ... |
| ... | .. | .. | ... | ... | .. | .. | ... |
| C-4 | .1 | 20 | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | C-4 | .1 | 10 | ... |
| ... | .. | .. | ... | ... | .. | .. | ... |
| C-4 | .1 | 08 | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | ... | .. | .. | ... |
| ... | .. | .. | ... | C-4 | .1 | 04 | ... |
| ... | .. | .. | ... | ... | .. | .. | ... |
```

You might need more tracks and more space, that all depends on the sound!

<!-- TODO: Maybe these should be headers, and not listitems? -->
The ["Split track options" section of the Advanced editor](./ui.md#advanced-editor) might help you with this.

# Sample chopping

The first thing you've got to understand is that [9xx](./fx.md#9xx-sample-offset) works.


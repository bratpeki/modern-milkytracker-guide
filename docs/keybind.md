This entire guide has been written with Windows/Linux and FastTracker II edit mode in mind.

Any help with the other keybinds is appreciated.

# FastTracker II edit mode

## Windows/Linux

### Windows

| Keys | Action |
| -    | -      |
| `Ctrl+X` | [Main window](./ui.md#main-window) |
| `Ctrl+S` | [Sample editor](./ui.md#sample-editor) |
| `Ctrl+I` | [Instrument editor](./ui.md#instrument-editor) |
| `Ctrl+Z` | [Toggle scopes](./ui.md#scopes) |
| `Ctrl+D` | [Disk operator](./ui.md#disk-operations-window) |
| `Ctrl+T` | [Transposition window](./ui.md#transposition-window) |
| `Ctrl+A` | [Advanced editor](./ui.md#advanced-editor) |
| `Ctrl+C` | [Configuration window](./ui.md#configuration-window) |
| `Ctrl+O` | [Quick options window](./ui.md#quick-options-window) |

### Pattern editor movement

| Keys | Action |
| -    | -      |
| Arrow keys                     | Move by open cell up/down, or by one slot left/right |
| `Tab`/`Sh+Tab`                 | Move to the next/previous track, can also [tab to the note slot specifically](./config.md#tab-to-note) |
| `Page Up`/`Page Down`          | Move up/down by 16 |
| `Home`/`End`                   | Go to the top/bottom of the pattern |
| `Sh` + up/down arrow keys      | Change the active instrument |
| `Ctrl+Sh` + up/down arrow keys | Change the active sample |
| `Ctrl` + up/down arrow keys    | Change the current file in the [disk operator](./ui.md#disk-operations-window) |
| `Ctrl` + left/right arrow keys | Go to the previous/next pattern |
| `Sh` + left/right arrow keys   | Go to the previous/next pattern in the [song order](./xm.md#songs) |
| `F9`                           | Go to the top of the pattern |
| `F10`                          | Go to 1/4 of the pattern |
| `F11`                          | Go to half of the pattern |
| `F12`                          | Go to 3/4 of the pattern |

### Playing and recording

| Keys | Action |
| -    | -      |
| `Tilde`/`Sh+Tilde`                       | Increase/decrease the [Add](./ui.md#add) by 1 |
| `F1` through `F8`                        | Select the octave (For `F1`, `Q` will play C1) |
| `Spc`                                    | While not playing , arms/disarms MT for recording |
| `CapsLock` and the key right of `LShift` | Places a ["Note-off"](./xm.md#note-off) |
| `2`, `3`, `5`,...                        | Playing sharp/flat notes |
| `Q`, `W`, `E`,...                        | Playing notes (`Q` is C) |
| `S`, `D`, `G`,...                        | Playing sharp/flat notes in the lower octave |
| `Y`/`Z`, `X`, `C`,...                    | Playing notes (`Y`/`Z` is C) in the lower octave |

### Playback

| Keys | Action |
| -    | -      |
| `AltGr` and `Ctrl+Enter` | Plays the current pattern |
| `Sh+Enter`               | Plays the current pattern, from the current line |
| `Right Ctrl` and `Enter` | Plays the song, starting from the current position in the song index |
| `Spc`                    | While playing, stops the playback |

### Muting

| Keys | Action |
| -    | -      |
| `Sh+M`      | Mute/unmute the current track |
| `Ctrl+Sh+M` | Invert muting |
| `Sh+U`      | Unmute all tracks |

### Cut/Copy/Paste

| Keys | Action |
| -    | -      |
| `Sh+F3` | Cutting the track contents |
| `Sh+F4` | Copying the track contents |
| `Sh+F5` | Pasting the track contents |
| `Alt+F3` | Cutting the selection block contents |
| `Alt+F4` | Copying the selection block contents |
| `Alt+F5` | Pasting the selection block contents |

### Sample editor

| Keys | Action |
| -    | -      |
| `Sh` + left-click hold | Draw sample |
| Left-click hold        | Make a selection in the sample |
| Right-click            | Opens the [sample manipulation drop-down](./samples.md#sample-manipulation) |
| Scroll                 | Zoom in and out of the sample, by 25% |

---

[0. INTRODUCTION](./intro.md)

[1. TRACKER BASICS](./basics.md)

[2. THE XM FILE FORMAT](./xm.md)

[2.1. EFFECT GLOSSARY](./fx.md)

[3. MILKYTRACKER UI REFERENCE](./ui.md)

[3.1. INTERACTIVE UI ELEMENTS](./elems.md)

[3.2. WORKING WITH SAMPLES](./samples.md)

[3.3. WORKING WITH THE PATTERN EDITOR](./playlist.md)

[4. CONFIGURING MILKYTRACKER](./config.md)

**4.1. KEYBIND OPTIONS**

[5. TIPS AND TRICKS](./tips.md)

[6. GOOD SOURCES](./sources.md)

[7. MAKING AN EXAMPLE SONG IN MILKYTRACKER](./song.md)

[8. THANKS](./thanks.md)

[9. MISSING DOCUMENTATION](./missing.md)

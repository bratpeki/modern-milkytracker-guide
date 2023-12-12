Here, we'll be covering the MT's UI and how to navigate around it.

I'll use shortcuts to indicate keyboard actions, such as `Ctrl+S`.
Keep in mind that `Ctrl` is the control key, `Sh` is the shift key, `Spc` is the space bar and `Alt` is, well, the alt key!
All the listed keyboard actions apply to the **FastTracker II edit mode**.

Also, left-, right- and middle-clicking will refer to their respective mouse actions.

Also, I'll talk about the various elements of the UI by first covering the ones you'll be using commonly, and then the rest.

**Before you read this**, you might want to read about the interactive UI elements in MT that are covered in "[3.1. INTERACTIVE UI ELEMENTS](./elems.md)".

# Startup

Upon first startup, you are going to be greeted by the MT splash screen:

![splash.png](../img/splash.png)

Afterwards, MT loads the [main window](#main-window).

The startup splash screen is easily disabled in the settings (`Misc. > Other > Splash screen`).

# Main window

![ui_startUpWin.png](../img/ui_startUpWin.png)

This is the only real GUI window in MT, all other "windows" that I refer to are just subwindows within the main window.

From here, you will be managing everything, from modules to the way your tracker works and looks.

You can always return to the main window by hitting `Ctrl+X`.

The elements in this window, from top-left to bottom-right, are:

1. [The general editor](#general-editor)
2. [The instrument menu](#instrument-menu)
3. [The sample menu](#sample-menu)
4. [The scopes](#scopes)
5. [The playlist](#playlist)

# General editor

![ui_generalEditor.png](../img/ui_generalEditor.png)

The general editor is the top-left window visible from the [main window](#main-window).

From here, you'll manage various properties relating to your song, your editing of the song, as well as toggle other windows.

You can return to this window by either hitting `Exit` on the windows that take its place (like the [disk operations window](#disk-operations-window), [transposition window](#transposition-window), etc) or by going back to the main window with `Ctrl+X`.

The elements in this window, from top-left to bottom-right, are:

1. [The song arranger](#the-song-arranger)
2. [Song title, length and peak window + Common MT options toggle window](#song-title-length-and-peak-window--common-mt-options-toggle-window)
4. [Song and editing properties](#song-and-editing-properties)
5. [Pattern editing window](#pattern-editing-window)
6. [General editor buttons window](#general-editor-buttons-window)

## The song arranger

![ui_generalEditor_songArr.png](../img/ui_generalEditor_songArr.png) Regular.<br>
![ui_generalEditor_songArrExpand.png](../img/ui_generalEditor_songArrExpand.png) Expanded view.

This window is used to arrange the patterns you've created into the final song.

- **Pattern sequence display**:
Allows you to view the song order number (in hex) and the pattern number (in hex), one next to the other.
In a new module, you have the pattern `00` set to order `0`.

- **Pattern sequence display expansion button**:
This button is above the `SEQ` button and allows you to hide the song pattern length and repeating song order.
This, in turn, expands the pattern sequence display further down, and allows for more readability.
Hitting the button toggles this behaviour on and off.
The example of this behaviour is above, on the second image of the section.

- `SEQ` button:
Adds a new pattern after the current one, if possible, so that its pattern number is the incremented previous pattern number.
So, if your pattern sequence is:
```
0 | 00
```
By hitting `SEQ` you will generate the following sequence:
```
0 | 00
1 | 01
```
If the current pattern in the sequence has the pattern number `FF`, the next one will be `00`, as well as every pattern after that next one.

- `CLN` button:
Works the same way as the `SEQ` button, except that it copies the content of the current pattern into the next one.

- `Ins.` button:
Inserts the current pattern at the next song order number.
The button has no effect if there are 255 patterns in the song.

- `Del` button:
Deletes the pattern from the current song order number and moves the next pattern into the deleted slot.
If there are no patterns after the deleted one (that is, if we deleted the last one) we just move back one song order to the previous pattern.
The button has no effect if there's only one pattern in the song.

- `+/-` buttons between `Ins.` and `Del`:
Increments or decrements the number of the pattern at the current song order.

- `+/-` buttons next to the song pattern length:
Adds a new pattern to the end of the song, or removes a pattern from the end of the song.
In case a new pattern is added, its pattern number is `00`.
The `+/-` buttons next to the song pattern length in the exapnded view have the same effect.

- `+/-` button next to the repeating song order:
Increments or decrements the repeating song order.

## Song title, length and peak window + Common MT options toggle window

![ui_generalEditor_songTitleTimePeak.png](../img/ui_generalEditor_songTitleTimePeak.png)<br>
![ui_generalEditor_songTitleTimePeak2.png](../img/ui_generalEditor_songTitleTimePeak2.png)<br>
![ui_generalEditor_songTitleTimePeak3.png](../img/ui_generalEditor_songTitleTimePeak3.png)

- "TITLE", "TIME" and "PEAK" tabs:
Allows the selection of which of those three things you want to look at.

- Song title text field tab:
Contains a text input field which changes the title of your song.
By default, the song title is an empty string.

- Song length tab:
Allows viewing the current time (hour:minute:second) that has elapsed since the module started playback, and the total time.
By default, in an empty startup module, the text in the tab reads `00:00:00 (00:00:07)`.
The `ESTIMATE` button estimates the total length of the song and updates the song length.
You usually have to click this button manually, but you can have MT estimate the time for you once the module is loaded, by ticking a checkbox in the settings (`Misc. > Other > ESTIMATE PLAYTIME AFTER LOAD`).

- Song peak tab:
Reads the intensity of the sound generated by the playback.
As per default, the peak is split into the left signal (left of center) and right signal (right of center), as well as the quiet (green), sufficient (yellow) and loud (red) areas.
If the song clips, the `PEAK LEVEL:` text above the peak will turn red. Right-clicking it resets it back to its default color, white.

- Common MT options toggle window:
This window consists of four buttons labeled `F`, `P`, `W` and `L`, in that order.
Right-clicking these toggles their respective options.
The options are:

| Label | Keyboard shortcut | Name of the action, taken from the MT manual  | Description |
| -     | -                 | -                                             | - |
| `F`   | `Ctrl+F`          | Song follow                                   | If on, the cursor follows the playhead. |
| `P`   | `Ctrl+P`          | Prospective pattern view                      | If on, the previous and next patterns in the song are visible. |
| `W`   | `Ctrl+W`          | Pattern wrapping                              | If on, during editing of a pattern, the cursor will wrap and stay on the current pattern, instead of moving to the next or previous one. |
| `L`   | `Ctrl+L`          | Pattern change behavior (live mode)           | If on, when you change the current pattern while another pattern is playing, it will first play the current one entirely, and then move on to the next one. If off, the pattern change happens immedietly, without wait. Used in live performances. |

## Song and editing properties

![ui_generalEditor_songEditProp1.png](../img/ui_generalEditor_songEditProp1.png) Regular.<br>
![ui_generalEditor_songEditProp2.png](../img/ui_generalEditor_songEditProp2.png) Flipped view.

This window consists of a couple properties related to the song and how you edit it.
The `+/-` buttons are placed next to their respective properties.
The `FLIP` button flips the display to show the rest of the editable properties.

- BPM:
The song's [BPM](./basics.md#ticks-spd-and-bpm).

- Spd:
The song's [SPD](./basics.md#ticks-spd-and-bpm).

- Add:
The ammount by which your cursor moves down after placing a note or effect. The cursor loops if pattern wrapping (`Ctrl+W`) is on.

- Oct:
The octave of the notes you place (ex. if `Oct` is equal to `04`, then the lowest key you can place with your keyboard is C4).

- The `Mainvol` property:
Shows you the [global song volume](./xm.md#global-song-volume).

## Pattern editing window

![ui_generalEditor_pattern.png](../img/ui_generalEditor_pattern.png)

- `+`/`-` buttons next to `Patn.`:
Switch between different patterns.

- `+`/`-` buttons next to `Len.`:
Increase or decrease the pattern length.
This action is desctructive; in case you shorten the pattern so certain notes disappear, they cannot be brought back by increasing the pattern length.
You can, however, bring them back by undoing your chagnes (`Ctrl+Alt+Z`).

- `Expand` button:
Doubles the pattern length, by inserting an empty pattern line on each second line (line 1 - empty line - line 2 - empty line - ...).

- `Shrink` button:
Halves the pattern length, by deleting even second line (line 1 - line 3 - line 5 - line 7...).
This action is desctructive; expanding a shrinked pattern will not bring back notes that were removed.
You can, however, bring them back by undoing your chagnes (`Ctrl+Alt+Z`).

## General editor buttons window

![ui_generalEditor_buttons.png](../img/ui_generalEditor_buttons.png)

- [`Zap` - Zapper](#zapper-window)
- [`Load` - Load module]()
- `Save` - Save module
- [`As...` - Save module as...]()
- [`Disk Op.` - Disk operations window](#disk-operation-window)
- [`Smp. Ed.` - Sample editor](#sample-editor)
- [`Ins. Ed.` - Instrument editor](#instrument-editor)
- [`Adv. Edit` - Advanced editor]()
- [`Transpose` - Note trasposition](#transposition-window)
- [`About` - About MT]()
- [`Optimize` - Module optimization](#optimization-window)
- [`Options` - Playback options]()
- [`Config` - MT configuration]()
- `Play Sng` - Play module
- `Pat` - Play pattern
- `Pos` - Play from cursor position
- `Stop` - Stop playback
- `Rec` - Toggle recording (editing)
- `Add` - Add tracks
- `Sub` - Subtract (Remove) tracks

The options which don't link to a heading do the following:

| Option     | Description |
| -          | - |
| `Save`     | Save the module by owerwriting the module you loaded. If the module is the default empty one that MT loads up with (`Untitled.xm`), this button works the same as [`As...`](). |
| `Play Sng` | Play the module, from the beginning of the current pattern. Same as `Right Ctrl`. |
| `Pat`      | Play the current pattern indefinitely, starting from the beginning. Same as `AltGr` (`Right Alt`). |
| `Pos`      | Play the current pattern indefinitely, starting from the cursor position. Same as `Sh+Enter`. |
| `Stop`     | Stop the playback. Same as `Spc`, when the module is playing. |
| `Rec`      | Toggle the recording mode. Same as `Spc`, when the module is not playing. |
| `Add`      | Adds 2 tracks to the song. Can't add more than the maximum value set in the settings (`I/O > XM channel limit`). |
| `Sub`      | Subtracts 2 tracks from the song. Can't subtract less than 2 tracks, because that makes the number of tracks 0, duh! This action is not desctructive until you save and reload the module. |

# Instrument menu

![](../img/ui_instrumentMenu.png)

Allows selection of the active instrument.
The active instrument is selected by left- or right-clicking on the ID slot or left-clicking the name slot text input field of the instrument.
The user can also change the active instrument by hitting `Sh+UpArrow` (setting the previous instrument as the active one) or `Sh+DownArrow` (setting the next instrument as the active one).
The active instrument is displayed in the [instrument editor](#instrument-editor), as well as being the instrument which is set for inserting notes into the [playlist](#playlist).

- "Instruments" text field:
Hides the active instrument highlight. Useful for making the text in the instrument slot more readable.

- `+`/`-` buttons:
Add or remove one instrument. Non-desctructive action, unless you save the file without the removed instruments.

- `ZAP` button:
Clears the instrument (samples and instrument settings). Destructive action, undoable. Opens a warning popup window.

- `LOAD` button:
Loads an XI instrument from memory.

- `SAVE` button:
Saves an XI instrument to memory.

- Scrollbar:
Used to navigate the instrument slots. Mouse gestures (scroll up/down) do the same thing.

# Sample menu

![](../img/ui_sampleMenu.png)

Allows selection of the active sample of the active instrument.
The active sample is selected by left- or right-clicking on the ID slot or left-clicking the name slot text input field of the sample.
The user can also change the active sample by hitting `Ctrl+Sh+UpArrow` (setting the previous sample as the active one) or `Ctrl+Sh+DownArrow` (setting the next sample as the active one).
The sample in the [sample editor](#sample-editor) is the currently active one.

- `CLEAR` button:
Clears the active sample. Destructive action, undoable. Doesn't open a warning popup window.

- `LOAD` button:
Loads a WAV file from memory into the active sample.

- `SAVE` button:
Saves a WAV file of the active sample to memory.

- Scrollbar:
Used to navigate the sample slots. Mouse gestures (scroll up/down) do the same thing.

# Instrument editor

![](../img/ui_instrumentEditor.png)

Allows editing of the currently selected instrument (via the [instrument menu](#instrument-menu)).
Can be toggled by hitting `Ctrl+I`.

- Envelope viewer:
Displays the volume or panning envelope of the instrument.
Special actions include left-clicking and right-clicking.
<!--TODO-->

- `Volume`/`Panning` tabs:
Used to edit either the volume or panning envelope.

- `0`-`9` and `STORE` buttons:
Used to load of store of the predefined envelopes.
The used can predefine 20 envelopes, 10 for volume and 10 for panning.
The predefined envelopes are loaded by hitting the numerical buttons, and storing is done by hitting the `STORE` button first, after which the user hits the numerical buttons.

- `UNDO`/`REDO` buttons:
Undo or redo the envelope changes.
These include all the envelope editing actions right of the `UNDO`/`REDO` buttons,
that being adding or removing points from the envelope (via the `Add`/`Del` buttons),
toggling the envelope on or off (via the `On` button),
toggling the sustain on or off, or changing which point is the sustain point (via the `Sustain` button and the `+`/`-` buttons under it),
toggling the loop on or off, of chaning the start and end point (via the `Loop` button and the `+`/`-` buttons under it)
and scaling the envelope, that is multiplying it by a given percentage (via the `SCALE X`/`SCALE Y` buttons).

- `COPY`/`PASTE` buttons:
Copy or paste the envelope (indepent of which type of envelope it is) into another envelope.

- `ZOOM IN`/`ZOOM OUT` buttons:
Zoom in or out of the envelope.

- Right-most part of the window:
Used for editing the basic instrument properties, as described in [the doc titled "THE XM FILE FORMAT" in the "Instruments" section](./xm.md#instruments).
There are still certain buttons of interest, described below.

- `Exit` button:
Close the instrument editor window. Same as hitting `Ctrl+I`.

- `Zap` button:
Zap the instrument. Cannot be undone.

- `Load` button:
Load an instrument from memory.

- `Save` button:
Save an instrument into memory.

- `Copy` button:
Copy a sample from one sample slot in one instrument into another sample slot in another instrument.
Overrides the sample in the destination sample slot, if one exists.
Opens an external window, seen below.

![](../img/ui_copySample.png)

- `Swap` button:
Swap a sample from one sample slot in one instrument with another sample slot in another instrument.
Opens an external window, seen below.

![](../img/ui_swapSample.png)

- Keyboard:
Allows either playing the instrument, or setting which key triggers which sample.
Playing the instrument is done by hitting `Play`, after which the keyboard is playable.
Setting which key triggers which sample is done by hitting `Edit`.
`Stop` stops all instrument playback, either from playing the keyboard, which is usually neccessary when the user has set a long fadeout, or playing the actual song.
The graphical look of the keyboard's two modes are seen below.

![](../img/ui_pianoPlay.png)<br>
"Playing" mode.<br>
![](../img/ui_pianoEdit.png)<br>
"Editing" mode.

# Sample editor

![](../img/ui_sampleEditor.png)

Allows editing of the currently selected sample (via the [sample menu](#sample-menu)).
Can be toggled by hitting `Ctrl+S`.

- Sample waveform viewer:
Displays the sample. Largest part of the sample editor.
Special actions include shift-left-clicking, left-clicking, right-clicking and scrolling.
Right-clicking on it open the waveform editing menu, which is covered in more detail in "[3.2. WORKING WITH SAMPLES](./samples.md)".

- "Play:" text field:
Indicates which note will play when using `Wav`, `Rng` and `Dsp`. The note is displayed below the text field.

- `Stop` button:
Stops sample playback.

- `Up`/`Dn` buttons:
Change the note that will play when using `Wav`, `Rng` and `Dsp`.

- `Wav` button:
Plays the entire sample on the note shown in the "Play:" text field.
Accounts for looping.

- `Rng` button:
Plays the selected sample range on the note shown in the "Play:" text field.
Does not account for looping.

- `Dsp` button:
Plays the sample range displayed in the sample viewer on the note shown in the "Play:" text field.
Does not account for looping.

- `Show rng` button:
Set the sample viewer in such a way that it displays the selected range.
There is usually padding around the displayed range.

- `Rng all` button:
Set the range to be the entire sample.

- `Undo`/`Redo` buttons:
Undo or redo the changes done to the sample.
The user can go back 15 steps.

- `Zoom out` button:
Zoom out partially.

- `Show all` button:
Zoom out entirely.

- `Redo filter` button:
Reapply the last change done to the same (generators, EQ, volume change, etc).

- `Cut`/`Copy`/`Paste` buttons:
Work as expected, providing the ability to cut, copy and paste parts of the sample into other sample slots.
Selecting a range in the sample editor, by holding the left mouse button, and pasting results in the selected section of the sample being swapped for the cut/copied section.
Cuting is undoable.

- `Crop` button:
Swaps the current sample for the range you have selected in it.
Undoable.

- `Vol` button:
Opens a popup window which lets you input a number.
Hitting `OK` in the popup window sets the amplitude of the sample to the input number, in percent.
The input number can go over 100, and below 0.
Going below 0 reverses the polarity of the waveform.

- `Draw` button:
Toggles the draw mode on the sample.
When the button is pressed, any left-mouse action overrides the current sample data, placing the waveform point there where the user has pressed.
**You can also toggle drawing by holding** `Sh` **and pressing the same button**.
Undoable.

<!-- TODO: Use a unified language for the mouse actions -->
<!-- TODO: Note that any popup window can be closed with the Esc key -->
<!-- TODO: Note that the text and number input field are focused by double left-clicking and unfocused by hitting the Esc key -->

# Disk operations window

Allows the user to perform reading and writing operations to their hard memory.

It comes in two views, which we'll call the ["list"](#list-view) and ["simple" view](#simple-view).
You can change the active view by hitting `FLIP` in the top-right corner.

## "List" view

![ui_diskOp.png](../img/ui_diskOp.png)

This window allows you to read or load the following information by hitting the `Type` button under the "Disk op" text field:

1. Modules (`Modules`)
2. Instruments (`Instr.`)
3. Samples (`Sample`)
4. Patterns (`Patt.`)
5. Tracks (`Track`)

Once you hit the `Type` button, you must select what you want to write or load.
By default, the type is set to modules.

Under the `Type` button are radio buttons which allow you to select in which format you are saving the file.
For modules, selecting `.wav` will export the module to a lossless WAV audio file.

The buttons right of the "Disk op" text field allow the following actions, from left to right:

1. (`<-`) Moving to the previous directory, up until the first directory that was opened in the disk operations window
2. (`->`) Undoing the move to the previous directory
3. (`UP`) Moving to the parent directory
4. (`ROOT`) Moving to the root directory
5. (`HOME`) Moving to the home directory
6. (`RELOAD`) Refreshing the current directory
7. (`STEP`) Stepping back one directory (similar to #3)
8. (`DEL`) Deleting the selected file (which doesn't have to be of appropriate type)
9. (`MKDIR`) Making a new directory in the current directory
10. Toggling additional options
11. (`<`/`>`) Toggling the saved directories tab
12. (`FLIP`) Toggling the two views of the disk operations window

In the center of the view is a listview which lets you select the file you want to load into the module, or go to a directory.

If the saved directories tab is toggled, there are six additional buttons; five for directory paths and one for storing them.
By hitting any of them, you will load your saved directories.
They are not shared for any type of file (for example, the module type and sample type have different saved directory paths).
You can store a path by hitting `STORE`, and then, once you are in the path you want to save, hitting the button of the slot you want to save the path to.

The `Save` button opens the [HD Recorder window](#hd-recorder-window), and the `Exit` buttons returns you to the [general editor](#general-editor).

## "Simple" view

![ui_diskOpSimple.png](../img/ui_diskOpSimple.png)

Allows quick selection of format and saving to disk.

Hitting the `Save As` button opens a popup window that allows selection the directory to which you will save.

As with the ["List" view](#list-view), the `Exit` buttons returns you to the [general editor](#general-editor).

## HD Recorder window

# Playlist

# Scopes

# Transposition window

# Zapper window

# Options window

# Configuration window

# Optimization window

# Advanced editor

# About window

---

[>>> WORKING WITH SAMPLES](./samples.md)<br>

[>>> TRACKER BASICS](./basics.md)<br>
[>>> THE XM FILE FORMAT](./xm.md)<br>
[>>> CONFIGURING MILKYTRACKER](./config.md)

[>>> BACK TO START](../README.md)

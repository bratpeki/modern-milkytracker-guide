There are plenty of different UI elements in MT.
Here, we'll be covering the interactive ones and how they behave.

# Buttons

![ui_elementButton.png](../img/ui_elementButton.png)
A button from the [general editor buttons window](#general-editor-buttons-window).<br>
![ui_elementButtonPressed.png](../img/ui_elementButtonPressed.png)
Pressed.

The simplest of them all!

Left-clicking activates the action associated with the button.
Right-clicking shows the button as clicked, but doesn't actually "click" it.

# Checkboxes

Toggles a certain behaviour on or off.
When on, there is a check inside the box.

These are commonly found in the [instrument editor](./ui.md#instrument-editor) and settings.

# Listviews

![ui_settings_resolutions](../img/ui_settings_resolutions.png)<br>
A listview of resolutions MT supports.

Allows selection of an element from a list, either by double left-clicking or right-clicking on the
element in the list.

Listviews have a scrollbar, which behavges an audio signal by es similarly to [sliders](#sliders),
except for the fact they are vertical, and their fine tune buttons have the arrow characters,
instead of the `+` and `-`.

The most important listviews in MT are in the
[disk operations window](./ui.md#disk-operations-window) and the
[instrument](./ui.md#instrument-menu) and [sample menus](./ui.md#sample-menu).

# Radio buttons

![ui_settings_scale.png](../img/ui_settings_scale.png)<br>
Radio buttons for the scale multiplier of the MT resolutions.

Select one of the given options.
The selected option will have a point in the circle next to the radio button, while the rest have
empty circles next to them.

You can find radio buttons in the [instrument](./ui.md#instrument-editor) and
[sample editors](./ui.md#sample-editor).

# Scrollbars

![ui_sliderH1](../img/ui_sliderH1.png) Horizonal.<br>
![ui_sliderV](../img/ui_sliderV.png) Vertical.

Allows scrolling.

The arrow characters at the edges of the scrollbar are used for fine-tuned scrolling.

Horizonal scrollbars are seen in the [pattern editor](./ui.md#pattern-editor) and
[sample editor](./ui.md#sample-editor). The vertical ones are seen in the
[instrument](./ui.md#instrument-menu) and [sample menus](./ui.md#sample-menu).

# Sliders

![ui_sliderH](../img/ui_sliderH.png)

Allows setting a value from a fixed interval, by sliding the box within the slider.

The `+` and `-` buttons that are on the edge of the slider allow for a fine tune of the value which
is being set, by increasing and decreasing it, respectfully.

They are commonly seen in the [instrument editor](./ui.md#instrument-editor) (volume, panning, fine
tune, fadeout, etc).

# Text input fields

There are only a few of these fields in MT.
They are:

- [The song title text input field](./ui.md#song-title-length-and-peak-window--common-mt-options-toggle-window)
- [Instrument name text input fields](./ui.md#instrument-menu)
- [Sample name text input fields](./ui.md#sample-menu)

These elements work in the following way:

- Double left-clicking or right-clicking on the field toggles a cursor and allows the user to edit the text in the field
- Hitting `Enter` saves the text into the field
- Hitting `Esc` resets the text to what it was before the editing

# Number input fields

This elements works similarly to the text input fields, with the following exceptions:

- If the user inserts a non-number character before a number character, the value in the field will be set to the default one
- If the user inserts a non-number character after the number and hits `Enter`, everything after the first non-number character is lost

Hitting `Esc` resets the text to what it was before the editing.

One example of this type of field is the sample size field in the sample creation popup window,
visible [here (in the diagram)](./samples.md#new).

# Drop-down menus

![ui_playlistDropDown.png](../img/ui_playlistDropDown.png)

This element features many different functions, all of which are related to each other.

Available features are show in black, the unavailable ones are in white.

A good example is the pattern editor track drop-down menu, featured above.

# Tickboxes

Enables/disables an option.

Enable options have a tick in the box, as expected!

Can be seen in the [configuration window](./ui.md#configuration-window).

# Popup windows

![](../img/ui_options_pan.png)

Any popup window can be closed with the `Esc` key.

A good example of a popup window is the default panning window in the
[Quick options](./ui.md#quick-options-window), featured above.

---

[0. INTRODUCTION](./intro.md)

[1. TRACKER BASICS](./basics.md)

[2. THE XM FILE FORMAT](./xm.md)

[2.1. EFFECT GLOSSARY](./fx.md)

[3. MILKYTRACKER UI REFERENCE](./ui.md)

**3.1. INTERACTIVE UI ELEMENTS**
- [Buttons](#buttons)
- [Checkboxes](#checkboxes)
- [Listviews](#listviews)
- [Radio buttons](radio-buttons)
- [Scrollbars](#scrollbars)
- [Sliders](#sliders)
- [Text input fields](#text-input-fields)
- [Number input fields](#number-input-fields)
- [Drop-down menus](#drop-down-menus)
- [Tickboxes](#tickboxes)
- [Popup windows](#popup-windows)

[3.2. WORKING WITH SAMPLES](./samples.md)

[3.3. WORKING WITH THE PATTERN EDITOR](./playlist.md)

[4. CONFIGURING MILKYTRACKER](./config.md)

[4.1. KEYBIND OPTIONS](./keybind.md)

[5. TIPS AND TRICKS](./tips.md)

[6. GOOD SOURCES](./sources.md)

[7. MAKING AN EXAMPLE SONG IN MILKYTRACKER](./song.md)

[8. THANKS](./thanks.md)

[9. MISSING DOCUMENTATION](./missing.md)

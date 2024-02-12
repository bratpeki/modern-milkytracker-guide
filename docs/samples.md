MilkyTracker has a significantly more powerful sample editor, in comparison to it's predecesor,
FastTracker II. The features available to you in MT include:

- Creating a new sample with a specified sample size
- Waveform generators for:
	- sine waves,
	- square waves,
	- triangle waves,
	- sawtooth waves,
	- noise
	- silence (which clears the sample)
- Volume boosting, fading and normalizing
- Reversing
- Smoothing
- Equalization
- ProTracker boosting
- Resampling

and some less important features.

Here, we'll be looking at how you can use these features to create and manipulate samples.

# Before we begin

When you open the sample editor (using `Ctrl+S` or `Smp. Ed.` from the
[general editor buttons window](./ui.md#general-editor-buttons-window)),
you are greeted with this window:

![ui_sampleEditor.png](../img/ui_sampleEditor.png)

These UI elements, and their basic functionality, are covered [here](./ui.md#sample-editor).

This document, however, serves to showcase the sample manipulation.

With that in mind, let's proceed.

# Sample manipulation

**To begin manipulating a loaded sample, or create a new sample, right click on the sample waveform viewer (the black box which shows the sample).**
This will show a drop-down menu of various functionalities you can use.
Those with an arrow expand to more functionalities.

<!-- TODO: Drop down in elems.md -->

The diagram below serves to highlight all the sample manipulation functionalities:

![sampleEditingDiagram.png](../img/sampleEditingDiagram.png)

I'll name each functionality by its name in the drop-down menu.

## New...

Creates a new sample, with the specified sample size.
I usually use 30 for simple waves and 500-1000 for percussion.

## Undo/Redo

Undoes or redoes a change done to the sample.

<!-- TODO: "Undoable" is not specific enough in ui.md, then -->

## Cut/Copy/Paste/Crop

Self-explanatory.

Cut, Copy and Crop require a range selection to be made.
You can make one by right-mouse dragging along a sample **when not in draw mode**.

## Range all

Range selects the entire sample.

## Advanced

Allows more advanced manipulation of an existing sample.

### Volume boost...

Boosts the volume by a given percent.

If a selection is made, makes the change only on the selection.

### Volume fade...

Fades the volume from the starting value to the given value.

If a selection is made, makes the change only on the selection.

### Normalize

Boosts the volume of the sample as far as possible before any clipping occurs.

If a selection is made, makes the change only on the selection.

### Backwards

Reverses the sample.

If a selection is made, makes the change only on the selection.

### Smooth (rect.)/Smooth (tri.)

Rectangular and triangular smoothing.

Smooths out the sample, making the transients smaller and high ends lower.

If a selection is made, makes the change only on the selection.

<!-- TODO: More info -->

### 3 Band EQ...

Opens a popup winow which prompts the user with a 3-band equalizer.

The frequency the bands are on are visible above the sliders.

If a selection is made, makes the change only on the selection.

### 10 Band EQ...

Opens a popup winow which prompts the user with a 10-band equalizer.

The frequency the bands are on are visible above the sliders.

If a selection is made, makes the change only on the selection.

### Resample...

Allows resampling the sample to a specific number of samples.
Resampling implies changing the sample count, using fine-tune and relative note settings.

This is usually useful for making it so you have about cca. 10000 sample blocks, for efficiently using 9xx.

An example of a track being resampled to be cca. 10000 sample blocks is given below.
The left window shows the original. The right window shows the resampled sample.

<!-- TODO: Move this to tips and tricks -->

![resampleTo10000.png](../img/resampleTo10000.png)

## ProTracker. Boost

Does the ProTracker sample boost.

Effectively, this boosts the volume and high-end.

## Generators

Generates a selected signal sample and places it into the selected sample slot.
Undable using [Undo](#undoredo).

# Tips and tricks

You can hold `Ctrl` when your mouse is inside the sample waveform viewer to view the
`9xx` offset regions! This is pretty useful for chopping vocals and breakbeats.

# Undocumented

So far, I haven't documented:

- Cross-fade
- Change sign
- Swap byte order
- DC normalize
- DC offset...
- Ext. paste

I've never used them, so I doubt you ever will, either, but any help regarding these is appreciated!

---

<!-- TODO: Links -->

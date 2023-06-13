## Tracker basics

Here, we will be covering the basics of **traditional** trackers.

I hightlight the term "traditional" because you will mainly hear that trackers are split into traditional and modern trackers. Modern trackers have some neat features like plugin support, mixers and so on.

Whenever we refer to something as a "tracker" in this guide, it will be a traditional tracker.

# What are trackers?

Trackers are computer programs that enable users to create music via music samples.
They handle manipulation of one of four sample properties:

- Offset
- Panning
- Pitch
- Volume

A tracker allows storing the user-created composition under a binary file called a module.
In MT, you will be met with two module formats: MOD and XM.
Modules are usually of a much smaller file size than the lossless export, making trackers optimal for making small, but good-sounding music.

# Origin of the name

You should know the following trems:

| Term             | Meaning                                                     |
| -                | -                                                           |
| **Track**        | **A single column in the program which holds musical data** |
| Tracking         | The act of placing notes into tracks                        |
| Tracker musician | A musician that makes music using trackers                  |

More often than not, you'll hear the term "tracker" being used to describe a tracker musician.

# The basics of tracker music

Here, we'll be looking at the elements which make up a tracker composition.

## Instruments

An instrument is a system consisting of samples and rules on how to play them back.

Instruments allow you to:

- Choose which note triggers which sample
- Set a volume and panning envelope
- Set fine definition properties

## Cells

Cells are single elements which make up a track.<br>
They usually look like this:

```
| C-4 | .1 | .. | ... |
```

In the case of many trackers, the data is presented in the same order, that being:

1. Note and octave
2. Instrument slot
3. Volume slot
4. Effect slot

The dots are meant to be empty spaces. Some trackers show them, some don't. MT does.

## Tracks

Tracks are columns consisting of a finite number of cells.<br>
For example, here's a track containing a manually created arpeggio:

```
| C-4 | .1 | .. | ... |
| D#4 | .1 | .. | ... |
| F-4 | .1 | .. | ... |
| D#4 | .1 | .. | ... |
| C-4 | .1 | .. | ... |
| D#4 | .1 | .. | ... |
| F-4 | .1 | .. | ... |
| D#4 | .1 | .. | ... |
```

Also, notice that instead of the `-`, there is now a `#` for sharp notes in the first row.<br>
This saves up on screen space.

## Patterns

The next step up after tracks are patterns, collections of multiple tracks.<br>
For example, let's expand on the previous example with a bass in the second track:

```
| TRACK 1             | TRACK 2             |
|-------------------------------------------|
| C-4 | .1 | .. | ... | C-3 | .2 | .. | ... |
| D#4 | .1 | .. | ... | ... | .. | .. | ... |
| F-4 | .1 | .. | ... | ... | .. | .. | ... |
| D#4 | .1 | .. | ... | ... | .. | .. | ... |
| C-4 | .1 | .. | ... | A#2 | .2 | .. | ... |
| D#4 | .1 | .. | ... | ... | .. | .. | ... |
| F-4 | .1 | .. | ... | ... | .. | .. | ... |
| D#4 | .1 | .. | ... | ... | .. | .. | ... |
```

They consist of pattern lines (rows), which are a collection of cells that play at the same time.<br>
In the example above:

```
| TRACK 1             | TRACK 2             |
|-------------------------------------------|
| C-4 | .1 | .. | ... | C-3 | .2 | .. | ... | < This is the first pattern line
| D#4 | .1 | .. | ... | ... | .. | .. | ... | < This is the second pattern line
```

Patterns will play back at different speeds depending on the BPM and pattern speed (labeled `SPD`).
More on SPD in the [TICKS, SPD AND BPM](#ticks-spd-and-bpm) section.

## Songs

A song is a system consisting of mulitple patterns, played one after another in a specific order.

The duration of the song can be either finite or infinite, depending on whether or not you've set pattern looping.

## Ticks, SPD and BPM

Ticks are the smallest unit of time in a tracker.

They are controlled via BPM, the measure for beats per minute, and SPD, the pattern speed.

BPM defines how much time there is between ticks.<br>
SPD defines the number of ticks between two pattern lines.

The general idea is:

- **The greater the BPM, the less time there is between two neighboring ticks.**
- **The greater the SPD, the more ticks there are between two pattern lines.**

It is useful to set a bigger SPD when you need fine-tuned changes to take place, because, for example, with SPD set to 10 you have 10 units of time between two pattern lines to make changes.

---

[>>> INTRODUCTION](./intro.md)<br>
[>>> THE XM FILE FORMAT](./xm.md)

[>>> BACK TO START](../README.md)

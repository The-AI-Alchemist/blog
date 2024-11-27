---
title: "Kaua'i O'o: An original song made in desmos"
date: 2024-11-26T17:47:28-08:00
draft: true
---

I have written an original piece of music in desmos graphing calculator, it's 96 seconds long, and inspired by the song of an extinct bird called "Kaua'i O'o"

What follows is an explanation of the surprisingly arbitrary standards which have confined most western music.

Our music system is centered around a note played at 440Hz, we call this A5(A note, fifth octave).

The following 2 paragraphs are to un-educate people who know music theory, if you don't know music theory, congratulations, you can skip them:

Forget anything you were taught about flats and sharps, they don't exist. We only call them flat and sharp because classical musicians invented "The Major Scale" and decided that some notes weren't cool enough to join it and get named after letters.

So despite it being called and OCTave, and there being 7 notes we're taught of within a single octave(ABCDEFG), there are actually 12 notes in an octave, when you stop being bigoted against flats and sharps.

We will give each note an ID, we will say that A5, being so central, gets to be considered the baseline, 0.

A#5;1,

B5;2

C5;3

C#5;4

And so on, whereby going lower than A5 yields negative numbers. We will now refer to these notes by their IDs, which bear less of the cultural baggage that traditional music notation bears. The most fundamental rule for how the frequencies of these notes scale is that going up by 12 will double the frequency, and going down by 12 with halve the frequency. And as note 0 has a frequency of 440Hz, we can write out the equation:

f(x) = 440 * 2 ^ (x/12)

I would encourage you to take a second to examine this equation.

Other music systems from different cultures of course do define their "note 0" differently, in fact, in the west 435 used to be the more common concert pitch in the west.(concert pitch is the more technical term for what we are calling "note 0"). And slight variations in concert pitch when tuning the instrument are sometimes used for artistic purposes.

Another value assigned arbitrarily is the 12 notes to double, the size of the octave. Different cultures have had 5,6,7, and others as their octave size.

To play the music in the song I wrote, we have 4 lists of notes; 4 channels. We also have a variable "I" representing the index; how far we are into the song. We also have the funciton "U" which increases I by 1, until it reaches the end of the song, where it then loops back to the beginning(because I couldn't think of anything else for it to do when it ended). For each channel, there is a place in the graph where the note at the current index is played, and we have set the ticker at the top of the graph to run the function "U" every quarter second (250ms), playing the song. Lastly, if I wanted a channel to be silent, not play anything, I just told it to play "note sqrt(-1)", and that got him to shut up.

I also rigged up a pretty little visual of the song, which made it easier to edit and more fun to look at.

Here's my graph(be sure to press the unmute button in the top right):

https://www.desmos.com/calculator/nfqfkdfrc2
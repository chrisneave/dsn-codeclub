---
layout: post
title: "Micro:bit - Ghost Catcher"
date: 2019-10-31
categories: microbit
---
This week we will be using the compass built into the Micro\:bit to help us find and catch ghosts. To get started read and follow the instructions below.

## Getting Started

Open a new MakeCode Editor by clicking on this link: [MakeCode Editor](https://makecode.microbit.org/#editor){:target="_blank"}.

First create a new variable and call it "ghost".

![create-a-new-variable](/assets/microbit-ghost-catcher/create-a-new-variable.png)

Next we need to set our ghost variable to a random number between 0 and 359. Let's do this within an "on shake" block:

![on-shake](/assets/microbit-ghost-catcher/on-shake.png)

## Detecting Ghosts

Now let's add some code to detect a ghost. Add the following blocks to your editor:

![detecting-a-ghost](/assets/microbit-ghost-catcher/detecting-a-ghost.png)

Try uploading your code to your Micro:bit and after calibrating the compass, giv the Micro:bit a little shake and then slowly rotate it round in a circle and see if you can detect a ghost. You might have to be patient and move the Micro:bit slowly but eventually you should see an image of a ghost popup on the LEDs.

Each time you give your Micro:bit a shake the ghost will disappear and a new one will show up in a different location.

**Note: Moving around won't help you detect the ghosts - only rotating on the spot will work.**

## Keeping Score

Now we can detect our ghosts we should add some more code that will catch each ghost and keep score of how many we have caught so far. Add the following two blocks, "on start" and "on button B pressed" to your editor:

**Note: You'll need to create the "score" variable in the same way you created the "ghost" variable**

![on-start](/assets/microbit-ghost-catcher/on-start.png)

![catching-a-ghost](/assets/microbit-ghost-catcher/catching-a-ghost.png)

Upload your code to your Micro:bit and this time when you detect a ghost trying pressing the "B" button (the button to the right of the LEDs) and see if you see an X meaning you caught the ghost. Once caught, your new score should be displayed.

Each time you shake your Micro:bit your score should disappear and be ready to detect a new ghost.

See how many ghosts you can detect. Can you beat your friends score?

## Useful Links

- [Finished Project](https://makecode.microbit.org/_Du76gKTRpdvJ){:target="_blank"}

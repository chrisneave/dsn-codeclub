---
layout: post
title: "Micro:bit - Radio Rainbows"
date: 2019-06-06
categories: microbit
---
This week we will be using the LED strip on the top of our robots to create a series of rainbows that move across multiple robots. We will be using the radio on our Microbits to detect when we need to light up our rainbow and also to tell the next Microbit to take a turn. Our Microbits will work together to take turns in lighting up its 5 LEDs on the robot to 5 colours of the rainbow in sequence.

The colours of the Rainbow are:

1. Red
2. Orange
3. Yellow
4. Green
5. Blue
6. Indigo
7. Violet

The first Microbit will display red on its first LED, then orange on the second through to blue on the last.

The second Microbit will start from the next colour, which is indigo then violet. The third LED is used to start a new rainbow by showing red.

Additional Microbits will continue the rainbow sequence using their own robot LEDs.

## Organizing Microbits into a sequence

Decide amongst the group which Microbit and robot will go first in the sequence, which will go second, third, fourth, etc. Once you have done this, work out the five colours you need to display for your part of the sequence.

## Add code to display your rainbow sequence

Open the [MakeCode Editor][editor]{:target="_blank"} and add the Neopixel blocks to the editor by clicking on the ![advanced](/assets/microbit-radio-rainbows/advanced.png) button followed by the ![extensions](/assets/microbit-radio-rainbows/extensions.png) button.

On the screen that appears click on the image for the `neopixel`.

![kitronik-servo-lite](/assets/microbit-radio-rainbows/neopixel.png)

Add the following blocks to your `on start` block so that it looks like this:

![onstart](/assets/microbit-radio-rainbows/onstart.png)

**Pro tip:** It's important that all Microbits use the same radio group so they can communicate with each other, so make sure the `radio set group` block uses a value of `1`.

Now create a new function by selecting `Make a function` from the `Functions` block category. Call your function `showRainbow`.

![make-a-function](/assets/microbit-radio-rainbows/make-a-function.png)

You should see your `showRainbow` function in the code area:

![show-rainbow](/assets/microbit-radio-rainbows/show-rainbow.png)

Next, you will need to add blocks to your `showRainbow` function that lights up each LED in turn with the next colour in your rainbow sequence starting with the first LED. Use a combination of the `set pixel colour at` and `show` blocks to light up each LED.

| ![set-pixel-colour-at](/assets/microbit-radio-rainbows/set-pixel-colour-at.png) | Set the colour of a specific LED. LEDs are numbered 0 to 4. |
| ![show](/assets/microbit-radio-rainbows/show.png) | Must be called after a `set` block to show changes in colour. |

**Pro tip:** You will need to repeat the two blocks above in a sequence for each of the five LEDs you need to light up.

To test your rainbow code add a block to call to your `showRainbow` function to an `on button A pressed` block. A block called `call function` should be available under the `Functions` block category that you can use to achieve this.

![on-button-a-pressed](/assets/microbit-radio-rainbows/on-button-a-pressed.png)

Now when you click on the A button in the Microbit simulator or press the A button on your Microbit after downloading your code the LED strip on your robot should light up with your rainbow sequence.

## Animating the rainbow

To make our rainbow more interesting, add a block to pause for a short while after lighting up each LED. Look in the `Basic` block category to find a block to help with this.

## Joining up all the rainbows

Now we have our rainbow sequence lighting up we need to add code that does two things:

1. Show our rainbow when we receive a number using the radio on our Microbit.
2. Sends a number using the radio so that the next Microbit in the sequence can show its rainbow sequence.

Add an `on radio received` block that calls our `showRainbow` function when a specific value is received. If the `receivedNumer` equals the number of your Microbit in the rainbow sequence, e.g. the first Microbit will listen for `1`, the second Microbit for `2`, and so on, then call your `showRainbow` function. Use these blocks to achieve this:

![on-radio-received](/assets/microbit-radio-rainbows/on-radio-received.png)
![if](/assets/microbit-radio-rainbows/if.png)
![equals](/assets/microbit-radio-rainbows/equals.png)
![received-number](/assets/microbit-radio-rainbows/received-number.png)

*Hint: You want to `call showRainbow` `if receivedNumber = X` where `X` is your number in the rainbow sequence.*

To send a signal to the next Microbit add a `radio send number` block after `call showRainbow` that sends the next number in the sequence. For example, the first Microbit will send the number 2, the second Microbit will send the number 3, and so on.

## Starting the sequence

Finally, we need to add code that starts off the explosion of LED rainbows! To do this add a `radio send number` block to an `on button B pressed` block and use it to send the number `1`. Now with all the Microbits lined up in a row, pressing the `B` button on any of the Microbits other than the first should start the sequence and cascade rainbow colours across all of the microbits.

**Pro tip:** You can't press button B on the first Microbit to start as Microbits are not able to receive their own signals, they can't send signals to themselves.

## Challenges

1. Can you add code that clears the rainbow on all Microbits at the start of a new sequence?
2. Can you add code to the last Microbit in the sequence to start a new rainbow sequence from the beginning, creating an eternal rainbow?

[editor]: https://makecode.microbit.org/#editor

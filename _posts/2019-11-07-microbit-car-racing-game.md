---
layout: post
title: "Micro:bit - Car Racing Game"
date: 2019-11-07
categories: microbit
---
This week we will be making our own car racing game using the Microbit LEDs and buttons to control our cars.

## Getting Started

Start by opening a new Micro:bit editor window in your browser by clicking the following link.

- [MakeCode Editor](https://makecode.microbit.org/#editor){:target="_blank"}

## Initialising the Game

First we need to set the score variable to 0 and then create another two variables to track our player and the state of the game.

Add the blocks below to your editor.

![initialising-the-game](/assets/microbit-car-racing-game/initialising-the-game.png)

To create the `playerCar` and `gameOn` variables you can select `New variable...` from the drop-down box in the `set variable` block.

The dark green blocks can be found in the `Game` block menu.

## Controlling the Main Sprite

Next we will add the blocks below to our editor to move the player left and right when either the A or B button is pressed.

![controlling-the-main-sprite](/assets/microbit-car-racing-game/controlling-the-main-sprite.png)

**Test your code and confirm that you can move the player pixel shown on the bottom row of LEDs from left to right using the A and B buttons.**
## Adding the First Car

Now we will add code to control the cars that the player must avoid. Click on the `Make a Function...` button in the `Functions` menu to create a new function called `controlCar`. Click on the `LedSprite` button to add a parameter and call it `car`.

The `Edit Function` popup should look like this:

![creating-a-new-function](/assets/microbit-car-racing-game/creating-a-new-function.png)

Once you click on `Done` you should see a new function block within your editor. Add the following blocks to this new function block so that it looks like this:

![control-car-function](/assets/microbit-car-racing-game/control-car-function.png)

The `car` variable should be dragged from `car` blob at the top of the function block where ever it is needed inside the function code.

Now create a forever block and add the following blocks. You can find the block representing your `controlCar` function under the `Functions` block menu.

![adding-the-first-car](/assets/microbit-car-racing-game/adding-the-first-car.png)

**Test your code and you should see a single car on the top left of the LED that animates its way to the bottom of the screen. Each time you avoid the car your score will increase. If you collide with the car then the game will end and your score will be displayed.**

## Duplicating the Code for the Other Cars

Now we can duplicate the `forever` block we added in the previous step four times to create another four cars. Each time you duplicate the existing `forever` block you will need to change the `car0` variable to a new variable each time: `car1`, `car2`, `car3`, and `car4`.

![duplicating-the-code-for-the-other-cars](/assets/microbit-car-racing-game/duplicating-the-code-for-the-other-cars.png)

**Now test your code and confirm that each column of the LED contains a falling car which the player must avoid.**

## Challenges

1. Tweak the code to make the cars move faster as the score increases.
2. Change the game into a "Catch the fruit" game where instead of avoiding the falling sprites, the player should try to catch then and score a point each time they do. You could either end the game after a timer has counted down or after a fixed number of fruit have been dropped.

## Useful Links

- [Finished Project](https://makecode.microbit.org/_P4H9RoEEhVkv){:target="_blank"}

*This project was adapted from the [BBC Micro:bit Car Racing Game](https://www.101computing.net/microbit-car-racing-game/){:target="_blank"} project.*

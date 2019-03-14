---
layout: post
title: "Micro:bit - Radio Robots"
date: 2019-03-14
categories: microbit
---
This week we will be using the radio built into the Micro\:bit to control our robot, moving it left, right, forwards and backwards. For this we will need two Micro:bits per team: one to act as the controller and ther other to be the robot.

You will write code for both the controller and the bot. If you are working in a team of two then you can have one person code the controller with one Micro:bit and the other can code up the bot. You don't need to team up but doing so will cut down on coding time and give you more time to experiment with your creation!

## Coding the Controller

Open the [MakeCode Editor][editor]{:target="_blank"} and change the name of the program to `Radio Robots - Bot`.

Remove the `forever` block as we're not going to need it. *If there are other blocks left over from a previous project you can delete those as well.*

Add the following code to the `on start` block to set the radio group to use. Both your controller and robot need to use the same radio group or else the bot will not receive any control commands from the controller.

![on-start](/assets/microbit-radio-robots/on-start.png)

**IMPORTANT: Pick a radio group number between 0 and 255 that is not shared with another team. If not then you will end up controlling someone else's bot and chaos will ensue!**

Now we need add code to figure out when to send commands to the controller and which commands to send. To do this we will use the accelerometer built in to the Micro:bit to sense the angle at which the Micro:bit is being tilted. You can decide how the angle of the Micro:bit should determine the movement of the bot but a sensible approach might be to use:

- Flat (level with the floor) = stop
- Tilt left = left
- Tilt right = right
- Tilt backwards (logo pointing at the top) = backward
- Tilt forwards (logo pointing at the bottom) = forward

To transmit the commands from the controller to the bot we need to encode each one as a number. To do this we will assign a number to each movement direction as follows:

- 0 = stop
- 1 = left
- 2 = right
- 3 = forward
- 4 = backward

With this in mind we now need to add blocks to detect the type of movement. For this we can use the `on` block from the `Input` category to detect when the Micro:bit is tilted.

![input-on-block](/assets/microbit-radio-robots/input-on-block.png)

The `on` block allows us to select an input signal and then execute a number of other code blocks whenever that input signal is raised. Because we are using radio to

Add the following block to your controller to send a `move left` signal when the Micro:bit is tilted to the left.

![tilt-left](/assets/microbit-radio-robots/tilt-left.png)

*Can you work out which blocks need to be added to send the remaining signals?*

Once you have added the remaining movement commands your controller code should look like this.

![controller-finished](/assets/microbit-radio-robots/controller-finished.png)

The JavaScript code will look like this:

```javascript
input.onGesture(Gesture.ScreenUp, function () {
    radio.sendNumber(0)
})
input.onGesture(Gesture.TiltLeft, function () {
    radio.sendNumber(1)
})
input.onGesture(Gesture.TiltRight, function () {
    radio.sendNumber(2)
})
input.onGesture(Gesture.LogoDown, function () {
    radio.sendNumber(3)
})
input.onGesture(Gesture.LogoUp, function () {
    radio.sendNumber(4)
})
radio.setGroup(1)
```

## Coding the Robot

Open the [MakeCode Editor][editor]{:target="_blank"} and change the name of the program to `Radio Robots - Bot`.

Remove the `forever` block as we're not going to need it. *If there are other blocks left over from a previous project you can delete those as well.*

Add the Servo blocks to the editor by clicking on the ![advanced](/assets/microbit-radio-robots/advanced.png) button followed by the ![extensions](/assets/microbit-radio-robots/extensions.png) button.

On the screen that appears click on the image for the `kitronik-servo-lite`.

![kitronik-servo-lite](/assets/microbit-radio-robots/kitronik-servo-lite.png)

You should now be able to see ![servo-lite-category](/assets/microbit-radio-robots/servo-lite-category.png) in the block selection panel.

Add the following code to the `on start` block to set the radio group to use. Both your controller and robot need to use the same radio group or else the bot will not receive any control commands from the controller.

![on-start](/assets/microbit-radio-robots/on-start.png)

**IMPORTANT: Pick a radio group number between 0 and 255 that is not shared with another team. If not then you will end up controlling someone else's bot and chaos will ensue!**

Add an `on radio received` block that will read signals from the controller and instruct the Robot servos to move depending on the value received.

We are going to use the following values to indicate movment in four directions as well as no movement so we are able to stop the Robot:

- 0 = stop
- 1 = left
- 2 = right
- 3 = forward
- 4 = backward

![on-radio-received](/assets/microbit-radio-robots/on-radio-received.png)

Your finished code should now look like this:

![bot-finished](/assets/microbit-radio-robots/bot-finished.png)

The JavaScript code will look like this:

```javascript
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        kitronik_servo_lite.left()
    } else if (receivedNumber == 2) {
        kitronik_servo_lite.right()
    } else if (receivedNumber == 3) {
        kitronik_servo_lite.forward()
    } else if (receivedNumber == 4) {
        kitronik_servo_lite.backward()
    } else {
        kitronik_servo_lite.stop()
    }
})
radio.setGroup(1)
```

Now try out your code by tilting the controller Micro:bit and seeing if the bot responds to each movement.

## Challenges

### Shake to dance

Can you add code to your controller and bot so that when the controller is shaken your bot dances?

### Push to move

Can you use the buttons on the controller to tell the bot how to move?

### Follow the Leader

Can you use the compass on the controller Micro:bit to make the bot face in the same direction (compass heading) as the controller? If you can then as you rotate the controller around 360 degrees the bot should turn to face the same direction.

[editor]: https://makecode.microbit.org/#editor

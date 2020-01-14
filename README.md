 # Make a remote controlled light show

## Introduction @unplugged

In this session you will code the @boardname@ to display one of the coloured lights on the STOP:bit depending on what message is received via the radio receiver.

## Step 1 @fullscreen

1. Add a ``||basic:on start||`` block.
2. Create a variable ``||variable:channel||``
3. Set the ``||variable:channel||`` variable to **1** inside the ``||basic:on start||`` block
4. Display the value of the ``||variable:channel||`` variable
5. Use the ``||radio:radio set group||`` radio set group block to set the radio channel to the ``||variable:channel||`` variable

```blocks
let channel = 1
basic.showNumber(channel)
radio.setGroup(channel)

```

## Step 2 @fullscreen

Add code so that when button ``|B|`` is pressed the channel number is increased by 1 and the new value is displayed and the radio channel is set to the new value

```blocks
input.onButtonPressed(Button.B, function () {
    channel += 1
    basic.showNumber(channel)
    radio.setGroup(channel)
})
```
## Step 3 @fullscreen

Add code so that when button ``|A|`` is pressed the channel number is decreased by 1, the new value is displayed and the radio channel is set to the new value

## Step 4 @fullscreen

Use an ``||radio:on radio received (received string)||`` block to write code that will turn on the red light for 1 second when the message **red** is received via the radio.

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "red") {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.pause(1000)
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```

## Step 5 @fullscreen

Expand the ``||logic:if||`` block by clicking  **+** sign twice so you can add a new test for receiving the message **amber** and turn the amber light on for 1 second.

Expand the ``||logic:if||`` block by clicking  **+** again and add one more test for receiving the message **green** and turn the green light on for 1 second.

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "red") {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.pause(1000)
        pins.digitalWritePin(DigitalPin.P0, 0)
    } else if (receivedString == "amber") {
        pins.digitalWritePin(DigitalPin.P1, 1)
        basic.pause(1000)
        pins.digitalWritePin(DigitalPin.P1, 0)
    } else if (receivedString == "green") {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(1000)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Step 6 @fullscreen

Connect your @boardname@, pair it and then use the ``||Download||`` button to send your code to the @boardname@

Finally make sure you **save** your code.

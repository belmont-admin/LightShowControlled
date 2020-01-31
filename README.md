 # Make a remote controlled light show

## Introduction @unplugged

In this session you will code the @boardname@ to display one of the coloured lights on the STOP:bit depending on what message is received via the radio receiver.

## Step 1 @fullscreen

1. Add a ``||basic:on start||`` block.
2. Create a variable ``||variables:channel||``
3. Inside the ``||basic:on start||`` block set the ``||variables:channel||`` variable to **1** using a ``||variables:set channel to||`` block.
4. Display the value of the ``||variables:channel||`` variable using a ``||basic:show number||`` block.
5. Use the ``||radio:radio set group||`` block to set the radio channel to the ``||variables:channel||`` variable

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

Use an ``||radio:on radio received (received string)||`` block to write code that will turn on the red light when the message **red** is received via the radio.

To use the ``||variables:receivedString||`` variable simply drag and drop it from inside the ``||radio:on radio received (received string)||`` block.

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "red") {
        pins.digitalWritePin(DigitalPin.P0, 1)
    }
})
```

## Step 5 @fullscreen

Expand the ``||logic:if||`` block by clicking  **+** sign twice so you can add a new test for receiving the message **yellow** and turn the yellow light on.

Expand the ``||logic:if||`` block by clicking  **+** again and add one more test for receiving the message **green** and turn the green light on.

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "red") {
        pins.digitalWritePin(DigitalPin.P0, 1)
    } else if (receivedString == "yellow") {
        pins.digitalWritePin(DigitalPin.P1, 1)
    } else if (receivedString == "green") {
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
})
```

## Step 6 @fullscreen

Now add code at the end to wait **250** milliseconds and then turn all the lights off.

### ~hint

#### Check your pause block very carefully
250 is not one of the values in the drop down menu and you will have to type it in.

### ~

```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "red") {
        pins.digitalWritePin(DigitalPin.P0, 1)
    } else if (receivedString == "yellow") {
        pins.digitalWritePin(DigitalPin.P1, 1)
    } else if (receivedString == "green") {
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
    basic.pause(250)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
})

```

## Step 7 @fullscreen

Connect your @boardname@, pair it and then use the ``||Download||`` button to send your code to the @boardname@

Finally make sure you **save** your code.

## Step 8 @fullscreen

When everyone has got code on their @boardname@ we can use all the @boardname@s together to make a light show.

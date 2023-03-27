
# University of Lincoln School of Computer Science Offer Holder Day Activity

That was a mouthful...

## Welcome

Hello and a warm welcome to the School of Computer Science at the University of Lincoln. We're delighted to have you here today! Today will _hopefully_ give you a small taste of what we get up to as a school - whilst also letting you go ham on a cool little device.

In front of you is a Badger 2040 - a programable badge with an E-Ink display (like the ones you see on a Kindle) and powered by the RP2040 Microcontroller - Raspberry Pi's answer to the Arduino. We'll talk about the specifics later. All you need to know is that today we will be writing and pushing some code onto these devices to make a pretty nifty name badge, and yes, you can take it home with you!

## The Task

### Overview

We're going to be using an IDE called Thonny to write and upload our code to the Badger. Devices powered by the RP2040 Microcontroller can utilise a flavour of Python called Micropython. Micropython is great as it leverages the simplicity of Python code, as well as a majority of libraries available under Python, whilst being optimised for use on a microcontroller.

Our end goal is getting our badges to display a name badge for ourselves, which can be customised and hacked further down the line, as and when you decide to give it a fresh new look!

### Step 0: Have you got everything?

For this to work, you'll need the following:

* A Badger 2040

* USB A->C Cable

* 3D Printed Case (incl. top and bottom)

We have some bolts to hold it all together - but because of insurance we can't legally trust you with tools - once you're happy, we'll fasten everything together for you!

Give us a shout if you're missing anything!

### Step 1: Setting up

First, we're going to fire up Thonny - go to the Start Menu and search for Thonny, we've already configured it for you, so you won't need to worry about setting up your Badger as a target! Now you'll need to plug in your Badger - Thonny will detect it and run your code on the Badger, rather than on the machine you're working on.

In most cases, the Badger will already have some basic stuff running, so in most cases, you'd only need to change a text file to change the display - however, in the interest of actually teaching you something, we've flashed them all with blank firmware...

### Step 2: Importing libraries & setting constants

We now need to start actually writing some code otherwise our Badger will sit there, aimlessly, wondering wherever it went wrong - so let's give it something to do! In Thonny, click New File, or press Ctrl+N.

Now we need to import some libraries that helps our code talk to our Badger and its display. Luckily in Python, as I'm sure most of you will know, that's quite easy. These libraries are also part of the Badger firmware itself, so we don't need to worry about downloading them. At the top of the Python script, write these 3 lines:

```py
import time
import badger2040
import badger_os
```

The time library is used to set an internal timer that we use a little later on, and the other 2 libraries allow us to talk to our Badger and control it, without having to deal with all the technical stuff by ourselves.

Now we have to set up some constants. These are basically variables that aren't variable at all - useful for settings that need to be read only. In Python, we don't actually have a way of declaring constants, everything is a variable of some kind, however - when using them for settings, we still call them constants - and we put their names into all upper case.

Using these constants, lets define the settings for our display:

```py
WIDTH  = badger2040.WIDTH
HEIGHT  = badger2040.HEIGHT
IMAGE_WIDTH  =  104
COMPANY_HEIGHT  =  30
DETAILS_HEIGHT  =  20
NAME_HEIGHT  =  HEIGHT  -  COMPANY_HEIGHT  - (DETAILS_HEIGHT  *  2) -  2 
TEXT_WIDTH  =  WIDTH  -  IMAGE_WIDTH  -  1
COMPANY_TEXT_SIZE  =  0.6
DETAILS_TEXT_SIZE  =  0.5
LEFT_PADDING  =  5
NAME_PADDING  =  20
DETAIL_SPACING  =  10
DEFAULT_TEXT  =  """UoL SoCS
Offer Holder
Come here
It's really good
I swear
Honest!"""
```

This sets up the display by getting its height and width in pixels, and then defines how big each section of our badge will be in pixels. We also define some padding. Padding is how many pixels from each side of an area we actually want our content to be displayed on - this stops things pushing right up against our borders.
  
## Glossary

| Acronym/Term | Meaning |

|--|--|

| IDE | Integrated Development Environment - where we write and manage code |

| RP2040 | A Rasberry Pi developed microcontroller with a dual-core 133MHz ARM Cortex M0 CPU

| Microcontroller | A SoC-like device which is more specialised for low power, low-cost use cases.

| SoC | System on a Chip. Houses CPUs, IO and memory all on one chip

| E-Ink Display | A display which uses charged ink particles to produce a display, doesn't require constant refreshing

| Library | Prebuilt Python files that allow you to quickly implement functionality without having to do it yourself

| Firmware | Low-level software that controls what a computer does, loads before any form of Operating System

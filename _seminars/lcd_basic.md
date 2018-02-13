---
title: Basic use of the LCD
layout: default
excerpt_separator: <!--more-->
---

1. toc
{:toc}
<!--{::options parse_block_html="true" /}-->

## Introduction

These exercises introduce you to using the LCD display on the applications
board.  This is a simple black-and-white display of 128 x 32 pixels. The top
left corner of the display is at (0,0) and the bottom right corner of the
display is at (127,31). At the end of these exercises you should be able to

* declare a display variable
* initialise the display
* clear the display screen
* position a text cursor at a specified location on the display
* write text to the display
* draw a line between specified points on the display
* draw an open rectangle of specified dimensions
* draw a filled rectangle of specified dimensions
* draw an open circle of specified dimensions
* draw a filled circle of specified dimensions
* display the status of digital and analogue sensors using text and/or graphics

## LCD basics

1. Obtain a copy of the repository [LCD](https://github.com/davidkendall/LCD) in
your usual way. Open the folder in Atom. Build, download and run the code.
Check that you can see some output on the LCD display. Now open the
file `main.cpp`. Notice the lines

   ```c
   #include <C12832.h>

   // Using Arduino pin notation
   C12832 lcd(D11, D13, D12, D7, D10);
   ```
   {: .code}
This shows you how to include the library header for the display and
how to declare a variable (`lcd`) of the appropriate type (`C12832`) to
access it. `C12832` is a class that provides the methods that we can use to
work with the display. Have a look at the description of the
[methods of the C12832 class]({{site.baseurl}}/c12832.html) to see what methods
are available and how to use them. The rest of these exercises will require
you to study this page carefully. Check your understanding by answering the
following questions.
   1. How would you declare a variable called `display` that you could
   use to interact with the LCD? What are the advantages and disadvantages
   of declaring this as a global variable? If it was declared as a local
   variable, e.g. in `main()`, how would it be possible to write to the
   display from any other function?
   1. Which method is used to clear the screen?
   1. How would you position the next text write operation to occur at the
   top left of the display?
   1. Refer to the [schematic]({{site.baseurl}}/docs/ApplicationShield%20V_1_0_0%20SCH.pdf) for the application board. Based on the pins that are used in the
   constructor for the `lcd` variable in the example in the repository,
   identify what sort of communication bus is used by the microcontroller
   to interact with the LCD display.
   {: .exercise}

1. The `mbed` library provides macros called `MBED_MAJOR_VERSION`,
`MBED_MINOR_VERSION` and `MBED_PATCH_VERSION`. The macros all evaluate
to integers. It's sometimes helpful to look at these values to see what
version of the library has been used to build your program. Write a program
to display a string on the LCD that shows the value of each of these macros,
separated by `.` characters, e.g. 5.7.1

1. Write a program that allows you to work out what is the maximum number of
lines of text that you can display at the same time on the LCD, using the
current font. Write a similar program to work out the maximum number of
characters per line. Experiment to find out what happens if you try to exceed
these limits.

1. Write a program to display the current values of the potentiometers. When
the board is held the right way up to read the LCD, Pot 1 should be on the
left and Pot 2 on the right. Display their values to 2 decimal places, like
this:

   ```
   L: 0.34
   R: 0.68
   ```
   {: .example}
Your program should execute in a loop with a short time delay and should
repeatedly update the display. Experiment with the delay needed to keep
your system responsive. **Note:** You may need to refer to repository
[s3.1](https://github.com/kf5011/s3.1) to remind yourself how to read the
value of the potentiometers.

1. Write some simple programs to become familiar with the graphics
methods, e.g.

   * a program that draws a line from the top left to the bottom right,
   a line from the bottom left to the top right and a maximal open rectangle
   bordering the whole display;
   * a program that draws an open circle of radius 5 whose centre has
   coordinates (70, 12), and a filled circled of radius 3 whose centre
   has the same coordinates;
   * a program that draws an open rectangle, 104 px x 10 px, with
   top left corner at (20,0), and a filled rectangle 100 px x 6 px,
   with top left corner at (22,2).
   {: .exercise}
Experiment with these, and similar, programs until you are confident
that you understand the main graphics methods.

1. Now write a program that uses both text and graphics to show the
status of the potentiometers. You should distinguish between
the potentiometers using L and R, as in the earlier exercise, but instead of
displaying the value of each
potentiometer in a text field, show its value using a
combination of an open and filled rectangle. The proportions of the
open and filled parts should be determined by the potentiometer value,
e.g. if the value of the potentiometer is 0.75, then the rectangle
should be 75% filled and 25% unfilled.

<!--1. Write a program that draws a filled circle of radius 4 and allows the-->
<!--user to move the circle around the display using the joystick. Sound the-->
<!--speaker if the circle touches the edge of the display and turn the speaker-->
<!--off when the circle moves away from the edge.-->


..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-8-
   :start: 1

A Few More turtle Methods and Observations
------------------------------------------

Here are a few more things that you might find useful as you write programs that use turtles.

* Turtle methods can use negative angles or distances.  So ``tess.forward(-100)``
  will move tess backwards, and ``tess.left(-30)`` turns her to the right.
  Additionally, because there are 360 degrees in a circle, turning 30 to the
  left will leave you facing in the same direction as turning 330 to the right!
  (The on-screen animation will differ, though --- you will be able to tell if
  tess is turning clockwise or counter-clockwise!)

  This suggests that we don't need both a left and a right turn method --- we
  could be minimalists, and just have one method.  There is also a *backward*
  method.  (If you are very nerdy, you might enjoy saying
  ``alex.backward(-100)`` to move alex forward!)

  Part of *thinking like a scientist* is to understand more of the structure
  and rich relationships in your field.  So reviewing a few basic facts about
  geometry and number lines like we've done here is a good start if we're
  going to play with turtles.

* A turtle's pen can be picked up or put down.  This allows us to move a turtle
  to a different place without drawing a line.   The methods are ``up`` and ``down``.  Note that the methods ``penup`` and ``pendown`` do the
  same thing.

  .. sourcecode:: python

     alex.up()
     alex.forward(100)     # this moves alex, but no line is drawn
     alex.down()

* Every turtle can have its own shape.  The ones available "out of the box"
  are ``arrow``, ``blank``, ``circle``, ``classic``, ``square``, ``triangle``,
  ``turtle``. Here's how we could change the turtle's shape to a turtle::

     alex.shape("turtle")


* You can speed up or slow down the turtle's animation speed. (Animation
  controls how quickly the turtle turns and moves forward.)  Speed settings can
  be set between 1 (slowest) to 10 (fastest).  But if you set the speed to 0,
  it has a special meaning --- turn off animation and go as fast as possible.

  .. sourcecode:: python

     alex.speed(10)

* A turtle can "stamp" its footprint onto the canvas, and this will remain
  after the turtle has moved somewhere else.  Stamping works even when the pen
  is up.

Let's do an example that shows off some of these new features.

.. activecode:: ch03_7
   :nocodelens:

   import turtle
   wn = turtle.Screen()
   wn.bgcolor("lightgreen")
   tess = turtle.Turtle()
   tess.color("blue")
   tess.shape("turtle")

   tess.up()                     # this is new
   tess.stamp()                  # leave an impression
   tess.forward(20)
   tess.stamp()                  # leave an impression
   tess.forward(20)
   tess.stamp()                  # leave an impression
   tess.forward(20)

One more thing to be careful about.  All except one of the shapes you see on the screen here are
footprints created by ``stamp``.  But the program still only has *one* turtle
instance --- can you figure out which one is the real tess?  (Hint: if you're
not sure, write a new line of code just before the exitonclick line to change tess'
color, or to put her pen down and draw a line, or to change her shape, etc.)


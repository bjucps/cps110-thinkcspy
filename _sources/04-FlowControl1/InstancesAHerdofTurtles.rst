..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: turtle-2-
   :start: 1

.. index:: instance


Instances --- A Herd of Turtles
-------------------------------

Just like we can have many different integers in a program, we can have many
turtles.  Each of them is an independent object and we call each one an **instance** of 
the Turtle class. Each instance has its own state, so alex might draw with a thin black pen and be at
some position, while tess might be going in her own direction with a fat pink
pen.  

Here is a program that creates two Turtle instances: one named ``tess``, and another named
``alex``. Watch alex draw a square and tess draw a triangle:

.. activecode:: ch03_3
   :nocodelens:
   
   from turtle import Screen, Turtle
   wn = Screen()             # Set up the window and its attributes
   wn.bgcolor("lightgreen")

   tess = Turtle()           # create tess and set some attributes
   tess.color("hotpink")
   tess.pensize(5)

   alex = Turtle()           # create alex

   tess.forward(80)                 # Let tess draw an equilateral triangle
   tess.left(120)
   tess.forward(80)
   tess.left(120)
   tess.forward(80)
   tess.left(120)                   # complete the triangle

   tess.right(180)                  # turn tess around
   tess.forward(80)                 # move her away from the origin

   alex.forward(50)                 # make alex draw a square
   alex.left(90)
   alex.forward(50)
   alex.left(90)
   alex.forward(50)
   alex.left(90)
   alex.forward(50)
   alex.left(90)

   wn.exitonclick()

This program is interesting because it involves interacting with two instances of the same
class. Look at the following two lines, and think about the difference between them::

   tess.forward(80)
   alex.forward(50)

Both of these statements invoke the same method (``forward``). The argument that specifies the distance is different,
but the really big difference involves the object before the dot. The first statement affects ``tess``'s state, and the
second affects ``alex``'s state. Try changing the commands in lines 24-26 by replacing
``alex`` on those lines with ``tess and watch what happens.

Now, here are some *How to think like a computer scientist* questions and observations
to consider. Before you read on, click the turtle drawing to make it disappear.

* Question 1: What direction does alex end up facing at the end of the program? 
* Question 2: The last method invocation on alex causes him to turn left. Did that
  have any effect on the final drawing? If not, why do you think that statement was included?

Now, here are some observations:

* There are 360 degrees in a full circle.  If you add up all the turns that a
  turtle makes, *no matter what steps occurred between the turns*, you can
  easily figure out if they add up to some multiple of 360.  This should
  convince you that alex is facing in exactly the same direction as he was when
  he was first created. (Geometry conventions have 0 degrees facing East and
  that is the case here too!)
* We could have left out the last turn for alex, but that would not have been
  as satisfying.  If you're asked to draw a closed shape like a square or a
  rectangle, it is a good idea to complete all the turns and to leave the
  turtle back where it started, facing the same direction as it started in.
  This makes reasoning about the program and composing chunks of code into
  bigger programs easier for us humans!
* We did the same with tess: she drew her triangle and turned through a full
  360 degress.  Then we turned her around and moved her aside.  Even the blank
  line 17 is a hint about how the programmer's *mental chunking* is working: in
  big terms, tess' movements were chunked as "draw the triangle"  (lines 11-16)
  and then "move away from the origin" (lines 18 and 19).
* One of the key uses for comments and blank lines is to record your mental chunking 
  and big ideas, to help other programmers comprehend the program.
* And, uh-huh, two turtles may not be enough for a herd, but you get the idea!


**Check your understanding**

.. mchoice:: test_question3_2_1
   :practice: T
   :answer_a: True
   :answer_b: False
   :correct: b
   :feedback_a: You can create and use as many turtles as you like.  As long as they have different names, you can operate them independently, and make them move in any order you like.  To convince yourself this is true, try interleaving the instructions for alex and tess in ActiveCode box 3.
   :feedback_b: You can create and use as many turtles as you like.  As long as they have different names, you can operate them independently, and make them move in any order you like.  If you are not totally convinced, try interleaving the instructions for alex and tess in ActiveCode box 3.

   True or False: You can only have one active turtle at a time.  If you create a second one, you will no longer be able to access or use the first.

**Mixed up programs**

.. parsonsprob:: 3_6

   The following program has one turtle, "jamal", draw a capital L in blue and then another, "tina", draw a line to the west in orange as shown to the left, <img src="../_static/TwoTurtles1.png" width="150" align="left" hspace="10" vspace="5" />.  The program should do all set-up, have "jamal" draw the L, and then have "tina" draw the line.   Finally, it should set the window to close when the user clicks in it.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p>
   -----
   import turtle
   wn = turtle.Screen()
   =====    	
   jamal = turtle.Turtle()
   jamal.pensize(10)
   jamal.color("blue")               	               
   jamal.right(90)
   jamal.forward(150)
   ===== 
   jamal.left(90)
   jamal.forward(75)
   =====
   tina = turtle.Turtle()
   tina.pensize(10)
   tina.color("orange")
   tina.left(180)
   tina.forward(75)
   =====
   wn.exitonclick()

.. parsonsprob:: 3_7

   The following program has one turtle, "jamal", draw a line to the north in blue and then another, "tina", draw a line to the east in orange as shown to the left, <img src="../_static/TwoTurtlesL.png" width="150" align="left" hspace="10" vspace="5" />.  The program should import the turtle module, get the window to draw on, create the turtle "jamal", have it draw a line to the north, then create the turtle "tina", and have it draw a line to the east.  Finally, it should set the window to close when the user clicks in it.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p> 
   -----
   import turtle
   =====
   wn = turtle.Screen()
   =====   	
   jamal = turtle.Turtle()
   jamal.color("blue") 
   jamal.pensize(10)   
   =====            	               
   jamal.left(90)
   jamal.forward(150)
   =====
   tina = turtle.Turtle()
   tina.pensize(10)  
   tina.color("orange")
   tina.forward(150)
   =====
   wn.exitonclick()


.. index:: for loop


..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: flowcontrol-for
   :start: 1

Repetition with a For Loop
--------------------------

Some of the programs we've seen so far are a bit tedious to type. If we want to make a 
repetitive pattern in our drawings, then it can take many lines of code. Thankfully, Python 
has a few ways for making this kind of task easier. In this section, I'll give you a sneak preview of a helpful technique
called a ``for`` loop that reduces the amount of repetitive coding. We'll go into more depth on the ``for`` loop
in the next chapter.

A for loop allows Python to repeat a section of your program several times. Take a look at this example:

.. activecode:: acrepwithloop

   print("This will execute first")

   for _ in range(3):
       print("This line will execute three times")
       print("This line will also execute three times")

   print("Now we are outside of the for loop!")

Run the program and observe its output. Then, click the **Show in CodeLens**
button and step through the execution to see how it works.

There are a few things to notice. 

1. Lines 3-5 form what is called a ``for`` loop. A **loop** is a section of lines in a program that execute
   repeatedly. 

2. Lines 4-5 make up the body of the for loop. The loop ``body`` is the statements inside the loop that are executed
   repeatedly. The two print statements are executed three times because of the number 3 in the ``range``
   function on line 3. Try changing the number in the range function in line 3 to ``5`` and see how that changes the
   behavior of the program.

The indentation is important. All of the statements that were printed out multiple times were indented under the for
loop. The statements following the loop are not indented, and execute after the loop completes. 

Now it's time to combine this with the Turtle module. We can do a lot of cool stuff if we combine these two things!
Below is code to do just that. Try to predict what the program will do before running it. After you run it, play with
it a bit. Can you adjust it to make the Turtle draw a square?

.. activecode:: acrepwithloop2

   import turtle   
   elan = turtle.Turtle()

   distance = 50
   for _ in range(10):
       elan.forward(distance)
       elan.right(90)
       distance = distance + 10
 

**Mixed up program**

.. parsonsprob:: 3_10

   The following program uses the stamp method to create a circle of turtle shapes as shown to the left, <img src="../_static/TurtleCircle.png" width="150" align="left" hspace="10" vspace="5"/> but the lines are mixed up.  The program should do all necessary set-up, create the turtle, set the shape to "turtle", and pick up the pen.  Then the turtle should repeat the following ten times: go forward 50 pixels, leave a copy of the turtle at the current position, reverse for 50 pixels, and then turn right 36 degrees.  After the loop, set the window to close when the user clicks in it.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order with the correct indention.  Click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order or are incorrectly indented.</p>  
   -----
   import turtle
   wn = turtle.Screen()
   jose = turtle.Turtle()
   jose.shape("turtle")
   jose.penup()
   =====                   
   for size in range(10):  
   =====    
     jose.forward(50)
   =====
     jose.stamp()    
   =====      
     jose.forward(-50)
   =====
     jose.right(36)             
   =====
   wn.exitonclick()

**Mixed up program**

.. parsonsprob:: 3_11

   The following program uses the stamp method to create a line of turtle shapes as shown to the left, <img src="../_static/Turtle3Stamp.png" width="150" align="left" hspace="10" vspace="5" /> but the lines are mixed up.  The program should do all necessary set-up, create the turtle, set the shape to "turtle", and pick up the pen.  Then the turtle should repeat the following three times: go forward 50 pixels and leave a copy of the turtle at the current position.  After the loop, set the window to close when the user clicks in it.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order with the correct indention.  Click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order or are incorrectly indented.</p>
   -----
   import turtle
   wn = turtle.Screen()
   =====
   nikea = turtle.Turtle()
   =====
   nikea.shape("turtle")
   =====
   nikea.penup()
   =====                   
   for size in range(3):  
   =====    
     nikea.forward(50)
   =====
     nikea.stamp()   
   =====                 
   wn.exitonclick()



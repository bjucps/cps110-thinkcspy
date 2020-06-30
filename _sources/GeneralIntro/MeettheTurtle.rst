
.. qnum::
   :prefix: intro-14-
   :start: 1

Meet the Turtle
---------------

.. video: "Meet the Turtle" - Demonstrate the Python turtle using the interpreter

.. youtube:: tNGQgq1R7RA
    :divid: vid_turtleintro
    :height: 315
    :width: 560
    :align: left

The programs you've seen so far haven't been very exciting. As we wrap up this chapter,
let's have some fun with the Python turtle. 

The Python turtle is a collection of drawing commands built into the Python library.
Imagine that you are a small turtle who carries a pen. As you move, the pen leaves a trail
behind you on the floor. You obey commands like ``forward`` (which makes you move forward,
drawing as you go), and ``left`` and ``right``, which cause you to rotate left or rotate right
without moving or drawing. That is the metaphor that the Python designers had in mind when
they created the turtle drawing commands.

Here's a sample program that uses the turtle drawing commands to command the virtual turtle to draw a rectangle:

.. activecode:: intro-turtle
    :nocodelens:

    import turtle               # allows us to use the Python turtle
    turtle.forward(150)         # tell turtle to move forward by 150 units
    turtle.left(90)             # rotate left 90 degrees
    turtle.forward(75)          
    turtle.left(90)             
    turtle.forward(150)         
    turtle.left(90)             
    turtle.forward(75)          
    print("All done!")

Here's a brief explanation of the program:

1. On Line 1, the ``import turtle`` command allows us to begin using the
   Python turtle. Without this line, we wouldn't be able to draw with the turtle.

2. Line 2 causes the turtle to move forward by 150 units.

3. Line 3 causes the turtle to rotate left in place 90 degrees.

4. Lines 4-8 cause the turtle to finish drawing a rectangle.

5. Line 9 displays an "All done!" message on the screen when the turtle finishes.

Experiment with changing some of the numbers in the commands to see how that
affects the resulting drawing. Then, try changing the order of the statements in the
program, or using the command ``right`` instead of the command ``left``.

Can you modify the program to make the turtle draw a triangle? Have fun!


**Check your understanding**

.. mchoice:: test_question3_1_0
   :practice: T
   :answer_a: North
   :answer_b: South
   :answer_c: East 
   :answer_d: West
   :correct: c
   :feedback_a: Some turtle systems start with the turtle facing north, but not this one.
   :feedback_b: No, look at the first example with a turtle.  Which direction does the turtle move?
   :feedback_c: Yes, the turtle starts out facing east.
   :feedback_d: No, look at the first example with a turtle.  Which direction does the turtle move?

   Which direction does the Turtle face when it is created?

**Mixed up programs**

.. parsonsprob:: 3_1

   The following program uses a turtle to draw a capital L as shown in the picture to the left of this text, <img src="../_static/TurtleL4.png" width="150" align="left" hspace="10" vspace="5" /> but the lines are mixed up.  Remember that the turtle starts off facing east when it is created.  The turtle should turn to face south and draw a line that is 150 pixels long and then turn to face east and draw a line that is 75 pixels long.  We have added a compass to the picture to indicate the directions north, south, west, and east.  <br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p>
   -----
   import turtle
   =====
   turtle.right(90)
   turtle.forward(150)
   =====
   turtle.left(90)
   turtle.forward(75)

.. parsonsprob:: 3_2

   The following program uses a turtle to draw a checkmark as shown to the left, <img src="../_static/TurtleCheckmark4.png" width="150" align="left" hspace="10" vspace="5" /> but the lines are mixed up.  The turtle should turn to face southeast, draw a line that is 75 pixels long, then turn to face northeast, and draw a line that is 150 pixels long.  We have added a compass to the picture to indicate the directions north, south, west, and east.  Northeast is between north and east. Southeast is between south and east. <br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p>
   -----
   import turtle
   =====
   turtle.right(45)
   turtle.forward(75)
   =====
   turtle.left(90)
   turtle.forward(150)

.. parsonsprob:: 3_3

   The following program uses a turtle to draw a single line to the west as shown to the left, <img src="../_static/TurtleLineToWest.png" width="150" align="left" hspace="10" vspace="5" /> but the program lines are mixed up.  The turtle should turn to face west and draw a line that is 75 pixels long.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p>   
   -----
   import turtle
   turtle.left(180)
   turtle.forward(75)

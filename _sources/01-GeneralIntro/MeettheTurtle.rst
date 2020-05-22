
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
Imagine that you are a critter carrying a pen, and that as you move, you leave a trail
behind you on the floor. You obey commands like ``forward`` (which makes you move forward,
drawing as you go), and ``left`` and ``right``, which cause you to rotate left or rotate right
without moving or drawing.

Here's a sample program that uses the drawing commands to make the turtle draw a rectangle:

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

2. Line 2 causes the turtle to move forward by 150 unites.

3. Line 3 causes the turtle to rotate left in place 90 degrees.

4. Lines 4-8 cause the turtle to finish drawing a rectangle.

5. Line 9 displays an "All done!" message on the screen when the turtle finishes.

Experiment with changing some of the numbers in the commands to see how that
affects the resulting drawing. Then, try changing the order of the statements in the
program, or using the command ``right`` instead of the command ``left``.

Can you modify the program to make the turtle draw a triangle? Have fun!


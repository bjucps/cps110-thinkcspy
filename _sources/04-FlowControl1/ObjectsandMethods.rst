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

.. index:: object, invoke, method, attribute, state, canvas

Objects and Methods
-------------------

The following program draws two sides of a rectangle using the Python
turtle graphics library.

.. activecode:: ch03_1
    :nocodelens:

    from turtle import Turtle # allows us to use the Turtle class
    alex = Turtle()           # create a Turtle named alex

    alex.forward(150)        	# tell alex to move forward by 150 units
    alex.left(90)           	# turn by 90 degrees
    alex.forward(75)         	# complete the second side of a rectangle

Here's a brief explanation of what this program does. Lines 1 and 2 create a turtle object named ``alex``, and the
remainder of the program causes alex to draw two lines. 

Let's expand a little on that brief summary:

1. The statement on line 1 allows the program to use Turtle objects. It tells Python that this program
   needs to use the ``Turtle`` class located in the ``turtle`` module (the next chapter has more details on modules and the
   import statement).

2. Line 2 creates an object named ``alex`` that is a member of the class ``Turtle``.
   These first two lines set us up so that we are ready to do some drawing.

3. In lines 4-6, we instruct the object ``alex`` to move and to turn. We do this by **invoking** (or "activating")
   alex's **methods** --- these are the commands that all turtles know how to respond to.
   
I've used some terms and concepts in the descriptions above that need more explanation. We'll get to that
in just a moment. 

.. note::

   This program is a little more involved than the one we introduced back in chapter 1. It creates a named turtle object instead of
   using the default turtle object that we used in that earlier example. We're creating a named turtle object here to introduce
   the concepts of objects and methods.

.. admonition:: Complete the rectangle ...

    Modify the program above by adding the commands necessary to have *alex* complete the
    rectangle.

Understanding Classes and Methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Recall that Python programs manipulate values called **objects**. So far, we've focused on objects like numbers and
strings, and we've manipulated those values primarily using expressions involving operators like ``+`` and ``*``, as
well as using functions like ``len`` and ``round``. However, in this program, we're manipulating the turtle object using
a different approach: method invocations.

A method is a command that an object understands and can perform. For example, turtles understand commands like ``forward`` and
``left``. You command an object to perform some work by writing a **method invocation** statement (also known as
a **method call** statement), like this::

   alex.forward(150)

The general form of a method invocation is this::

   OBJECT-NAME.METHOD-NAME(ARGUMENTS)

where ``OBJECT-NAME`` is the name of the object (or, more precisely, the name of the variable that references the
object, such as ``alex``), ``METHOD-NAME`` is the name of a method you wish the object to carry out (ex. ``forward``),
and ARGUMENTS in parenthesis supply the information the method needs in order to carry out the requested work.

.. note::

   Although we're focused on Turtle objects in this chapter, string objects can be manipulated
   using methods, also. For example, you can convert a string to lowercase using a method invocation like this:

      s = "HELLO"
      s = s.lower()

   You'll learn more about string methods in the chapter on strings.

In the example below, we show a few additional capabilities of turtle objects, and also introduce a new type of
object called a Screen. 

.. activecode:: ch03_2
    :nocodelens:
    
    from turtle import Screen, Turtle

    win = Screen()            # create a Screen named win
    tess = Turtle()           # create a Turtle named tess

    win.bgcolor("lightgreen")        # set the canvas background color

    tess.color("blue")               # make tess blue
    tess.pensize(3)                  # set the width of her pen

    tess.forward(50)
    tess.left(120)
    tess.forward(50)

    win.exitonclick()                # close the canvas when user clicks on it

When you run this program, you can click on the drawing after the turtle is finished drawing,
and the turtle's canvas will disappear. 

This program uses two objects: a Screen object named ``win``, and a Turtle object named ``tess``. Note lines 3 and 4, which 
create the objects.

.. note::

   In case you were wondering, a Screen object represents the drawing surface, or canvas, that the Turtle draws on. We
   didn't create one in the first program because if you don't create a Screen object in your program, Python creates
   one for you behind the scenes. But if you want to set the background color of the canvas, or allow the user to close
   the canvas by clicking on it, you must create one in order to have these capabilities.

Take a closer look at these two lines::

   win = Screen()
   tess = Turtle()

Let's dig into what these two lines mean. Recall that all values in Python belong to some data type, or class. For example, ``56`` belongs
to the ``int`` class, and ``"Hello"`` belongs to the ``str`` class. So far, we've created integer and string variables using lines
like this::

   i = 56
   s = "Hello"

But we can also create integer and string variables using a different notation::

   i = int()   # Creates an int with value 0
   s = str()   # Creates an empty string

Now, this is not the usual way to create integer and string variables, and I don't encourage you to use this form. I am
demonstrating this notation to introduce the idea that, in general, you create objects in Python using an assignment
statement that has this form::

   VARIABLE = CLASS()

where VARIABLE is the variable name you wish to use to refer to the new object, and CLASS is the name of the class of
the object that you wish to create. Note the parentheses, which are required.

In this program, instead of working with integer and string objects, we're working with Turtle and Screen objects. As we discussed
above, you don't manipulate Turtle and Screen objects using operators like ``+``, but rather through commanding them to
perform actions by invoking their methods. Now, here comes a very important concept: slow down and read this carefully:

.. admonition::

   **The methods that you can invoke on a particular object are determined by the object's class.**

Classes define methods. A class defines the methods that you can invoke on objects belonging to the class. The Turtle
class defines methods named ``forward``, ``left``, ``pensize``, and ``color``, among others, so you can invoke those
methods on ``tess``, which is a member of the Turtle class. The Screen class defines methods named ``bgcolor`` (which
sets the background color) and ``exitonclick`` (which waits for the user to click on the canvas, then causes the canvas
to disappear), so you can invoke those methods on ``win``, a member of the Screen class. 

It is illegal to invoke a method on an object that is not defined by the object's class. If we ask tess to
``exitonclick``, we'll get an error, because tess, a member of the Turtle class, doesn't contain a method of that name.

.. admonition:: Extend this program ...

    #. Modify this program so that before it creates the Screen, it prompts
       the user to enter the desired background color. It should store the
       user's response in a variable, and set the color of the canvas
       to the value entered by the user.
       (Hint: you can find a list of permitted color names at
       https://www.w3schools.com/colors/colors_names.asp.  It includes some quite
       unusual ones, like "PeachPuff"  and "HotPink".)
    #. Do similar changes to allow the user, at runtime, to set tess's color.
    #. Do the same for the width of tess's pen.  *Hint:* your dialog with the
       user will return a string, but tess' ``pensize`` method
       expects its argument to be an ``int``.  That means you need to convert
       the string to an int before you pass it to ``pensize``.

Attributes
^^^^^^^^^^

In addition to methods, objects also have attributes (sometimes called *properties*). An **attribute** is a value
associated with the object. The attributes of an object, like its methods, are determined by its class. For example,
Turtle objects have a *color* attribute that controls the color of the line that the turtle draws when it moves. Typically,
you manipulate the values of an object's attributes using methods. For example, the method invocation
``alex.color("red")`` changes the value of alex's color attribute to red. Turtles have additional attributes such as the
width of its pen(tail), the position of the turtle within the window, which way it is facing, the state of its pen (up
or down), and so on.

Like Turtle objects, Screen objects also have attributes. The method invocation ``win.bgcolor("lightgreen")`` changes the
value of win's background color attribute to lightgreen. 

The values of an object's attributes make up its current **state**. State refers to the combined values of the object's
attributes. For example, at a given moment in time, a turtle has a particular position within the window, is facing a
certain direction, and so on. If you make the turtle move forward, its overall state changes, because the value of its
position attribute has changed.


**Check your understanding**


.. mchoice:: test_question3_1_3
   :practice: T
   :answer_a: True
   :answer_b: False
   :correct: a
   :feedback_a: In this chapter you saw one named alex and one named tess, but any legal variable name is allowed.
   :feedback_b: A variable, including one referring to a Turtle object, can have whatever name you choose as long as it follows the naming conventions from Chapter 2.

   True or False: A Turtle object can have any name that follows the variable naming rules from Chapter 2.

.. mchoice:: test_question3_1_5
   :practice: T
   :answer_a: c = Color
   :answer_b: c = Color()
   :answer_c: c = new Color()
   :correct: b
   :feedback_a: Incorrect; parentheses are required.
   :feedback_b: Correct! You would manipulate the new object via its name ``c``.
   :feedback_c: Incorrect; the word new is used in some languages, but not Python.

   Suppose there were a class in Python named Color, and you wanted to create an object of that class. How would you do it?

.. mchoice:: test_question3_1_6
   :practice: T
   :answer_a: a.forward(5)
   :answer_b: print(len(b))
   :answer_c: c.pensize(5)
   :answer_d: d.bgcolor()
   :correct: b,c
   :feedback_a: Incorrect. Objects of the ``int`` class do not have a forward method.
   :feedback_b: Correct. The ``len`` function can operate on ``str`` data.
   :feedback_c: Correct. Objects of the Turtle class have a pensize method.
   :feedback_d: Incorrect. Objects of the Screen class have a bgcolor method, but the method requires an argument to specify the color.

   Given the following definitions, which of these statements are **legal**?

   ::

      a = 5
      b = "Hello"
      c = Turtle()
      d = Screen()

.. mchoice:: test_question3_1_4
   :practice: T
   :answer_a: <img src="../_static/test1Alt1.png" alt="right turn of 90 degrees before drawing, draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :answer_b: <img src="../_static/test1Alt2.png" alt="left turn of 180 degrees before drawing,  draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :answer_c: <img src="../_static/test1Alt3.png" alt="left turn of 270 degrees before drawing,  draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :answer_d: <img src="../_static/test1Alt4v2.png" alt="right turn of 270 degrees before drawing, draw a line 150 pixels long, turn right 90, and draw a line 75 pixels long">
   :answer_e: <img src="../_static/test1correct.png" alt="left turn of 90 degrees before drawing,  draw a line 150 pixels long, turn left 90, and draw a line 75 pixels long">
   :correct: e
   :feedback_a: This code would turn the turtle to the south before drawing
   :feedback_b: This code would turn the turtle to the west before drawing
   :feedback_c: This code would turn the turtle to the south before drawing
   :feedback_d: This code is almost correct, but the short end would be facing east instead of west.  
   :feedback_e: Yes, the turtle starts facing east, so to turn it north you can turn left 90 or right 270 degrees.

   Which of the following code would produce the following image? 

   .. image:: ../_static/turtleTest1.png 
      :alt: long line to north with shorter line to west on top

**Mixed up programs**

.. parsonsprob:: 3_4

   The following program uses a turtle to draw a capital L in white on a blue background as shown to the left, <img src="../_static/BlueTurtleL.png" width="150" align="left" hspace="10" vspace="5" /> but the lines are mixed up.  The program should do all necessary set-up and create the turtle and set the pen size to 10.  The turtle should then turn to face south, draw a line that is 150 pixels long, turn to face east, and draw a line that is 75 pixels long.   Finally, set the window to close when the user clicks in it.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p>
   -----
   import turtle
   wn = turtle.Screen()
   =====
   wn.bgcolor("blue")     	
   jamal = turtle.Turtle()
   =====
   jamal.color("white")               	
   jamal.pensize(10) 
   =====                
   jamal.right(90)
   jamal.forward(150)
   ===== 
   jamal.left(90)
   jamal.forward(75)
   wn.exitonclick()

.. parsonsprob:: 3_5

   The following program uses a turtle to draw a capital T in white on a green background as shown to the left, <img src="../_static/TurtleT.png" width="150" align="left" hspace="10" vspace="5"/> but the lines are mixed up.  The program should do all necessary set-up, create the turtle, and set the pen size to 10.  After that the turtle should turn to face north, draw a line that is 150 pixels long, turn to face west, and draw a line that is 50 pixels long.  Next, the turtle should turn 180 degrees and draw a line that is 100 pixels long.  Finally, set the window to close when the user clicks in it.<br /><br /><p>Drag the blocks of statements from the left column to the right column and put them in the right order.  Then click on <i>Check Me</i> to see if you are right. You will be told if any of the lines are in the wrong order.</p>  
   -----
   import turtle
   wn = turtle.Screen()
   wn.bgcolor("green")     	
   jamal = turtle.Turtle()
   jamal.color("white")               	
   jamal.pensize(10) 
   =====                
   jamal.left(90)
   jamal.forward(150)
   =====
   jamal.left(90)
   jamal.forward(50)
   =====
   jamal.right(180)
   jamal.forward(100)
   =====
   wn.exitonclick()


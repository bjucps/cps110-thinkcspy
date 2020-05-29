..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-1-
   :start: 1

Function Definition
-------------------

Here's a program that defines a simple function named ``hello``, and then executes it.

.. activecode:: ac11_1_1

    def hello():
        print("Hello")
        print("Glad to meet you")

    hello()  # Execute the function

The syntax for creating a named function, a **function definition**, is:

.. code-block:: python

    def name( parameters ):
        statements

A function definition has two parts: the **function interface**, and the statements, called the **function implementation** or 
**function body**. Let's explore those two parts.

The **function interface** is the first line that specifies the name of the function and some *parameter names* enclosed in parentheses. 

* You can make up any names you want for the functions you create, as long as the name follows the rules for legal
  identifiers that were given previously. You should also avoid defining functions with the same name as as a variable you define,
  or as a built-in function like ``print`` or ``len``. Although Python allows you to do this, the results will quickly lead
  to confusing and undesirable behavior. 

* The parameters specify what information, if any, you have to provide in order to use the new function. Another way to
  say this is that the parameters specify what the function needs to do its work. The parameter list may be empty (as it
  is in this example), or it may contain any number of parameters separated from one another by commas. In either case,
  the parentheses are required. We'll cover more about parameters shortly.

Like other compound statements we've seen such as ``for`` and ``if``, function definitions are a compound statement.
The **function implementation** contains several statements, which must be indented underneath the function interface.

Here's another example of a program that defines a function:

.. activecode:: ac11_1_2
    :nocodelens:

    import turtle

    def drawSquare(t, sz):
        """Make turtle t draw a square of with side sz."""

        for i in range(4):
            t.forward(sz)
            t.left(90)


    wn = turtle.Screen()      # Set up the window and its attributes
    wn.bgcolor("lightgreen")

    alex = turtle.Turtle()    # create alex
    drawSquare(alex, 50)      # Execute the drawSquare function, using alex 

    wn.exitonclick()

The function in this example is named ``drawSquare``. It has two parameters --- one to tell the function which turtle to move around 
and the other to tell it the size of the square we want drawn. In the function definition they are called ``t`` and 
``sz`` respectively. Make sure you know where the body of the function ends --- it depends on the indentation and the 
blank lines don't count for this purpose!

.. admonition::  docstrings

    Take a close look at the triple-quoted string just inside the definition of drawSquare:
    
    .. sourcecode:: python    
        
        def drawSquare(t, sz):
            """Make turtle t draw a square of with side sz."""
    
    By convention, Python programmers write a triple-quoted string as the first line inside a function definition to
    describe what the function does. This string is called a **docstring**. We'll discuss docstrings in more detail
    later in the book. For now, note that the docstring must be indented to the same level as the other lines inside
    the function.

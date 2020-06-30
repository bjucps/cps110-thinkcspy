..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-8-
   :start: 1

.. _input:

Input
-----

.. youtube:: 3T3BEX0Y1h4
    :divid: video_2_6_getting-input
    :height: 315
    :width: 560
    :align: left

.. Demonstrates using the input() function in three environments: activecode, codelens, and Python shell
.. Demonstrates empty string, and the fact that numeric entries are treated as strings

Here is one of the versions of the time conversion program we developed earlier:

.. sourcecode:: python

    tot_seconds = 645
    minutes = tot_seconds // 60
    seconds = tot_seconds % 60
    print(minutes, seconds)

This program is very limited in that it works for only one specific case (645 seconds). If we want to convert
a different value (say, 1028 seconds), we must modify the program, changing the first assignment statement
to use the value 1028 instead of 645. 

This is an example of a program where the data processed by the program is written directly into the instructions of the
program itself. We say that the data is hard coded into the program. A **hard coded** value is one that is written
directly into the instructions of the program, and thus cannot be supplied or modified by the user at runtime. For
simple programs that you can run directly in this textbook environment, that's not a significant problem. To this point,
all of the programs you've seen have used hard coded values. But to be useful to end users who are not programmers,
programs must allow the user to supply information to the program at runtime, without requiring the user to be able to
know how to modify the program.

In order to do this, we need a way to get input from the user.  Luckily, in Python
there is a built-in function called ``input`` to accomplish this task.  

.. sourcecode:: python

    name = input("Please enter your name: ")

At runtime, the input function displays a prompt (in this case, "Please enter your name:"). Then, it waits for the 
user to enter a response and press **Enter**. When this happens, the text that has been entered is
returned from the `input` function, and in this case assigned to the variable `name`.  

Run the following example a couple of times and try some different names in the input box that appears.

.. activecode:: inputfun

    name = input('Please enter your name: ')
    print('Hello,', name, '!')

.. note::

    The behavior of the ``input`` function when running programs in the textbook environment is different
    from its behavior when running programs using the standard Python interpreter. In the book environment,
    the input function displays a pop-up dialog. In the Python interpreter, the prompt appears as part of
    the regular program output. Try it out in the interpreter to see what I mean:

    .. sourcecode:: python

        >>> color = input("What's your favorite color? ")
        What's your favorite color? blue
        >>> color
        'blue'
        >>>

Improving Output Formatting
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Let's tweak the program slightly to improve the formatting. There's a space between the name and the exclamation
point::

    Hello, George !

The space is there because the print function inserts a space between the value of each expression in the comma-delimited
list of expressions in parenthesis. To eliminate the unwanted space, try changing the print statement to look like this::

    print('Hello, ' + name + '!')

Here, instead of supplying a list of expressions, we've created a single expression that uses the ``+`` operator to join
together three strings into a single string value. Recall that ``+`` does concatenation when operating on ``str``
values. Now, run the program and look carefully at the output. The output should look like this::

    Hello, George!

If looks like this::

    Hello,George!

you may have forgotten to put a space after the comma in the first string literal. 

.. note::

    This might be a good time to point out the significance of whitespace in programs. As we've seen, spaces inside quotes 
    are part of the value of a string, and are significant. Spaces outside of quotes have no effect on the program.
    The following print statements all behave exactly the same:

    .. activecode:: input-whitespace
        :nocodelens:

        # No difference between the following 
        name = 'George'
        name='George'

        # No difference between the following 
        print('Hello, ' + name + '!')
        print( 'Hello, ' + name + '!' )
        print('Hello, '+name+'!')

    Even though whitespace outside quotes has no effect on the behavior of a program, separating the parts of
    an expression with individual spaces tends to aid the readability of the code for programmers, and
    is therefore encouraged.

Numeric Input
^^^^^^^^^^^^^

It is very important to note that the ``input`` function returns a string value. If you ask the user to enter a number
and the user enters the number ``17``, ``input`` has no way of knowing that the user's entry represents a number instead
of text; it treats the entry as a string of characters (``str`` data) and the value stored in the variable would be
the string ``"17"``, not the number ``17``. This is true even though the user does not put quotes around the number when
typing it in. Try it out in the interpreter to see what I mean:

.. sourcecode:: python

    >>> num = input('Enter a number: ')
    Enter a number: 17
    >>> num
    '17'
    >>>

This is a good opportunity to re-emphasize the difference between ``int`` and ``str`` data types. When we see the value
``'17'``, it's hard for us to think of anything other than the number 17. But to Python, the string ``'17'`` is simply
a sequence of digits that has no mathematical meaning. 

To see the difficulties that behavior can cause, try executing the following program:

.. activecode:: input_sum

    num1 = input('Enter a number:')
    num2 = input('Enter another number:')
    sum = num1 + num2

    print(num1, '+', num2, '=', sum)

Does the result surprise you? 

This example underscores an important point about the ``+`` operator in Python: it has a dual role.
When operating on numbers it does addition; with strings, it does concatenation. When you look at
an expression involving ``+`` and two variables, you can't know whether the ``+`` is doing an
addition or a concatenation without first understanding the data type of the values referenced by
the two variables. As you can imagine, this can be a source of confusion!

If you want numeric input, you must convert the ``str`` value returned from ``input`` to an ``int`` or a ``float``.
Let's modify the program to use the ``int`` conversion function to convert the user's input from a ``str`` to 
an ``int``:

.. activecode:: input_sum2

    num1 = int(input('Enter a number'))
    num2 = int(input('Enter another number'))
    sum = num1 + num2

    print(num1, '+', num2, '=', sum)

We'll explore conversion functions in more detail in the next section.

Time Conversion Case Study
^^^^^^^^^^^^^^^^^^^^^^^^^^

Now, back to our time conversion program:

.. tabbed:: input_tc1_tabbed

    .. tab:: Question

        Enhance this program so that is more useful. Change this program so that it prompts the user to enter the number
        of seconds, instead of using the value 645.

        .. activecode:: input_tc1

            tot_seconds = 645
            minutes = tot_seconds // 60
            seconds = tot_seconds % 60
            print(tot_seconds, 'seconds =', minutes, 'minutes', seconds, 'seconds')

    .. tab:: Tip

        Change the first line of this program to use the input function to allow the user to enter the number of seconds. 
        Remember to use the int conversion function, as demonstrated above, to convert the user's input to ``int`` value.

    .. tab:: Solution

        Here's the first line::

            tot_seconds = int(input('Enter total seconds:'))


**Check your understanding**

.. mchoice:: test_question2_7_1
   :practice: T
   :answer_a: &lt;class 'str'&gt;
   :answer_b: &lt;class 'int'&gt;
   :answer_c: &lt;class 18&gt;
   :answer_d: 18
   :correct: a
   :feedback_a: All input from users is read in as a string.
   :feedback_b: Even though the user typed in an integer, it does not come into the program as an integer.
   :feedback_c: 18 is the value of what the user typed, not the type of the data.
   :feedback_d: 18 is the value of what the user typed, not the type of the data.

   What is printed when the following statements execute?

   .. code-block:: python

     n = input("Please enter your age: ")
     # user types in 18
     print ( type(n) )


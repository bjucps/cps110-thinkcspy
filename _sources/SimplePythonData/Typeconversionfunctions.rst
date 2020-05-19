..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: data-3-
   :start: 1

Type conversion functions
-------------------------

Sometimes it is necessary to convert values from one type to another.  Python provides
a few simple functions that will allow us to do that.  The functions ``int``, ``float`` and ``str``
will (attempt to) convert their arguments into types `int`, `float` and `str`
respectively.  We call these **type conversion** functions.

The ``int`` function can take a floating point number or a string, and turn it
into an int. If you give a float value to ``int``, it *discards* the decimal portion of
the number - a process we call *truncation towards zero* on the number line.
Let us see this in action::

    >>> int(3.7)
    3
    >>> int('3')
    3
    >>>

The ``float`` function takes a string and converts it to a ``float`` value::

    >>> float('3.7')
    3.7
    >>>

And the ``str`` function takes either an int or a float and converts it to a string::

    >>> str(3.7)
    '3.7'
    >>> str(-15)
    '-15'
    >>>

Now, take a look at this example:

.. sourcecode:: python

    >>> int('abc')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    ValueError: invalid literal for int() with base 10: 'abc'
    >>>

It is illegal to attempt to convert a string that does not represent a number to an int or a float using the
``int`` and ``float`` functions. Python reports an error if you attempt to do this.

Using Type Conversion Functions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Now that you've seen the type conversion functions, let's explore how they are actually used in programs.
In the last section, you saw a program that asks the user for two numbers and adds them together. Here's the
original version, which misbehaved::

    num1 = input('Enter a number:')
    num2 = input('Enter another number:')
    sum = num1 + num2

    print(num1, '+', num2, '=', sum)

Here is the corrected version:

.. activecode:: typeconv_sum1

    num1 = int(input('Enter a number:'))
    num2 = int(input('Enter another number:'))
    sum = num1 + num2

    print(num1, '+', num2, '=', sum)

In this example, the first two lines take the string value produced by the ``input`` function and convert each to an
integer using the ``int`` function. Take a moment to step through this in CodeLens. 

Let's look at another way of writing the same program:

.. activecode:: typeconv_sum2

    num1 = input('Enter a number:')
    num2 = input('Enter another number:')
    sum = int(num1) + int(num2)

    print(num1, '+', num2, '=', sum)

In this version of the program, ``num1`` and ``num2`` hold ``str`` values rather than ``int`` values. Their ``str``
values are converted to ``int`` values in line 3 for use in the addition operation, but the variables themselves retain
their ``str`` values. This is a fine point, but it's important important for you to grasp. Step through the program in
CodeLens to see that for yourself.

Let's dive into this a little more deeply. Currently, there is a space in between the parts of the output::

    2 + 2 = 4

Suppose we didn't want the spaces in between the numbers and the symbols? How would you eliminate the spaces to display something like this::

    2+2=4

Think about it for a moment and see if you can come up with the answer.

Did you figure it out? The answer involves using string concatenation in the print statement instead of using commas.
Try modifying the second example above to use string concatenation in the print statement to produce the desired output
with no spaces. For a refresher of the technique, see "Improving Output Formatting" in the :ref:`previous
section<input>`.

.. reveal:: typeconv_sum2_concat
   :showtitle: Show me the solution
   :modal:
   :modalTitle: Here's the solution!

   .. sourcecode:: python

        num1 = input('Enter a number:')
        num2 = input('Enter another number:')
        sum = int(num1) + int(num2)

        print(num1 + '+' + num2 + '=' + str(sum))


   Notice how this solution uses the ``str`` function to convert the value in ``sum`` to a string, so that it can be
   concatenated with the other strings in the print statement.

Formatting Output
^^^^^^^^^^^^^^^^^

Remember that the ``+`` operator can be used for two purposes: adding numbers, and concatenating strings. However, in
order for ``+`` to work, both operands must be either numeric or a ``str``. The following Python shell example
illustrates this point::

    >>> count = 5
    >>> 'count is ' + str(count)
    'count is 5'
    >>> 'count is ' + count
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: can only concatenate str (not "int") to str
    >>>

Since programs often need to display output involving several variables on one line, but without the
extra space that results when you separate your expressions with a comma, it's common to use a lot of
string concatenation in print statements. However, the resulting code is littered with ``+`` symbols
and often not very easy to read. Just look at this line from the solution above::

    print(num1 + '+' + num2 + '=' + str(sum))

Not very writable or readable, is it? You have to think hard about where the quotes go and what each +
does.

Recent versions of Python provide an elegant way to improve the readability of these print statements:
the f-String. An **f-String** is a string that contains embedded references to variables. Take a look
at this version of our sum program:

.. sourcecode:: python

    num1 = int(input('Enter a number:'))
    num2 = int(input('Enter another number:'))
    sum = num1 + num2

    print(f'{num1} + {num2} = {sum}')

This program produces the same output as the ones above. However, it uses an f-String to streamline the print statement.
An f-String starts with a lowercase ``f`` just before the opening quote. See the ``f`` just inside the opening
parenthesis of the print statement? It's easy to miss. f-Strings contain embedded variable references enclosed in curly
braces, like ``{num1}`` and ``{sum}``. When evaluated, the f-String inserts the value of the referenced variable at the
indicated spot in the string. There's no need to use the ``str`` conversion function or concatenation operator to get
several values displayed on the same line.

The activecode interpreter for this book doesn't support f-Strings, so you can't experiment with them in the book. But
if you have Python version **3.6 or later** installed on your computer, you can use them, and enjoy the improved
readability and writability that results. Since that version was released around 2016, if you downloaded and installed
Python on your computer when you started using this book, you definitely have f-String support.


**Check your understanding**

.. mchoice:: test_question2_2_1
   :practice: T
   :answer_a: Nothing is printed. It generates a runtime error.
   :answer_b: 53
   :answer_c: 54
   :answer_d: 53.785
   :correct: b
   :feedback_a: The statement is valid Python code.  It calls the int function on 53.785 and then prints the value that is returned.
   :feedback_b: The int function truncates all values after the decimal and prints the integer value.
   :feedback_c: When converting to an integer, the int function does not round.
   :feedback_d: The int function removes the fractional part of 53.785 and returns an integer, which is then printed.

   What value is printed when the following statement executes?

   .. code-block:: python

      print( int(53.785) )


.. clickablearea:: ca_id_ints
    :question: Click on all of the variables that hold a value of type `int` in the code below
    :iscode:
    :feedback: Remember input returns a `str`

    :click-incorrect:seconds:endclick: = input("Please enter the number of seconds you wish to convert")

    :click-correct:hours:endclick: = int(:click-incorrect:seconds:endclick:) // 3600
    :click-correct:total_secs:endclick: = int(:click-incorrect:seconds:endclick:)
    :click-correct:secs_still_remaining:endclick: = :click-correct:total_secs:endclick: % 3600
    print(:click-correct:secs_still_remaining:endclick:)

.. clickablearea:: ca_id_str
    :question: Click on all of the variables that hold a value of type `str` in the code below
    :iscode:
    :feedback:

    :click-correct:seconds:endclick: = input("Please enter the number of seconds you wish to convert")

    :click-incorrect:hours:endclick: = int(:click-correct:seconds:endclick:) // 3600
    :click-incorrect:total_secs:endclick: = int(:click-correct:seconds:endclick:)
    :click-incorrect:secs_still_remaining:endclick: = :click-incorrect:total_secs:endclick: % 3600
    print(:click-incorrect:secs_still_remaining:endclick:)



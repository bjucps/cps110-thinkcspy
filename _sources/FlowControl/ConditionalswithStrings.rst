..  Copyright (C)  Stephen Schaub.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

Conditionals with Strings
=========================

There are a few things to keep in mind when using ``if`` statements with string variables.

First, when comparing a variable with a string value, remember to quote the string value, as in 
this example:

.. activecode:: ch05_comparestring

      color = input('Enter a color:')

      if color == 'red':
        print('Red is my favorite color!')
      else:
        print('I like ' + color + ', too.')

String comparisons are **case sensitive**. That means that, in the example above, if the user
enters **RED**, the comparison to 'red' will be ``False``, since the values being compared are in different
capitalizations. 

If you want a **case insensitive** comparison, one technique involves converting all of the letters
in the string to lowercase or uppercase, using an appropriate string method. We cover string methods
in more detail in the chapter on strings, but for now, I'll give you a sneak peek. Try changing
the comparison in line 3 above to the following::

    if color.lower() == 'red':

Then, run the program and try entering values like 'RED', 'Red', and 'red'. The program will recognize
all three capitalizations as the word 'red' because the expression ``color.lower()`` 
converts the input to all lowercase before comparing it with the value 'red'. 

Checking for Empty Strings
--------------------------

You can check to see if the user entered a value by comparing the variable containing the user's input 
with an empty string, like this:

.. activecode:: ch05_emptystring

      color = input('Enter a color:')

      if color != '':
        # User entered at least one character
        print(color + ' is my favorite color!')
      else:
        print('You did not enter anything.')

Try running this example a couple of times. In one test, try entering a color, and in another,
try pressing Enter without entering a value. 

The value ``''`` (two quotes with no space between) represents an empty string. When the user
enters at least one character, the comparison ``color != ''`` is True. However, when the
user presses Enter without entering a value, Python stores an empty string in ``color``, and the
comparison ``color != ''`` is False.

Comparing Strings and Numbers
-----------------------------

You can compare string values with string values, and number values with number values.
However, you can run into trouble if you attempt to compare string values with number values.
Take a look at this example:

.. activecode:: ch05_compare_str_num

      num = input('Enter a number:')

      if num == 0:
        print('You entered zero.')
      else:
        print('You did not enter zero.')

Try running this example and entering 0.

When Python evaluated the expression ``num == 0``, it computed the result ``False`` 
because the value in ``num`` was type ``str``, 0 was type ``int``, and ``==``
never considers a ``str`` value to be equal to an ``int`` value.

Take a moment to see if you can figure out how to correct the program above to correctly respond
'You entered zero.' when the user enters 0.

.. reveal:: rte_compare_str_num
   :showtitle: Show me the solution
   :modal:
   :modalTitle: Correcting the problem

   There are two ways you can correct the problem. One is to use the ``int()`` function to
   convert the user's input to an int, like this::

       num = int(input('Enter a number:'))

   The other is to change the if statement so that it compares ``num`` with a ``str``, like this::

       if num == '0':

A different problem occurs if you attempt to use a greater than or less than comparison. Try running
the following example:

.. activecode:: ch05_compare_str_num_gt

      num = input('Enter a number:')

      if num >= 0:
        print('You entered a number greater than zero.')

Attempting to compare a string value with a number is legal with ``==`` and ``!=`` (even though it
leads to confusing results), but is illegal with the other comparison operators.

To Python, strings and numbers are different data types, and it's important for you to ensure that
the values you are comparing in ``if`` statements are either both strings or both numbers.

**Check your understanding**

.. mchoice:: ch05_comparestr_1
   :practice: T
   :answer_a: No
   :answer_b: Yes
   :correct: a
   :feedback_a: Correct. The comparison ``x < '0'`` is illegal and will cause a runtime error.
   :feedback_b: Incorrect. The comparison ``x < '0'`` is illegal and will cause a runtime error.

   Will the following code fragment report that x is negative?

   .. code-block:: python

     x = -10
     if x < '0':
         print('x is negative.')
     else:
         print('x is not negative.')


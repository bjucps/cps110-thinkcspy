..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-5-
   :start: 1

.. _stringMethods:

String Methods
--------------

We previously saw that each turtle instance has its own attributes and
a number of methods that can be applied to the instance.  For example,
we wrote ``tess.right(90)`` when we wanted the turtle object ``tess`` to perform the ``right`` method to turn
to the right 90 degrees.  The "dot notation" is the way we connect the name of an object to the name of a method
it can perform.

Strings are also objects.  Each string instance has its own attributes and methods.  The most important attribute of the string is the collection of characters.  There are a wide variety of methods.  Try the following program.

.. activecode:: chp08_upper

    ss = "Hello, World"
    print(ss.upper())

    tt = ss.lower()
    print(tt)


In this example, ``upper`` is a method that can be invoked on any string object
to create a new string in which all the
characters are in uppercase.  ``lower`` works in a similar fashion changing all characters in the string
to lowercase.  (The original string ``ss`` remains unchanged.  A new string ``tt`` is created.)

In addition to ``upper`` and ``lower``, the following table provides a summary of some other useful string methods.  There are a few activecode examples that follow so that you can try them out.

==========  ==============      ==================================================================
Method      Parameters          Description
==========  ==============      ==================================================================
upper       none                Returns a string in all uppercase
lower       none                Returns a string in all lowercase
capitalize  none                Returns a string with first character capitalized, the rest lower

strip       none                Returns a string with the leading and trailing whitespace removed
lstrip      none                Returns a string with the leading whitespace removed
rstrip      none                Returns a string with the trailing whitespace removed
count       item                Returns the number of occurrences of item
replace     old, new            Replaces all occurrences of old substring with new

center      width               Returns a string centered in a field of width spaces
ljust       width               Returns a string left justified in a field of width spaces
rjust       width               Returns a string right justified in a field of width spaces

find        item                Returns the leftmost index where the substring item is found, or -1 if not found
rfind       item                Returns the rightmost index where the substring item is found, or -1 if not found
index       item                Like find except causes a runtime error if item is not found
rindex      item                Like rfind except causes a runtime error if item is not found
format      substitutions       Involved! See :ref:`Format-Strings`, below
==========  ==============      ==================================================================

You should experiment with these
methods so that you understand what they do.  Note once again that the methods that return strings do not
change the original.  You can also consult the `Python documentation for strings <https://docs.python.org/3/library/stdtypes.html#string-methods>`_.

.. activecode:: ch08_methods1

    ss = "    Hello, World    "

    els = ss.count("l")
    print(els)

    print("***" + ss.strip() + "***")
    print("***" + ss.lstrip() + "***")
    print("***" + ss.rstrip() + "***")

    news = ss.replace("o", "***")
    print(news)


.. activecode:: ch08_methods2


    food = "banana bread"
    print(food.capitalize())

    print("*" + food.center(25) + "*")
    print("*" + food.ljust(25) + "*")     # stars added to show bounds
    print("*" + food.rjust(25) + "*")

    print(food.find("e"))
    print(food.find("na"))
    print(food.find("b"))

    print(food.rfind("e"))
    print(food.rfind("na"))
    print(food.rfind("b"))

    print(food.index("e"))


**Check your understanding**

.. mchoice:: test_question8_3_1
   :practice: T
   :answer_a: 0
   :answer_b: 2
   :answer_c: 3
   :correct: c
   :feedback_a: There are definitely o and p characters.
   :feedback_b: There are 2 o characters but what about p?
   :feedback_c: Yes, add the number of o characters and the number of p characters.


   What is printed by the following statements?

   .. code-block:: python

      s = "python rocks"
      print(s.count("o") + s.count("p"))




.. mchoice:: test_question8_3_2
   :practice: T
   :answer_a: yyyyy
   :answer_b: 55555
   :answer_c: n
   :answer_d: Error, you cannot combine all those things together.
   :correct: a
   :feedback_a: Yes, s[1] is y and the index of n is 5, so 5 y characters.  It is important to realize that the index method has precedence over the repetition operator.  Repetition is done last.
   :feedback_b: Close.  5 is not repeated, it is the number of times to repeat.
   :feedback_c: This expression uses the index of n
   :feedback_d: This is fine, the repetition operator used the result of indexing and the index method.


   What is printed by the following statements?

   .. code-block:: python

      s = "python rocks"
      print(s[1] * s.index("n"))


.. index::
   braces; format string
   single: {}; format string
   format string
   string; format method


.. _Format-Strings:

More on f-Strings
~~~~~~~~~~~~~~~~~~~~~

We introduced f-Strings in Chapter 2 as a convenient way to get the values of variables
inserted into a string. For example, rather than writing:

.. code-block:: python

    count = 5
    msg = 'count is ' + str(count)

You can write:

.. code-block:: python

    count = 5
    msg = f'count is {count}'

and achieve the same effect. Note the ``f`` before the opening quote of the string: that cues the Python interpreter
to look inside the string literal for variable names surrounded by ``{}`` and replace those markers with the variables'
values.

f-Strings can include formatting specifications. Take a look at this example:

.. activecode:: ch08_methods6

    origPrice = 56.235
    discount = .08
    newPrice = (1 - discount/100)*origPrice
    calculation = f'${origPrice:.2f} discounted by {discount}% is ${newPrice:.2f}.'
    print(calculation)

In this example, the line

.. sourcecode:: python

    calculation = f'${origPrice:.2f} discounted by {discount}% is ${newPrice:.2f}.'

contains a complicated f-String with three markers:

* ``{origPrice:.2f}`` inserts the value of ``origPrice``, rounded to two decimal places
* ``{discount}`` inserts the value of ``discount``
* ``{newPrice:.2f}`` inserts the value of ``newPrice``, rounded to two decimal places

In the example above, we've created a variable and then printed it, but we could have
done both steps in one line, like this:

.. code-block:: python

    print(f'${origPrice:.2f} discounted by {discount}% is ${newPrice:.2f}.')

A technical point: Since braces have special meaning in f-Strings,
if you want braces to actually be included in the final *formatted* string,
you must double them. For example, the initial and final doubled
braces in the format string below generate literal braces in the
formatted string.

.. code-block:: python

    a = 5
    b = 9
    print(f'The set is {{ {a}, {b} }}.')

This produces the output::

    The set is { 5, 9 }.

.. _format-method:

The ``format`` method
~~~~~~~~~~~~~~~~~~~~~

``f-Strings`` are a relatively recent addition to Python. Before they were added to the language,
the the string method ``format`` was used to insert variables into strings. 

Have a look at this example:

.. activecode:: ch08_methods3

    first = input('Your first name: ')
    last = input('Your last name: ')
    greeting = 'Hello {} {}!'.format(first, last)
    print(greeting)

The string for the ``format`` method has a special form, with braces embedded.
Such a string is called a *format string*. For each pair of curly
braces in the format string, the ``format`` method substitutes a value
from its parameter list. In the example above, the value of the parameter ``first``
is substituted in place of the first pair of curly brackets, and the value
of the parameter ``last`` is substituted in place of the second pair.

Like f-Strings, format strings can give further information inside the braces
showing how to specially format data:

.. activecode:: ch08_methods7

    origPrice = 56.23
    discount = .08
    newPrice = (1 - discount/100)*origPrice
    calculation = '${:.2f} discounted by {}% is ${:.2f}.'.format(origPrice, discount, newPrice)
    print(calculation)

This kind of format string depends directly on the order of the
parameters to the format method. There are other approaches that we will
skip here, explicitly numbering substitutions and taking substitutions from a dictionary.

For more information on the type of formatting specifications you can use in format strings (and f-Strings), see
`this helpful article <https://www.digitalocean.com/community/tutorials/how-to-use-string-formatters-in-python-3>`_.


So, which should you use: format strings or f-Strings? In most cases, f-Strings are preferable, because they tend to
produce more readable code. However, it helps to know about both techniques, since the code you will see on the Internet
(and in this book) uses both.



.. mchoice:: test_question8_3_3
   :practice: T
   :answer_a: Nothing - it causes an error
   :answer_b: sum of {} and {} is {}; product: {}. 2 6 8 12
   :answer_c: sum of 2 and 6 is 8; product: 12.
   :answer_d: sum of {2} and {6} is {8}; product: {12}.
   :correct: c
   :feedback_a: It is legal format syntax:  put the data in place of the braces.
   :feedback_b: Put the data into the format string; not after it.
   :feedback_c: Yes, correct substitutions!
   :feedback_d: Close:  REPLACE the braces.


   What is printed by the following statements?

   .. code-block:: python

       x = 2
       y = 6
       print('sum of {} and {} is {}; product: {}.'.format( x, y, x+y, x*y))


.. mchoice:: test_question8_3_4
   :practice: T
   :answer_a: 2.34567 2.34567 2.34567
   :answer_b: 2.3 2.34 2.34567
   :answer_c: 2.3 2.35 2.3456700
   :correct: c
   :feedback_a: The numbers before the f in the braces give the number of digits to display after the decimal point.
   :feedback_b: Close, but round to the number of digits and display the full number of digits specified.
   :feedback_c: Yes, correct number of digits with rounding!


   What is printed by the following statements?

   .. code-block:: python

       v = 2.34567
       print('{:.1f} {:.2f} {:.7f}'.format(v, v, v))



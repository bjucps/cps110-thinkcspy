..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: strings-5a-
   :start: 1

String Formatting
-----------------

.. index::
   braces; format string
   single: {}; format string
   format string
   string; format method


In this section, we'll explore techniques to format information into strings.

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

.. The following section has been removed since the page fails to render properly
.. with the version of Runestone current in 2020

.. A technical point: Since braces have special meaning in f-Strings,
.. if you want braces to actually be included in the final *formatted* string,
.. you must double them. For example, the initial and final doubled
.. braces in the format string below generate literal braces in the
.. formatted string.

.. ::

..     a = 5
..     b = 9
..     print(f'The set is {{ {a}, {b} }}.')

.. This produces the output::

..     The set is { 5, 9 }.

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



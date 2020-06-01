
.. qnum::
   :prefix: valrevisit-
   :start: 1

Validation Revisited
--------------------

Using boolean logic, we can considerably simplify our validation example 
presented earlier. For reference, here's a slightly simplified form of the original version:

.. sourcecode:: python

    valid_input = False
    while valid_input == False:
        response = input('Do you like lima beans? Y)es or N)o: ')
        response = response.upper()
        if response == 'Y':
            valid_input = True
        elif response == 'N':
            valid_input = True

    if response == 'Y':
        print('Great! They are very healthy.')
    else:
        print('Too bad. If cooked right, they are quite tasty.')

.. tabbed:: valid_revisit_tab

    .. tab:: Question

        Replace the ??? in the program below with a boolean expression
        that causes the loop to keep repeating until the user enters a Y or
        an N.

        .. activecode:: ch07_validation_revisit
            :timelimit: 60000

            response = input('Do you like lima beans? Y)es or N)o: ')
            while ???:
              response = input('Do you like lima beans? Y)es or N)o: ')

            if response == 'Y':
                print('Great! They are very healthy.')
            else:
                print('Too bad. If cooked right, they are quite tasty.')

    .. tab:: Tip

        Design an expression that yields True if ``response`` is something other 
        than a Y or an N.

    .. tab:: Solution 

        Here is one solution:

        .. sourcecode:: python

            while response != 'Y' and response != 'N':

        There are other possible solutions. To explore them, look at the exercise
        below.

As you can see, boolean expressions can considerably streamline the code necessary
to perform input validation.

**Check your understanding**

.. mchoice:: valrevisit-1
   :practice: T

   Which of the following expressions is equivalent to ``response != 'Y' and response != 'N'``?
   To help you figure out the answer, try putting in values 'Y', 'N', and 'X' in the following
   expressions and evaluating them to see if they produce the same value as they do for
   this expression.

   - not (response == 'Y' or 'N')

     - Incorrect. ``or`` needs a boolean expression on both sides.

   - not (response == 'Y' and response == 'N')

     - Incorrect. Try plugging in the value of ``'Y'`` in this expression and the original
       to see 

   - not (response == 'Y' or response == 'N')

     + Correct!

   - not response == 'Y' and not response == 'N'

     + Correct!

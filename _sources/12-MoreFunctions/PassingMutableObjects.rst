..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: func-12-
   :start: 1

Passing Mutable Objects
-----------------------

.. youtube:: DeSEZgN6xIU
    :divid: vid_mutableobjects
    :height: 315
    :width: 560
    :align: left


Take a look at the following code example. Can you predict what will happen when you run it?

.. activecode:: ac11_12_1
   
   def double(y):
       y = 2 * y
   
   num = 5
   double(num)
   print(num)

Use **Show CodeLens** to step through the code to see why the assignment to the formal parameter ``y``
inside ``double`` did not affect the argument ``num``. An assignment to a formal parameter inside a function **never**
affects the argument in the caller.

On the other hand, if you are passing a mutable object, such as a list, to a function, and the function alters the
object's state, that state change will be visible to the caller when the function returns. Take a look at the following
example.

.. activecode:: ac11_12_2
     
   def changeit(lst):
       lst[0] = "Michigan"
       lst[1] = "Wolverines"
      
   mylst = ['our', 'students', 'are', 'awesome']
   changeit(mylst)
   print(mylst)

Try stepping through this in codelens to see what happens. The state of the list referenced by ``lst`` is altered
by ``changeit``, and since ``mylst`` is an alias for ``lst``, ``mylst`` is affected by the actions taken by the function.

Look closely at this line::

    lst[0] = "Michigan"

That statement modifies the state of ``lst`` by changing the value in slot 0. Although that line may appear to contradict the
statement above that "an assignment to a formal parameter inside a function never affects the argument in the caller,"
note that there is a difference between assigning to a *slot* of a list, and assigning to the list variable itself.
To see that difference, try changing that line to the following::

    lst = ["BJU", "Bruins"]

Then, run again. This time, ``mylist`` is not altered. To understand why, use CodeLens to step carefully through the code
and observe how the assignment to ``lst`` causes it to refer to a separate list.

Take a moment to experiment some more with the ``changeit`` function. Change the body of the function to the following::

    lst.append("Michigan Wolverines")

Step through using CodeLens. You should see that ``mylst`` is affected by this change, since the state of the list is altered.

Then, try again with this as the body::

    lst = lst + ["Michigan Wolverines"]

Step through using CodeLens. Here, we create a new list using the concatenation operator, and ``mylst`` is not affected by the change.

Understanding the techniques that functions can and cannot use to alter the state of mutable parameters is important.
You may want to take some time to study the information on this page more thoroughly and play with the examples until
you feel confident about your grasp of the material.

Side Effects
~~~~~~~~~~~~

We say that the original function ``changeit`` above has a **side effect** on the list object that is passed to it. In general, any
lasting effect that occurs as a result of a function call is called a side effect. Here are some ways a function can
have a side effect:

* Printing out a value. This doesn't change any objects or variable bindings, but it does have a potential lasting effect outside the function execution, because a person might see the output and be influenced by it.
* Changing the state of a mutable object, such as appending a value to a list or modifying the value in a certain position in a list.
* Changing the value of a global variable.

Side effects are sometimes convenient. For example, it may be convenient to have a single dictionary that accumulates 
information, and pass it around to various functions that might add to it or modify it.

However, programs that have side effects involving global variables can be very difficult to debug. When an object has a
value that is not what you expected, it can be difficult to track down exactly where in the code it was set. Wherever it
is practical to do so, it is best to avoid having functions modify the values of global variables, but to transfer
information instead using parameters and return values.

**Check Your Understanding**

.. mchoice:: mutobj-q1

    What is the output of the following code fragment?

    .. sourcecode:: python

        def myfun(lst):
            lst = [1, 2, 3]

        mylist = ['a', 'b']
        myfun(mylist)
        print(mylist)

    - ['a', 'b']

      + Correct! ``mylist`` is not changed by the assignment in ``myfun``.

    - [1, 2, 3]

      - Incorrect. ``mylist`` is not changed by the assignment in ``myfun``.

.. mchoice:: mutobj-q2

    What is the output of the following code fragment?

    .. sourcecode:: python

        def myfun(lst):
            del lst[0]

        mylist = ['a', 'b']
        myfun(mylist)
        print(mylist)

    - ['a', 'b']

      - Incorrect. ``myfun`` alters the state of the list object by removing the value at slot 0.

    - ['b']

      + Correct! ``myfun`` alters the state of the list object by removing the value at slot 0.

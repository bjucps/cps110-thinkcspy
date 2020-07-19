..  Copyright (C)  Stephen Schaub.  Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts.  A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: pytest-1-
   :start: 1

Testing with pytest
===================

Writing automated unit tests is very helpful in reducing the effort needed to build software. However, the simple
approach described so far is inadequate to help programmers realize the full benefits of unit testing. In this section,
we introduce a unit test framework which addresses some practical issues that crop up when you try to apply
unit testing techniques in software development projects. Here are some of the issues with using plain assertion unit
tests:

* Simple assert-based tests don't give very good diagnostic information when they fail. It would help to have better
  reporting. For example, when an assert fails, it would help us in diagnosing the error to see what value the function
  actually produced. An AssertionError doesn't give us that information.

* We need a better way to organize our unit test code. So far, I've suggested creating separate programs to hold
  the functions under test together with their unit test code. But that isn't practical for most projects. For example,
  functions often need to call other functions in the program in order to do their work. It's not convenient to
  bring those auxiliary functions over into separate test programs.

* We need a way to keep the unit test around and use it even after the function is first developed
  to help us catch bugs that are inadvertently introduced into the function when we make modifications to it.

Unit testing frameworks help to address these issues, by improving error reporting, providing a structure
for programmers to organize their unit tests, and making it possible to leverage existing unit tests when
making enhancements to functions. **pytest** is one unit testing framework that provides these benefits.

For our purposes, the attractive thing about pytest is that writing unit tests with pytest feels a lot like writing unit
tests using plain assert statements. The only difference is that you put your assert statements into test functions.
Here's an example of how it works:

.. activecode:: ac_round6_pytest1

    def round6(num: float) -> int:
        """This function has a bug in it"""
        return int(num + .6)

    # ---- automated unit test ----

    def test_round6():
        assert round6(9.7) == 10
        assert round6(8.5) == 8

    ====

    success = True
    for item in globals():
        if item.startswith("test_"):
            try:
                globals()[item]()
            except Exception as e:
                success = False
                print(item + "() test failed with", e)

    if success:
        print("All tests passed!")
        
This code example defines two functions: the function to be tested, ``round6``, and a function named ``test_round6``
that contains unit test code. When using the pytest approach, you write your unit test as a function whose name must
start with the prefix ``test_``. Inside the function, you write normal assert statements to test the desired function.
Notice that you do not write a line to *call* the unit test function. Instead, when you launch pytest to run the unit
tests, pytest scans your script and executes only the functions with the prefix ``test_``. 

This ActiveCode environment simulates pytest by scanning for and executing functions with a ``test_`` prefix when you
click **Run**. Go ahead and try it. 

To run pytest unit tests outside the textbook, you could put this example code into a Python file
named something like myround.py, and execute it with the pytest command, like this::

    pytest myround.py

.. note:: 

    To use the pytest command, you must first install pytest. Use the **pip** command from your computer's command line
    or terminal to do that. **pip** downloads and installs Python libraries. Enter the following command:

    Windows::

        pip install pytest 

    Mac/Linux::

        pip3 install pytest 

Understanding pytest Failure Reports
------------------------------------

When you run pytest and an assertion fails, you see a report like this::

    =============================== FAILURES ================================
    ______________________________ test_round6 ______________________________
        def test_round6():
            assert round6(9.7) == 10
    >       assert round6(8.5) == 8
    E       assert 9 == 8
    E        +  where 9 = round6(8.5)
                                                                            
    test.py:8: AssertionError

Let's take a closer look at this report to understand what it's telling you.

#. First, notice the line with the ``>`` symbol::

       >       assert round6(8.5) == 8

   The ``>`` symbol points to the line with the assertion that failed.

#. Next, notice the lines marked ``E``::

       E       assert 9 == 8
       E        +  where 9 = round6(8.5)

   This indicates that the call to ``round6(8.5)`` returned the value 9, instead of the value 8.
   The value ``9`` is the actual result of the function. Knowing the value actually produced by 
   the function can help you to troubleshoot the bug and correct the problem.

Integrated Unit Testing with pytest
------------------------------------

When you use the pytest framework, you can include pytest test functions in your main program, along with the rest of
your program code. This allows you to keep your tests together with the functions that they test, and you can run either
your program (using the python command) or the unit tests (using the pytest command). 

Take a look at this example that shows a function (``round6``), together with a unit test function (``test_round6``), and 
a main program that uses ``round6``:

.. sourcecode:: python
    :linenos:

    def round6(num: float) -> int:
        return int(num + .6)

    # ---- automated unit test ----

    def test_round6():
        assert round6(9.7) == 10
        assert round6(8.5) == 8

    # ----- main program follows -----

    if __name__ == '__main__':
        num = float(input('Enter a value:'))
        print('The value rounded is: ' + str(round6(num)))

Notice how the main program is inside the ``if`` statement on line 12. This if condition is true when the program is run
using the **python** command, and allows the main program to execute. When the unit tests are executed using the
**pytest** command, any top-level code outside a function in the python file gets executed when **pytest** scans the
script looking for unit test functions with a ``test_`` prefix. The ``if`` condition is false in this scenario, and that
prevents the main program from executing when **pytest** is scanning the script. If that explanation didn't make total
sense, just remember: in order for pytest to work correctly, any code that is part of the main program must be inside an
``if`` statement like the one in this example, so that it doesn't interfere with pytests's unit testing process.

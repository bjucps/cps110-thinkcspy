.. index:: testing, unit test, equivalence class

Unit Testing
------------

When we write functions that return values, we intend to use them over and over again. However, we want to be 
certain that they return the correct result. To be more certain these functions work correctly we write unit tests.

To write a **unit test**, we must know the correct result when calling the function with a specific input. 


.. activecode:: ch04_ut1
    :include: run_unit_tests

    def square(x):
        '''raise x to the second power'''
        return x * x
    
    def test_square():
        assert square(10) == 100



    ====

    run_unit_tests()


.. admonition:: Extend the program ...

   On line 8, write another unit test (that should pass) for the ``square`` function.


Choosing Good Unit Tests
^^^^^^^^^^^^^^^^^^^^^^^^

When we write unit tests, we should consider significantly different valid inputs to the function. 

For example, the input to the ``square`` function could be either a positive or negative value. These two different kinds of inputs give us two **equivalence classes** of inputs. We then choose an input from each of these classes. **It is important to have at least one test for each equivalence class of inputs.**

Semantic errors are often caused by improperly handling the boundaries between equivalence classes. The boundary for this problem is zero. **It is important to have a test at each boundary.**

.. admonition:: Extend the program ...

   Starting on line 9, write two more unit tests (that should pass) so that all input equivalence classes and boundaries are covered.


.. activecode:: run_unit_tests
    :hidecode:

    def run_unit_tests():

        all_tests_passed = True
        some_tests_detected = False
        for (name, func) in globals().items():

            if name.startswith("test_"):
                some_tests_detected = True
                try:
                    func()
                    print(name + " tests passed.")
                except Exception as e:
                    all_tests_passed = False
                    print("Test " + name + " failed: " + str(e))

        if some_tests_detected:
            if all_tests_passed:
                print("Congrats - all tests passed!")
        else:
            print("No tests found.")

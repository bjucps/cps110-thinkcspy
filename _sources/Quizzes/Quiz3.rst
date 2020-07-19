.. qnum::
   :prefix: quiz-3
   :start: 1

Code Quiz 3
===========

Part 1
------

.. actex:: ac_quiz3-1
    :autograde: unittest
    :timelimit: 1000

    (20 points) Write a function named `stringify` that takes a list of strings, and converts them to a colon-delimited
    string, with each value in the list surrounded with {} brackets::
    
        def select(items: list, key: str) -> list
    
    For example::

        stringify(["a", "b", "c"]) == ":{a}:{b}:{c}:"
        stringify([]) == ":"
    
    ~~~~

    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(stringify(["a", "b", "c"]), ":{a}:{b}:{c}:", """Test 1: stringify(["a", "b", "c"]) == ":{a}:{b}:{c}:" (10 points)""")
            self.assertEqual(stringify([]), ':', """Test 2: stringify([]) == ":" (5 points)""")
            self.assertEqual(stringify(["2"]), ":{2}:", """Test 3: stringify(["2"]) == ":{2}:" (5 points)""")

    myTests().main()


Part 2
------

.. actex:: ac_quiz3-2
    :autograde: unittest
    :timelimit: 1000

    (15 points) Write a function named `select`. The function should accept a list of dictionaries and a key, and should return a list
    containing the values in the dictionaries that are associated with the key specified by key::

        def select(items: list, key: str) -> list
    
    For example::

        select([{"a": "cat", "b": "dog"}, {"a": "gerbil", "b": "pig"}], "b") == ["dog", "pig"]
        select([{"a": "cat", "c": "dog"}, {"a": "gerbil", "b": "pig"}], "b") == ["pig"]

    The second example shows that the dictionary may not contain the key.

    ~~~~

    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(select([{"a": "cat", "b": "dog"}, {"a": "gerbil", "b": "pig"}], "b"), ["dog", "pig"], "Test 1: (first above) (10 points)")
            self.assertEqual(select([{"a": "cat", "c": "dog"}, {"a": "gerbil", "b": "pig"}], "b"), ["pig"], "Test 2: (second above) (5 points)")

    myTests().main()

Part 3
------

.. actex:: ac_quiz3-3
    :autograde: unittest
    :timelimit: 1000

    (15 points) Write a function named `parse`. The function should accept a query string and return a dictionary containing query
    variables and their associated values::

        def parse(qry: str) -> dict
    
    For example::

        parse("?a=bat&wonderful=stuff&count=56") == {"a":"bat", "wonderful":"stuff", "count":"56"}

    Make sure your function works properly for empty query strings ("?"), as well as for query variables whose values
    are empty ("?a=&b="). You may assume that the query string is properly formed (no empty query variables). You may
    also assume that the query string contains no duplicate query variables.

    ~~~~

    ====
    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def testOne(self):
            self.assertEqual(parse("?a=bat&wonderful=stuff&count=56"),  {"a":"bat", "wonderful":"stuff", "count":"56"}, "Test 1: (first above) (5 points)")
            self.assertEqual(parse("?"),  {}, """Test 2: (parse("?") == {}) (5 points)""")
            self.assertEqual(parse("?a="),  {"a": ""}, """Test 3: (parse("?a=") == {'a':''}) (5 points)""")

    myTests().main()

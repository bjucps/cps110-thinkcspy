.. qnum::
   :prefix: quiz-4
   :start: 1

Code Quiz 4
===========


.. actex:: ac_quiz4-1
    :autograde: unittest
    :timelimit: 1000

    **Part 1 (30 points)**

    Create a class named ``Product`` that contains three instance variables: partNo, description, and quantity. Define a
    constructor that takes three parameters and uses it to initialize the instance variables. Also, override the
    ``__str__`` method so that printing a Product object yields text formatted according to the following template::

        Product PART_NO: DESCRIPTION (QUANTITY)

    Test with the following lines of code::
    
        p1 = Product(123, 'Apple juice', 3)
        print(str(p1))
        
    This should produce the output::
    
        Product 123: Apple juice (3)

    **Part 2 (10 points)**

    Create a second class named ``ProductList``. It should have an instance variable that holds a list of Product objects.

    Define a ProductList method named add that takes a Product object as a parameter and adds it to the collection.

    Define a ProductList method named getProducts that returns a string containing all the items in the list, formatted like this::

        / Product 301: Frying Pan (10) / Product 101: Baby Ruth (50) / Product 201: Pencil (25) /

    Note that the order in which the products are displayed should be the order in which they were added.

    Test with the following lines of code::

        pl = ProductList()
        pl.add(Product(301, 'Frying Pan', 10))
        pl.add(Product(101, 'Baby Ruth', 50))
        pl.add(Product(201, 'Pencil', 25))
        print(pl.getProducts())

    This should produce a line of output, formatted as shown above.

    **Part 3 (10 points)**

    Add a method named ``find`` to the ProductList class. It should take a part number, search the list to see if the
    product with that part number is present. If the product is present, it should return the Product object; otherwise,
    it should return **None**. 

    For example::

        print(str(pl.find(101)))

    should display::

        Product 101: Baby Ruth (50)

    ~~~~

    ====

    from unittest.gui import TestCaseGui

    class myTests(TestCaseGui):
        def test_15_Product(self):

            p1 = Product(123, 'Apple juice', 3)
            p2  = Product(42, "Wat", 99)
            self.assertEqual(p1.partNo, 123, "test_15_Product: p1.partNo == 123")
            self.assertEqual(p1.description, 'Apple juice', "test_15_Product: p1.description == 'Apple juice'")
            self.assertEqual(p1.quantity, 3, "test_15_Product: p1.quantity == 3")


            self.assertEqual(p2.partNo, 42, "test_15_Product: p2.partNo == 42")
            self.assertEqual(p2.description, "Wat", "test_15_Product: p2.description == Wat")
            self.assertEqual(p2.quantity, 99, "test_15_Product: p2.quantity == 99")

        def test_15_Product_str(self):

            p1 = Product(123, 'Apple juice', 3)
            p2  = Product(42, "Wat", 99)

            self.assertEqual(str(p1), "Product 123: Apple juice (3)", "test_15_Product_str: Apple juice (3)")
            self.assertEqual(str(p2), "Product 42: Wat (99)", "test_15_Product_str:Wat (99)")

        def test_10_getProducts(self):

            pl = ProductList()
            pl.add(Product(301, 'Frying Pan', 10))
            pl.add(Product(101, 'Baby Ruth', 50))
            pl.add(Product(201, 'Pencil', 25))

            products1 = pl.getProducts()

            pl2 = ProductList()
            pl2.add(Product(97, "Foo", 1000))
            pl2.add(Product(99, "Bar", 2000))
            pl2.add(Product(98, "Baz", 3000))
            pl2.add(Product(94, "Wat", 2500))
            pl2.add(Product(101, "Zoomp", 3100))
            products2 = pl2.getProducts()

            self.assertEqual(products1, '/ Product 301: Frying Pan (10) / Product 101: Baby Ruth (50) / Product 201: Pencil (25) /', "test_10_getProducts (1)")

            self.assertEqual(products2, "/ Product 97: Foo (1000) / Product 99: Bar (2000) / Product 98: Baz (3000) / Product 94: Wat (2500) / Product 101: Zoomp (3100) /", "test_10_getProducts (2)")


        def test_10_find(self):

            pl = ProductList()
            pl.add(Product(301, 'Frying Pan', 10))
            pl.add(Product(101, 'Baby Ruth', 50))
            pl.add(Product(201, 'Pencil', 25))

            p = pl.find(101)
            self.assertEqual(p.partNo, 101, "test_10_find: p.partNo == 101")
            self.assertEqual(p.description, 'Baby Ruth', "test_10_find: p.description == 'Baby Ruth'")

            p = pl.find(102)
            self.assertEqual(p, None, "test_10_find: p is None")


    myTests().main()

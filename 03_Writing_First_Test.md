# Writing Your First Unit Test
By now, you are probably eager to start writing your first unit test. Perhaps you have written tests before but are looking for a refresher in how to write good, concise unit tests. Whatever your Python or testing background, let's start at the beginning with some simple tests for a straightforward application. The examples first show you how to structure your test into a class with the correct naming conventions. Further on in this lesson, you are simply shown snippets of test methods, which you are expected to use with a proper test class.

One of the classic examples for demonstrating unit testing is a small calculator program. Python actually includes a lot of basic math functionality in the standard library. But what if you wrapped that into a simple-to-use command line application that could perform some simple calculations? This first scenario demonstrates how to implement the calculate class of the application example from earlier. Start with the add method, which looks something like this.

```python

class Calculate(object):
    def add(self, x, y):
        return x + y

if __name__ == '__main__':
    calc = Calculate()
    result = calc.add(2, 2)
    print result
  ```
   
   Clearly, this is a very simple class that is just making use of Python's built-in math function for adding and making it into a method you can call in your code. Save this code to a file named calculate.py, then execute this and see the result, like so.
    
    ```
    $ python calculate.py
    4
    ```
   
   # CHECKING VALUES WITH THE ASSERTEQUALS METHOD
You have some working code, so why not write the tests to prove it and look into what could go wrong if the code is used in ways you didn't foresee? Try writing a test that checks to see that if you pass in the two numbers as 2, then you get the result as 4. Using the standard Python library, you can import the unittest package. This provides useful methods to make different kinds of assertions (for instance, checking whether something meets some condition) on your method. One of those assertions you can use is the assertEqual method. This method allows you to pass in two values and check whether they are equal.

Create a test file called calculate_test.py, following the standard naming conventions of using the class name under test and appending with _test.

```python

import unittest
from app.calculate import Calculate


class TestCalculate(unittest.TestCase):
    def setUp(self):
        self.calc = Calculate()

    def test_add_method_returns_correct_result(self):
        self.assertEqual(4, self.calc.add(2,2))


if __name__ == '__main__':
    unittest.main()
```

A line-by-line examination shows that this example first imports the functionality you need from Python’s unittest module. You are also importing your own class, Calculate, so that you can test its methods. You do this in the setUp method, which is executed before each test, so that you need define your instance only once and have it created before each test. Then you can write your test and again the standard is to append your test name with append_test and explain what the test is doing briefly in the rest of the name. Here you are checking if the add method returns the correct result. To do this, you make use of the assertEqual method provided by the imported unittest module. This checks if the first argument is equal to the second. In this example, you are checking whether 4 is equal to the result of calling your add method on 2 and 2. In this case, the test passes as your code works and displays the following result in the terminal.


```
$ python test/calculate_test.py
.
----------------------------------------------------------------------
Ran 1 test in 0.000s
OK
```

This shows you that your test ran okay, and you ran only the one test. What if things go wrong? You can simulate that by breaking the test. Change test_add_method_returns_correct_result to assert that 2 add 3 equals 4, then you should see a failing test.

```python
import unittest
from app.calculate import Calculate


class TestCalculate(unittest.TestCase):
    ...
    def test_add_method_returns_correct_result(self):
        self.assertEqual(4, self.calc.add(2,3))
    ...

```

Running the python test

```
$ python test/calculate_test.py
F
======================================================================
FAIL: test_add_method_returns_correct_result (__main__.TestCalculate)
----------------------------------------------------------------------
Traceback (most recent call last):
  File  "/Users/user/workspace/python_testing/test/calculate_test.py", line 12, in test_add_method_returns_correct_result
    self.assertEqual(4, self.calc.add(2,3))
AssertionError: 4 != 5
----------------------------------------------------------------------
Ran 1 test in 0.000s
FAILED (failures=1)
```
You can see that the unittest module provides great feedback as to what went wrong and where. You can easily go back and fix the test. Of course, a real failure would usually be caused by your code not meeting your expectation and producing the wrong result. In that case, you would need to go in and fix your code. There you have it. You've written your first, simple unit test.






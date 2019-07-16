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


# Another Easy Example in Python Unit Testing

# unittest module
In Python we have unittest module to help us.

# Factorial code
In this example we will write a file factorial.py.

```python
import sys

def fact(n):
    """
    Factorial function

    :arg n: Number
    :returns: factorial of n

    """
    if n == 0:
        return 1
    return n * fact(n -1)

def div(n):
    """
    Just divide
    """
    res = 10 / n
    return res


def main(n):
    res = fact(n)
    print(res)

if __name__ == '__main__':
    if len(sys.argv) > 1:
        main(int(sys.argv[1]))
```
Output
```
$ python factorial.py 5
```
# Which function to test ?
As you can see fact(n) is function which is doing all calculations, so we should test that at least.

# Our first test case
Now we will write our first test case.

```python
import unittest
from factorial import fact

class TestFactorial(unittest.TestCase):
    """
    Our basic test class
    """

    def test_fact(self):
        """
        The actual test.
        Any method which starts with ``test_`` will considered as a test case.
        """
        res = fact(5)
        self.assertEqual(res, 120)


if __name__ == '__main__':
    unittest.main()
```
> Running the test:

```
$ python factorial_test.py
.
----------------------------------------------------------------------
Ran 1 test in 0.000s

OK
```
# Description
We are importing unittest module first and then the required functions which we want to test.

A testcase is created by subclassing unittest.TestCase.

Now open the test file and change 120 to 121 and see what happens.

# Different assert statements

![image](https://user-images.githubusercontent.com/47218880/61316151-f443f100-a7c5-11e9-9581-16fa69c39680.png)

This section provides a quick guide to all the different methods available in the unit test package. For each one, a description of its uage and an example are provided. All methods that take an optional argument, msg=None, can be provided a custom message that is displayed on failure. 

### **assertEqual(x, y, msg=None)**
This method checks to see whether argurment x equals arugment y. Under the covers, this method is performing the check using the == definition for the objects. 

```python
def test_assert_equal(self):
    self.assertEqual(1, 1)
```

### **assertAlmostEqual(x, y, places=None, msg=None, delta=None)**
On first glance, this method may seem a little strange but in context becomes useful. The method is basically useful around testing calculations when you want a result to be within a certain amount of places to the expected, or within a certain delta.

```python
def test_assert_almost_equal_delta_0_5(self):
    self.assertAlmostEqual(1, 1.2, delta=0.5)

def test_assert_almost_equal_places(self):
    self.assertAlmostEqual(1, 1.00001, places=4)
```
### **assertRaises(exception, method, arguments, msg=None)**
Given a method and set of arguments to that method, does it raise the exception? Arguments must match the signature of the method or syntax error is raised. Arguments are passed as comma-separated lists, not as part of the method call, as shown in the following example:

```python
def test_assert_raises(self):
    self.assertRaises(ValueError, int, "a")

def test_assert_raises_alternative(self):
    with self.assertRaises(AttributeError):
        [].get
```
### **assertDictContainsSubset(expected, actual, msg=None)**
Use this method to check whether actual contains expected. It’s useful for checking that
part of a dictionary is present in the result, when you are expecting other things to be there
also. For example, a large dictionary may be returned and you need to test that only a couple
of entries are present.

```python
def test_assert_dict_contains_subset(self):
    expected = {'a': 'b'}
    actual = {'a': 'b', 'c': 'd', 'e': 'f'}
    self.assertDictContainsSubset(expected, actual)
```

### **assertDictEqual(d1, d2, msg=None)**
This method asserts that two dictionaries contain exactly the same key value pairs. For this
test to pass, the two dictionaries must be exactly the same, but not necessarily in the same
order.

```python
def test_assert_dict_equal(self):
    expected = {'a': 'b', 'c': 'd'}
    actual = {'c': 'd', 'a': 'b'}
    self.assertDictEqual(expected, actual)
```
### **assertTrue(expr, msg=None)**
Use this method to check the truth value of an expression or result. This method can be
useful and has a few interesting caveats. This is because Python’s implicit truth behavior,
such as numeric values like 0 and 1 have truth-value of False and True, respectively.
Table 2-1 lists some implied truths along with test examples, but more information can be
found in the Python documentation.

```python
def test_assert_true(self):
    self.assertTrue(1)
    self.assertTrue("Hello, World")
```

### **assertFalse(expr, msg=None)**
This method is the inverse of assertTrue and is used for checking whether the expression
or result under the test is False.

```python
def test_assert_false(self):
    self.assertFalse(0)
    self.assertFalse("")
```

### **assertGreater(a, b, msg=None)**
This method allows you to check whether one value is greater than the other. It is essentially
a helper method that wraps up the use of assertTrue on the expression a > b. It displays
a helpful message by default when the value is not greater.

```python
def test_assert_greater(self):
    self.assertGreater(2, 1)
```
### **assertGreaterEqual(a, b, msg=None)**
You use this method to check whether one value is greater than or equal to another value.
Essentially, this wrapper is asserting True on a >= b. The assertion also gives a nicer message if the expectation is not met.

```python
def test_assert_greater_equal(self):
    self.assertGreaterEqual(2, 2)
```

### **assertIn(member, container, msg=None)**
With this method, you can check whether a value is in a container (hashable) such as a list or
tuple. This method is useful when you don’t care what the other values are, you just wish to
check that a certain value(s) is in the container.

```python
def test_assert_in(self):
    self.assertIn(1, [1,2,3,4,5])
```
### **assertIs(expr1, expr2)**
Use this method to check that expr1 and expr2 are identical. That is to say they are the
same object. For example, the python code [] is [] would return False, as the creation
of each list is a separate object.

```python
def test_assert_is(self):
    self.assertIs("a", "a")
```
### **assertIsInstance(obj, class, msg=None)**
This method asserts that an object is an instance of a specified class. This is useful for checking that the return type of your method is as expected (for instance, if you wish to check that
a value is a type of int):

```python
def test_assert_is_instance(self):
    self.assertIsInstance(1, int)
```

### **assertNotIsInstance(obj, class, msg=None)**
This reverse of assertIsInstance provides an easy way to assert that the object is not a
type of the class.

```python
def test_assert_is_not_instance(self):
    self.assertNotIsInstance(1, str)
```

### **assertIsNone(obj, msg=None)**
Use this to easily check if a value is None. This method provides a useful standard message if
not None.

```python
def test_assert_is_none(self):
    self.assertIsNone(None)
```

### **assertIsNot(expr1, expr2, msg=None)**
Using this method, you can check that expr1 is not the same as expr2. This is to say that
expr1 is not the same object as expr2.

```python
def test_assert_is_not(self):
    self.assertIsNot([], [])
```
### **assertIsNotNone(obj, msg=None)**
This method checks that the value provided is not None. This is useful for checking that your
method returns an actual value, rather than nothing.

```python
def test_assert_is_not_none(self):
    self.assertIsNotNone(1)
```
### **assertLess(a, b, msg=None)**
This method checks that the value a is less than the value b. This is a wrapper method for
assertTrue on a < b.

```python
def test_assert_less(self):
    self.assertLess(1, 2)
```

### **assertLessEqual(a, b, msg=None)**
This method checks that the value a is less than or equal to the value b. This is a wrapper
method for assertTrue on a <= b.

```python
def test_assert_less_equal(self):
    self.assertLessEqual(2, 2)
```
### **assertItemsEqual(a, b, msg=None)**
This assertion is perfect for testing whether two lists are equal. Lists are unordered; therefore, assertEqual on a list can produce intermittent failing tests as the order of the lists
may change when running the tests. This can produce a failing test when in fact the two lists
have the same contents and are equal.

```python
def test_assert_items_equal(self):
    self.assertItemsEqual([1,2,3], [3,1,2])
```

### **assertRaises(excClass, callableObj, *args, **kwargs, msg=None)**
This assertion is used to check that under certain conditions exceptions are raised. You pass
in the exception you expect, the callable that will raise the exception and any arguments to
that callable. In the earlier example, this pops the first item from an empty list and results in
an IndexError.

```python
def test_assert_raises(self):
    self.assertRaises(IndexError, [].pop, 0)
```


# Testing exceptions
If we call div(0) in factorial.py , we can see if raises an exception.

We can also test these exceptions, like:

> self.assertRaises(ZeroDivisionError, div, 0)

Full code

```python
import unittest
from factorial import fact, div

class TestFactorial(unittest.TestCase):
    """
    Our basic test class
    """

    def test_fact(self):
        """
        The actual test.
        Any method which starts with ``test_`` will considered as a test case.
        """
        res = fact(5)
        self.assertEqual(res, 120)

    def test_error(self):
        """
        To test exception raise due to run time error
        """
        self.assertRaises(ZeroDivisionError, div, 0)



if __name__ == '__main__':
    unittest.main()
```

## mounttab.py

Here we have only one function mount_details() doing the parsing and printing mount details.

```python
import os


def mount_details():
    """
    Prints the mount details
    """
    if os.path.exists('/proc/mounts'):
        fd = open('/proc/mounts')
        for line in fd:
            line = line.strip()
            words = line.split()
            print()'%s on %s type %s' % (words[0],words[1],words[2]), end=' ')
            if len(words) > 5:
                print('(%s)' % ' '.join(words[3:-2]))
            else:
                print('')


if __name__ == '__main__':
    mount_details()
```
## After refactoring
Now we refactored the code and have one new function parse_mounts which we can test easily.

```python
import os

def parse_mounts():
    """
    It parses /proc/mounts and returns a list of tuples
    """
    result = []
    if os.path.exists('/proc/mounts'):
        fd = open('/proc/mounts')
        for line in fd:
            line = line.strip()
            words = line.split()
            if len(words) > 5:
                res = (words[0],words[1],words[2], '(%s)' % ' '.join(words[3:-2]))
            else:
               res = (words[0],words[1],words[2])
            result.append(res)
    return result

def mount_details():
    """
    Prints the mount details
    """
    result = parse_mounts()
    for line in result:
        if len(line) == 4:
            print('%s on %s type %s %s' % line)
        else:
            print('%s on %s type %s' % line)


if __name__ == '__main__':
    mount_details()
```
and the test code for the same.

```python
#!/usr/bin/env python
import unittest
from mounttab2 import parse_mounts

class TestMount(unittest.TestCase):
    """
    Our basic test class
    """

    def test_parsemount(self):
        """
        The actual test.
        Any method which starts with ``test_`` will considered as a test case.
        """
        result = parse_mounts()
        self.assertIsInstance(result, list)
        self.assertIsInstance(result[0], tuple)

    def test_rootext4(self):
        """
        Test to find root filesystem
        """
        result = parse_mounts()
        for line in result:
            if line[1] == '/' and line[2] != 'rootfs':
                self.assertEqual(line[2], 'ext4')


if __name__ == '__main__':
    unittest.main()
```

```
$ python mounttest.py
..
----------------------------------------------------------------------
Ran 2 tests in 0.001s

OK
```
## Test coverage
Test coverage is a simple way to find untested parts of a codebase. It does not tell you how good your tests are.

In Python we already have a nice coverage tool to help us. You can install it in Fedora

> # yum install python-coverage

Or using pip.

> $ pip install coverage

# Coverage Example
```
$ coverage -x mounttest.py
<OUTPUT snipped>

$ coverage -rm
Name        Stmts   Miss  Cover   Missing
-----------------------------------------
mounttab2      21      7    67%   16, 24-29, 33
mounttest      14      0   100%
-----------------------------------------
TOTAL          35      7    80%
```

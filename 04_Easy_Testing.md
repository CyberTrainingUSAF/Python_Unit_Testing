
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





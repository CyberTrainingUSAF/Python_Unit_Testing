
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

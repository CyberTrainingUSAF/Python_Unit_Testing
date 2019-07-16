# Asserting the basics
The basic concept of an automated unittest test case is to instantiate part of our code, subject it to operations, and verify certain results using assertions.

If the results are as expected, unittest counts it as a test success
If the results don't match, an exception is thrown and unittest counts it as a test failure
## Getting ready
Unittest was added to Python's standard batteries included library suite and doesn't require any extra installation.

## How to do it...
With these steps, we will code a simple program and then write some automated tests using unittest:

Create a new file called recipe1.py in which to put all of this recipe's code. Pick a class to test. This is known as the class under test. For this recipe, we'll pick a class that uses a simplistic Roman numeral converter:

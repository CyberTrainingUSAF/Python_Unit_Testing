# Implementing Unittest to develop basic tests

In this Lesson, we will cover the following techniques:

- Asserting the basics
- Setting up and tearing down a test harness
- Running test cases from the command line
- Running a subset of test case methods
- Chaining together a suite of tests
- Defining test suites inside the test module
- Retooling old test code to run inside unittest
- Breaking down obscure tests into simple ones
- Testing the edges
- Testing corner cases by iteration

# Introduction
Testing has always been a part of software development. However, the world was introduced to a new concept called automated testing when Kent Beck and Erich Gamma introduced JUnit for Java development (http://junit.org). It was based on Kent's earlier work with Smalltalk and automated testing. Currently, automated testing has become a well-accepted concept in the software industry.

A Python version, originally dubbed PyUnit, was created in 1999 and added to Python's standard set of libraries later in 2001 in Python 2.1. Currently, the PyUnit library is available for both versions of Python, that is, 2.7 (https://docs.python.org/2.7/library/unittest.html) and 3.x (https://docs.python.org/3.6/library/unittest.html). Since then, the Python community has referred to it as unittest, the name of the library imported into the test code.

Unittest is the foundation of automated testing in the Python world. In this chapter, we will explore the basics of testing and asserting code functionality, building suites of tests, test situations to avoid, and finally testing edges and corner cases.

For all the recipes in these lessons, we will use virtualenv (https://pypi.python.org/pypi/virtualenv) to create a controlled Python runtime environment. Unittest is part of the standard library, which requires no extra installation steps. But in later lessons, using virtualenv will allow us to conveniently install other test tools, without cluttering up our default Python installation. The steps to install virtualenv are as follows:

To install virtualenv, either download it from the site mentioned previously or if you have Easy Install, just type: easy_install virtualenv. You can also use pip install virtualenv as well.
For some systems, you may need to install it either as root or by using sudo.
After installing virtualenv, use it to create a clean environment named ptc (an abbreviation used for Python Testing Cookbook) by using --no-site-packages.
Activate the virtual Python environment. This can vary, depending on which shell you are using. Take a look at this screenshot:  
![image](https://user-images.githubusercontent.com/47218880/61306435-39f6be80-a7b2-11e9-9729-c36bd6b1a8a3.png)  
For the Windows platform, you can either select the folder where you want to create the ptc folder or you can directly get it created in your desired drive. Look at this screenshot:

![image](https://user-images.githubusercontent.com/47218880/61307084-4a5b6900-a7b3-11e9-98c3-1308292cbd3e.png)

Finally, verify that the environment is active by checking the path of pip.



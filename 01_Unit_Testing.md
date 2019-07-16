# What is Unit Testing?

In unit testing, you look to cover the program’s functionality at its most basic level. Test each individual unit of code, typically a method, in isolation to see if given certain conditions it responds in the expected way. Breaking testing down to this level gives you confidence that each part of the application will behave as expected and enables you to cover edge cases where the unexpected happens and deal with them accordingly.

 Example program structure showing the classes and methods. The methods are the “units” you will test.
 
 ![image](https://user-images.githubusercontent.com/47218880/61303667-87bcf800-a7ad-11e9-9450-c4647ca4ad12.png)
 
In the preceding example, the methods highlighted are the individual units of this application that you need to test. If you know that each of the calculate class’s methods work as expected, you can be confident that the calculate feature of your application has been delivered to your expectations.

For instance, you may wish to test whether the result of calling the method with two numbers actually adds them together to produce the correct sum. Breaking your code down into these units makes the testing process easier. When dealing with a small unit of an application, you have a clear understanding of its responsibilities and the things that can go wrong with the specific piece of code, thus enabling you to cover the unit with the appropriate tests.

Furthermore, when testing in this manner it usually becomes obvious if you have broken down the code into a good-sized unit. If you have to write many different tests to cover all the different possibilities that the method can go through, your method may be too large and you should consider refactoring it into two or more methods with fine-grained responsibilities. Conversely, there may be cases where your method is too simple and could be combined with some other functionality to create a more useful method. As a programmer with experience, you should start to get a feel for a good-sized method. Ten lines is often a good rule of thumb to follow. There are, of course, plenty of cases where you need more or less than this arbitrary number of lines, and as a programmer your common sense should guide you to provide the most readable code.

The tests that you write are a story that explains your code. What would you want to read or see when first reading through the code and trying to understand what it does? Clear, concise naming conventions of variables, class names, filenames, and tests can all help to make your code clear and easy to maintain for other people.

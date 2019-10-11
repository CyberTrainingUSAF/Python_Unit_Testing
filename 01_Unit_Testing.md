
---

# Brief History Of Unit Testing

Testing your code hasn't always been around. There were developers out there that tested their code as it was written but it wasn't common practice. You mainly had people testing code if there was apparent danger or lives at stake if something failed. A major contributing factor to this is speed. Simple programs used to take long amounts of time to compile, minutes or even hours on bigger projects. 

Computers started to become faster so cycle times in development started to shrink. People started to make small changes to their code or projects and test on those small changes. Computers are more powerful so in turn software is more complex. 

Testing forces developers into a specific way of thinking. You originally write your code to cover that one case that you're thinking about but then as your start to write test code you realize that you have other scenarios that can arise. This is where Test Driven Development (TDD) comes into play. A big mistake of writing code is to write a bunch of code and test it at the end. You aren't fresh on the code you wrote a few days ago and the thought process you made while writing the code could be lost to you.

There is often a QA person who's sole job is to write tests and constantly test the application. From TDD we have Behavior Driven Development (BDD) which utilizes the agile methodology. This method takes unit testing one step further and looks to test the application's behavior in terms of functionality being delivered. The benefit of this approach is that non-technical team members, such as a scrum master or a product owner, can write feature files, and then the developer or QA can implement the code underneath.

# What is Unit Testing?

In unit testing, you look to cover the program’s functionality at its most basic level. Test each individual unit of code, typically a method, in isolation to see if given certain conditions it responds in the expected way. Breaking testing down to this level gives you confidence that each part of the application will behave as expected and enables you to cover edge cases where the unexpected happens and deal with them accordingly.

 Example program structure showing the classes and methods. The methods are the “units” you will test.
 
 ![image](https://user-images.githubusercontent.com/47218880/61303667-87bcf800-a7ad-11e9-9450-c4647ca4ad12.png)
 
In the preceding example, the methods highlighted are the individual units of this application that you need to test. If you know that each of the calculate class’s methods work as expected, you can be confident that the calculate feature of your application has been delivered to your expectations.

For instance, you may wish to test whether the result of calling the method with two numbers actually adds them together to produce the correct sum. Breaking your code down into these units makes the testing process easier. When dealing with a small unit of an application, you have a clear understanding of its responsibilities and the things that can go wrong with the specific piece of code, thus enabling you to cover the unit with the appropriate tests.

Furthermore, when testing in this manner it usually becomes obvious if you have broken down the code into a good-sized unit. If you have to write many different tests to cover all the different possibilities that the method can go through, your method may be too large and you should consider refactoring it into two or more methods with fine-grained responsibilities. Conversely, there may be cases where your method is too simple and could be combined with some other functionality to create a more useful method. As a programmer with experience, you should start to get a feel for a good-sized method. Ten lines is often a good rule of thumb to follow. There are, of course, plenty of cases where you need more or less than this arbitrary number of lines, and as a programmer your common sense should guide you to provide the most readable code.

The tests that you write are a story that explains your code. What would you want to read or see when first reading through the code and trying to understand what it does? Clear, concise naming conventions of variables, class names, filenames, and tests can all help to make your code clear and easy to maintain for other people.

# What Should You Test?
A question that many developers ask especially when first starting out is, what should I test? This is an interesting question and also a fair one, as the programs that are being built now are often vast with many complexities. However, unit testing makes the task easier as the whole idea is to focus on the smallest units of code rather than thinking about how to test the large program you are putting together as a whole. Before you write any code you give thought to the kind of tests you will be writing to check the methods will work as expected. As you write more and more unit tests you will gain experience in what works well and what perhaps causes you issues later down the line. For example, a frequent mistake of inexperienced developers is writing very brittle test suites. This means that as code evolves the tests break for reasons other than the functionality changing. The tests are often checking elements of the code or data to too fine a granularity, meaning that as data changes (and not your functionality, which is what you are really testing), the tests fail and you need to go and fix it. Making your tests as flexible as possible while still testing your functionality is the best way to defend against this brittleness.

Another reason to test comes from the process of finding bugs whether in a production environment, the test environment, or while testing your program locally. Whenever you find a bug that affects your program that requires a code change to fix, you should write a test to cover that scenario. By doing this, you ensure that you have covered the defect that caused the problem and with test in place the bug should not reoccur in the future. By adding this layer of defense every time you find a bug (hopefully, not very often) you ensure that your code is more robust in the future as more functionality is added.

|[Next Topic](02_Develop_Basic_Tests.md)|
|---|
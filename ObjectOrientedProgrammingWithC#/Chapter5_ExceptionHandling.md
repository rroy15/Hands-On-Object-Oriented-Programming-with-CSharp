# Chapter 5

## Exception Handling - Let's try to understand

Lets first try to analyze the words “Exception” and “Handling”. We all know exception is something that doesn’t happen normally, its something unusual. It could be both good and bad. For example sometimes we say “This person is exceptionally talented”, here we mean that this person that we are talking about has some talent which no other person has. Or its a very rare talent that is found in very less people. Sometimes we also say “This boy does always good in the exam, but this time is an exception!”. Here we are using exception in a negative way. But the word exception doesn’t have any positive or negative meaning by itself. Exception means something not normal or unusual. So what does exception has to do in programming! In programming there could be some cases where the computer/software is not working as its suppose to work and that is what we call **exception**. Why we call it exception? Because it's very normal that the computer or the software will only do those things which you instructed. If you have instructed something and the computer is doing something different or fail to do what you have instructed then it means it's an unusual thing. And that is **exception**.

Now we also know another term “Error”. Is error a synonym of Exception? No its not. These terminologies are very important in software development. So we have to very clearly understand what means what. Error and Exception is not same, by error we mean when your software doesn’t run. Or more specifically we can say when your code doesn’t build, there is an error in the code. Where as an exception happens on run time. The easiest way to distinguish them is if your code doesn’t compile/build then there is some error in your code. If your code compiles/builds but when you run it you get some unusual behavior then its an exception.

Now let's talk about the other word “Handling”. Do we really need to discuss about this word? I mean, isn’t it very expressive by itself? Anyways let's do it if by any chance it's not making any sense to you. “Handling” means to handle anything. It means to control something. So now if we analyze the two words side by side, we can easily understand that the “Exception Handling” mens handling/controlling/supervising the exceptions that occurs while you run the program.

## Why we need exception handling in programming

You wrote some code, it's suppose to do something. Something you instructed, but there is a situation that the software can't execute that task. Because its not possible by the software.

Suppose you instructed the software to read a file and collect data and store it in a database. But the software can't find the file where you told the file should be. There could be many reasons that the file is not there! Now what will your software do? Its not smart enough that it will handle the situation automatically. We the human, the software developers has to instruct it how to handle the situation. But how we software developers will know what the software is facing now?

The software will let us know by passing a message (which we call exception in programming). But what should it say to us. "Help! Help!" won't make our life easy. We need more information about the situation, so that we can guide the computer to work accordingly. So the .Net framework has created some very common exceptions which occurs very often. If the problem that the software is facing has an predefined exception, it will throw that. For example, if there is a case where the program is trying to divide a number by zero, but mathematically its not possible! So the program is in big trouble. Its confused and helpless. Its so panicked that it decides to suicide! But the .Net framework stops it and says, "ask for help Mr.Program", throw this DivideByZeroException, to your master, he/she will help you." Yeah, this speech is imaginary, the computer doesn't talk like that, I just said it this way to make you understand. Anyways the program will then throw the DivideByZeroException. And that is how we will know what exception we need to handle. So that is why we need exceptions in programming. And that is why its super important that you know about exception handling.

## Exception handling in C# Programming

.NET framework and C# programming language has developed some powerful ways to handle these exceptions. There is a class in .NET under system namespace. “System.Exceptions” has some functionality which will help you to manage the exceptions that will occur while run time and protect your program from crash. Crash!! Yes, if you didn’t handle exceptions properly in your code, your software will crash. That is why “exception handling” is very important in software development.

Now you might ask, but how can i handle exceptions in my code? Exception is something unexpected, how would i know which exception will occur in my code and cause the program to crash? It's a very good question. And i am sure, this question was also asked or at least thought about when the language developers were designing the language. That is why they came up with a solution for that. .Net created a very beautiful mechanism to handle exceptions.

### Basics Of Exception Handling

The exception handling in C# is achieved/done mainly by 4 keywords. Try, Catch, Throw and Finally. We will talk about these keywords in detail individually later. But just to give you basic idea of what are meant by those keywords let's discuss in brief for now.

When you are not sure of the expected behavior of a code or their is a possibility of an exception, you should put that code in try block. Because try block will throw an exception if any exception happens inside the code of that block. If no exception occurs, the try block will act like it doesn’t exists. If any exceptions in the try block it throws an exception. This is the main task of try block, throwing exceptions.

Catch block is executed when an exception is caught. The exceptions thrown by try block will be handled by the following catch block. There could be multiple catch blocks for a try block. Each catch block can be dedicated for particular exception. For example, in our schools, we have different teachers expertise in different subjects. When ever its time to choose a teacher for a class for a particular subject, we chose that teacher who is the expert in that topic. Same there could be different catch block for different types of exceptions.

Throw is used when you manually want to throw an exception. Why do you even want to throw an exception by yourself? Yes, there could be situations when you want to throw exceptions to control an specific kind of situations.

Finally is a block of code, that will be compulsorily executed. It doesn’t matter if the try threw any exception or not, finally block will be executed. This is mainly use to code some task which is essential to handle in any case.

### Lets see Try and Catch

Try and Catch are the most two important keywords for exception handling in C#. If you write a try block without an catch block doesn’t make any sense. Because if the try block throws an exception but if there is no catch block to handle it then what is the benefit. Whereas the catch block if depended on try block. Just catch block can’t exists if its not just before a try block. Let see how we can write a try-catch block:

Try{
	Int a = 5 / 0;
}
Catch(DivideByZeroException ex){
	Console.WriteLine(“You have divided by zero”);
}

We can also have more catch blocks for this try block.

Try{
	Int a = 5 / 0;
}
Catch(DivideByZeroException ex){
	Console.WriteLine(“You have divided by zero”);
}
Catch(Exception ex)
{
	Console.WriteLine(“Normal exception”);
}

### What will happen if you don’t handle exceptions

Is exceptions really important? Is it worth the time when you have tons of complexity in the logic. Yes, it is super important. Lets now analyze what will happen if you don’t take care of the exceptions. When an exception in triggered, if no code handles it, then the exception goes to the system runtime. And when the system runtime faces an exception, it just terminates the program. So, now you understand why you want to handle exceptions. If you fail to do it, your application might break down in the middle of running. I am sure you personally don’t like those programs which crashes while you are using it. So we have to be careful with it. Lets see an example what is done by the system runtime if the exception is not handled:

```csharp

Using system;

class LearnException {
    public static void Main()
    {
        int[] a = {1,2,3,4};

        for (int i=0; i<10; i++)
        {
            Console.Writeline(a[i]);
        }
    }
}

```

If we run this code, for the first 4 times it will run perfectly and print the number 1 to 4. But after that it will throw an exception of IndexOutOfRangeException. And the system runtime will terminate the program.

### Multiple Catch blocks

Its very normal that you might get different types of exceptions in one try block. But how can you handle it? Should you use the general exception to handle it? No, that is not a good idea. Because if you use general exception handing you might miss some of the important information about the exception. That is why dotnet has introduced multiple catch blocks for a try block. You can specify one catch block which will be called for one type of exception, and you can create other catch blocks just after one by one with different exception type. Only the particular catch block will be executed if it has a dedicate catch block. Lets see an example:

```csharp

using System;

class ManyCatchBlocks
{
    public static void Main()
    {
        try
        {
            Console.WriteLine("Here we will divide 5 by 0");
            var a = 5/0;
        }
        catch(IndexOutOfRangeException ex)
        {
            Console.WriteLine("Index is out of range " + ex);
        }
        catch(DivideByZeroException ex)
        {
            Console.WriteLine("You have divided by zero, which is not correct!");
        }
    }
}

```

Now you might ask, ok you told we shouldn't use General Exception handler. But why is that? I mean yes we might miss some information but my system is not crashing! Isn't it better! Actually, answer to this question is not straight forward. It may vary system to system, but let me tell you why you want the system to crash sometimes? Suppose you have a system where you deal with very complex and sensitive data. In such a system, when an exception happens it might be risky to allow the customer to use the software. They could do some serious damage to the data, as that exception is not handle properly. But yes, if you think your system will be fine if you allow the user to continue even if they got an unknown exception you can use general catch block. Now let me show you how you can do that. If you want a catch block to catch any kind of exception, whether its system exception or code level exception it doesn't matter, the catch block should catch it. Then write a catch block without any argument.

```csharp
using System;

namespace ExceptionCode
{
	class Program
	{
		static void Main(string[] args)
		{
			try
			{
				var a = 0;
				var b = 5;
				var c = b / a;
			}
			catch (IndexOutOfRangeException ex)
			{
				Console.WriteLine("Index out of range " + ex);
			}
			catch
            {
                Console.WriteLine("I will catch you exception! You can't hide from me!");
            }

            Console.WriteLine("Hello");
            Console.ReadKey();
        }
    }
}

```

But keep in mind, this has to be the last catch block. Otherwise there will be a runtime error that catch block can't be after the general catch block.

### What is Throw keyword used for

This is a wierd world. Sometimes in your own program you have to create exceptions by yourself! No, not to take revenge on the user, but for the sake of your application. Sometimes there are situations, when you need to throw an exception to bypass some difficulty or may be to log something or maybe to just redirect the flow of the software. And don't worry, by doing it you are not becoming the bad guy. You are actually the superman who is saving the program from trouble. But how can you create an exception. To do that C# has a keyword called "Throw". This keyword will help you to create an instance of a type of exception and throw it. Let me show you an example of throw:

```csharp

using System;

namespace ExceptionCode
{
	class Program
	{
		static void Main(string[] args)
		{
			try
			{
				Console.WriteLine("You are the boss!");
				throw new DivideByZeroException();
			}
			catch (IndexOutOfRangeException ex)
			{
				Console.WriteLine("Index out of range " + ex);
			}
			catch (DivideByZeroException ex)
			{
				Console.WriteLine("Divide by zero " + ex);
			}
			catch
			{
				Console.WriteLine("I will catch you exception! You can't hide from me!");
			}

			Console.WriteLine("See, i told you!");
			Console.ReadKey();
		}
	}
}

```

So if you want or need to throw an exception because may be you want the upper layer catch block to handle it. You simple throw a new instance of an exception. This could be any kind of exception. It could be a system exception, it could be a self created exception. Just keep in mind that there is some catch block which will handle it.

1. Closest matching catch statement is checked
2. You should check the catch as early as possible otherwise the stack trace will be huge.
3. Custom exceptions for special cases and more precise

### Why we need exception

### How to handle exception using try and catch

### Multiple catch blocks

### General catch block

### Finally block; What does that do

When we say "Finally", we mean something that we where waiting for or something that is going conclude the process. Its almost same in exception handling. A "Finally" block is a block of code, which will be executed no matter what happens to the try or catch block. It doesn't matter what type of exceptions were thrown or wheter those were handled or not, the finally block will get executed. Now you may ask why do we need this finally block? If there is any exception in our program, we are handling it by the catch block! Can't we write the code there instead of finally block? Yes, you can but what happens if there was exception thrown, the catch block will not be triggered. It means the code inside the catch block will not get executed. That is why finally block is important. It doesn't matter if there was any exception or not, the finally block will run. Let me show you can example fo finally block:

```csharp
using System;

namespace ExceptionCode
{
	class Program
	{
		static void Main(string[] args)
		{


			try
			{
				int a = 0;
				int b = 5;
				int c = b / a;
			}
			catch (IndexOutOfRangeException ex)
			{
				Console.WriteLine("Index out of range " + ex);
			}
			catch (DivideByZeroException ex)
			{
				Console.WriteLine("Divide by zero " + ex);
			}
			catch
			{
				Console.WriteLine("I will catch you exception! You can't hide from me!");
			}

			finally
			{
				Console.WriteLine("I am the finally block i will run by hook or by crook!");
			}
		}
	}
}

```

An important use case of finally block could be when you open a database connection in the try block! You have to close it otherwise that connection will be open for the rest of the program and it will take a lot of resources. And not only that there are limited number of connections a database can make, so if you open one and don't close it, that connection string is wasted. So the best practice is to close the connection as soon as your work with the connection is complete. And finally block plays the best role here. It doesn't matter what will happen in try block, the finally block will close the connection.

```csharp
using System;

namespace ExceptionCode
{
	class Program
	{
		static void Main(string[] args)
		{


			try
			{
				// Step 1: Established database connection
				// Step 2: Do some activity in database
			}
			catch (IndexOutOfRangeException ex)
			{
				// Handle IndexOutOfRangeExceptions here
			}
			catch (DivideByZeroException ex)
			{
				// Handle DivideByZeroException here
			}
			catch
			{
				// Handle All other exception here
			}

			finally
			{
				// Close the database connection
            }

        }
    }
}

```

Finally block is not something that you must have to have to handle exceptions. But use it if you need it.

### Wy we want to throw exceptions

### Exception Class

Exception is noting but a class in c#. It has few properties and few methods. The main three properties are

- Message: This contains what is the exception about.
- StackTrace: This contains the method call stack information.
- TargetSite: This gives an object which contains the method where the exception happened.
- InnerException: This gives the instance of the exception which caused the exception.

One of the most popular method that this class has in **ToString()**. This method returns a string which contains information about the exception. Its easier to read and understand when it is represented in string format.

/// Example code goes here

### Some common exception classes

There are many exception classes available in .NET Framework. .NET Framework created those to make the developers life easy. Its provides specific information about the exceptions. Below some of the most common exception classes are shared.

- DivideByZeroException: This exception is thrown when any number is divided by zero.
- IndexOutOfRangeException: This exception is thrown when the application tries to use an index of an array which doesn't exist.
- InvalidCastException: This exception is thrown when trying to do some not valid casting.
- NullReferenceException: This exception is thrown when trying to use or access a null reference type.

/// NullRefException example

### User defined Exception

Sometimes there might be case where you think the pre-defined exceptions are not statisfying your condition. You might wish there could be a way where you can create your own exception and use it. Using something you created will surly make you more happy. Anyways, in C# there is actually a machanism that you an create your own custom exceptions. You can put what message is appropriate for that kind of exception. Lets see an example how to create and use custom exception below:

```csharp
using System;

namespace ExceptionCode
{

	class HelloException : Exception
	{
		public HelloException() { }
		public HelloException(string message) : base(message) { }
		public HelloException(string message, Exception inner) : base(message, inner) { }
	}

	class Program
	{
		static void Main(string[] args)
		{
			
			try
			{
				throw new HelloException("Hello is an exception!");
			}
			catch (HelloException ex)
			{
				Console.WriteLine("Exception Message:");
				Console.WriteLine(ex.Message);
			}

			Console.ReadKey();

		}
	}
}
```

So we can see from the above example that you just have to create a class that will extend the Exception class. This class should have 3 constructors, one shouldn't take any parameter, one should take a string and pass it to base. Another constructor should take a string and an Exception and pass it to the base.

Using a custom exception is like using any other built in exception provided .NET framework.

### Exception Filter

This feature isn't much old at the time I am writing this book. It was introduce in C# 6. The main benefit of this is you can catch more specific exception in a block. Lets see an example of Exception Filter:

```csharp

using System;

namespace ExceptionCode
{
	class Program
	{
		static void Main(string[] args)
		{

			int[] a = new int[] {1,2,3};

			try
			{
				Console.WriteLine(a[5]);
			}
			catch (IndexOutOfRangeException ex) when (ex.Message == "Test Message")
			{
				Console.WriteLine("Message:");
				Console.WriteLine("Test Message");
			}
			catch (IndexOutOfRangeException ex) when (ex.Message == "Index was outside the bounds of the array.")
			{
				Console.WriteLine("Message:");
				Console.WriteLine(ex.Message);
				Console.WriteLine("Stack Trace:");
				Console.WriteLine(ex.StackTrace);
				Console.WriteLine("String:");
				Console.WriteLine(ex.ToString());
			}

			Console.ReadKey();

		}
	}
}


```

To filter out exceptions you have to use the keyword "when" just next to the catch declaration line. So first any exception is thrown it will check what type of exception it is, in our example the exception type is "IndexOutOfRangeException" and then it will check what is the condition given in "when". The catch block which matches both the condition, will be executed.



### Exception Handling Best Practices

As you can see there are different ways you can handle exceptions. Sometimes you can throw exceptions, sometimes you can use finally block, sometimes multiple catch blocks. So there is chance to get confused at the beginning if you don't have enough experience in it. But thanks to the C# community, they have shared the best practices of Exception Handling with the world. Let go throw on some of them.

1. Use finally block to close/cleanup the dependent resources that could cause problem in the future.

2. Catch specific exception and handle it properly. Use multiple catch blocks if needed.

3. Create your own exceptions if needed and use it.

4. Handle exceptions as soon as possible.

5. Don't use general exception handler if you can handle using specific handler.

6. The exceptions messages should be very clear.
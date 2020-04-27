# Clean Code Developer Checklist
A developer checklist derived from the book Clean Code by Robert C Martin 

## Table of contents :bookmark_tabs:
  - [Naming things](#naming-things-u5272)
  - [Functions](#functions-microscope)
  - [Formatting](#formatting-rainbow)
  - [Objects and Data Structures](#objects-and-data-structures-two_men_holding_hands)
  - [Error handling](#error-handling-interrobang)
  - [Unit tests](#unit-tests-umbrella)
  - [Class](#class-school_satchel)
  - [Emergence](#emergence-green_book)
  - [Concurrency](#concurrency-arrows_clockwise)
  - [Code smells](#code-smells-speak_no_evil)

<br/>


## Naming things :u5272:

- [x] **Name should reveal intent**
  - It should tell you why it exists, what it does, and how it is used.
  - Name should depict the context.

- [x] **Avoid using abbreviations**
  - Use `hypotenuse` instead of `hp`.

- [x] **Do not encode name with data structure**
  - Use `accounts` instead of `accountList`.

- [x] **Do not use names which vary in small ways**
  - Find the difference between `ControllerForEfficientHandlingOfStrings` and `ControllerForEfficientStorageOfStrings` :dancers:

- [x] **Do not name variables just to satisfy the compiler**
  - Don't name something `name1` cause `name` is already taken.

- [x] **Avoid using noise words**
  - `ProductData` and `ProductInfo` kind of means the same thing.
  - Similarly words like `a`, `an`, `the` are also noise words.
  - Noise words are also **redundant**, use `name` instead of `nameString`.

- [x] **Distinguish names in such a way that the reader knows which one to call.**

- [x] **Use pronounceable names**

- [x] **Use searchable names**
  - Use constants instead of hard coding a value, `WORK_DAYS_PER_WEEK = 5` instead of just using 5.

- [x] **The length of a name should correspond to the size of its scope**
  - There can be a variable `i` inside a `for loop` but `i` should never be a `instance variable`.

- [x] **Classes and objects should have noun or noun phrase names.**
  - Avoid words like `Manager`, `Processor`, `Data`, or `Info` in the name of a class.
  - If your class name ends with `er`,  `or` or `utils`, you should consider re looking at the responsibility of the class.
  - A class name should not be a verb.

- [x] **Methods should have verb or verb phrase names**

- [x] **When constructors are overloaded, try to use static factory methods with names that describe the** **arguments**
  - `Complex fulcrumPoint = Complex.FromRealNumber(23.0)`is better than `Complex fulcrumPoint = new Complex(23.0)`

- [x] **Pick one word for one abstract concept and stick with it**
    - For instance, it’s confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes.

- [x] **Don’t add gratuitous context**
  - For application "Gas Station Deluxe," it is a bad idea to prefix every class with `GSD`.
  - For example use `AccountAddress` instead of `GSDAccountAddress`

- [x] **It's okay to use computer science terms, algorithm names, pattern names, math terms**
  - Always using the problem domain to get names might result in complication, hence we can use solution domain names on need.

- [x] **Add no more context to a name than is necessary**
  - Shorter names are generally better than longer ones, so long as they are clear.

<br/>

---

<br/>

## Functions :microscope:

- [x] **Function should be small**
  - They should be smaller :stuck_out_tongue:
  
- [x] **Blocks inside `if`, `else`, `while` should be one line long, and that should probably be a function call**
  - This keep the enclosing function small.
  - It also adds documentary value because the function called within the block can have a nicely descriptive name.
  
- [x] **The indent level of a function should not be greater than one or two**

- [x] **Functions should do one thing, they should do it well, they should do it only**
  - If a function does only those steps that are one level below the stated name of the function, then the function is doing one thing.

- [x] **Functions should not have sections inside them**
  - If you are able to split a function into sections, then that function is probably doing multiple things.

- [x] **Function should have one level of abstraction**
  - We need to make sure that the statements within our function are all at the same level of abstraction.

- [x] **The Stepdown Rule**
  - The abstraction of a class should decrease as we go reading downwards.
  
- [x] **Switch statement should be buried in a low-level class, should appear only once, to create polymorphic objects and is never repeated**
  - For example it can be in an `Abstract Factory`, but not to be seen anywhere else. 

- [x] **Try to have functions with 3 arguments**
  - Try to keep no of arguments to 3/4.
  - It should never go beyond 4.

- [x] **If a function is going to transform its input argument, the transformation should appear as the return value**
  - If a function does transformation operation of it's input, then the output of that function should be the transformed value
  - If a function is doing a transform of the input, it should do that that only.

- [x] **Flag arguments should be avoided**
  - It does one thing if the flag is `true` and another if the flag is `false`, hence violating Single Responsibility.
  - We should split the function into 2 different functions and call them separately.

- [x] **When a function need more than 2 or 3 arguments, if possible wrap some of those arguments into a class of their own**

- [x] **Functions should not have any side-effects**
  - Mutation of input parameters is to be avoided.

- [x] **Function should do one thing, which the name suggests and not do anything else**

- [x] **Functions should either do something or answer something (command query separation)**
  - Either function should change the state of something, or it should return something.

- [x] **Prefer exceptions to returning error codes**
  - When you return an error code, you create the problem that the caller must deal with the error immediately.
  - Also using Error `enum` is creating a dependency magnet, multiple classes must import and use them.

- [x] **Extract Try/Catch Blocks**
  - Error handing is one thing. Thus, a function that handles errors should do nothing else.
  - If the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.

- [x] **Avoid code duplication**
  - The DRY principle.

<br/>

---

<br/>

## Formatting :rainbow:

- [x] **Vertical size of a file should be typically be within the 200 lines limit**
  
- [x] **We would like a source file to be like a newspaper article**
  - The name should be simple but explanatory.
  - The topmost parts of the source file should provide the high-level concepts and algorithms. i.e. the `public methods`
    - We should be able to tell what a class does by looking at the upper portion of the class.
    - We should be able to see how it does, when we scroll downwards. 
  - Detail should increase as we move downward we should see more implementation details i.e. the `private methods`
  - The general rule for arranging methods
    - public
    - protected 
    - private

- [x] **Vertical Openness Between Concepts**
  - Each line represents an expression or a clause, and each group of lines represents a complete thought. Those thoughts should be separated from each other with blank lines.
  - i.e. methods should be vertically separated by breaks

- [x] **Variables should be declared as close to their usage as possible**
  
- [x] **Instance variables should be declared at the top of the class**

- [x] **If one function calls another, they should be vertically close**
  - The caller should be above the callee.
  - The `private` method which is being called from a `public` method, should appear close to the `public` method.

- [x] **Codes having strong conceptual affinity between them should have less vertical separation between them**
  For example
  ```
    public static void assertTrue(boolean condition) {
       assertThat(condition).isTrue();
     }

     public static void assertFalse(boolean condition) {
       assertThat(condition).isFalse()
     }
     ```


- [x] **Lines should not be more than 120 characters**
  
- [x] **Use spaces between `operators`, `parameters`, and `commas`**

- [x] **Use a consistent formatting style across the team**
  - Use the same `.editorconfig` file across the team.

- [x] **Indentation**
  - Collapsing everything in one line with short `ifs`, `loops`, `functions` is not a good idea.
  - Even for one line `ifs`, one line `whiles` - expand them into multiline and add indent.

<br/>

---

<br/>

## Objects and Data Structures :two_men_holding_hands:

- [x] **Hide implementation of classes with Abstraction**
  - Do not expose variables out through getters and setters. Rather have abstract interfaces that allow users to manipulate the data, without having to know its implementation.
  - We do not want to expose the details of our data. Rather we want to express our data in abstract terms.

- [x] **Data/object anti-symmetry**
  - Objects should hide their data behind abstractions and expose functions that operate on that data.
  - Data structure should expose their data and have no meaningful functions.

- [x] **Choosing between Functional code and OO code**
  - Functional code (code using data structures) makes it easy to add new functions without changing the existing data structures (using pattern matching). 
  - OO code, on the other hand, makes it easy to add new classes (using polymorphism) without changing existing functions.
  - In any complex system there are going to be times when we want to add new data types rather than new functions. For these cases objects and OO are most appropriate. 
  - On the other hand, there will also be times when we’ll want to add new functions as opposed to data types. In that case procedural code and data structures will be more appropriate.
  - Everything is an object is a myth. Sometimes you should just have simple data structures with procedures operating on them.

- [x] **The law of demeter**
  - a method f of a class C should only call the methods of these:
    - [x] C
    - [x] An object created by f
    - [x] An object passed as an argument to f
    - [x] An object held in an instance variable of C
  - The method should not invoke methods on objects that are returned by any of the allowed functions.

- [x] **Train Wrecks**
  - ```
    final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
    ```
    This kind of chaining operations are called train wrecks and should be avoided.
  - This is a violation of law of demeter as well, as we are invoking methods on objects that are returned.
  - And this is only permitted if data structures are used instead of objects, as objects are not supposed to expose their data.
  - But chained transformations are fine though 
  ```
  someList.map(..).map(..).filter(..)
  ```

- [x] **Hybrids, classes which have functions that do significant things, and they also have either public variables or public accessors and mutators**
  - This might result in feature envy smell, as we are exposing access to variables, the caller might be tempted to use them.

- [x] **DTOs should not have any behavior , i.e. they should be data-structure and not objects**

<br/>

---

<br/>

## Error handling :interrobang:

- [x] **Error handling is important, but if it obscures logic, it’s wrong**
  - If your codebase has to many error handler spread across different modules, then by default the code becomes unreadable.
  
- [x] **Use unchecked exceptions**
  - Checked exceptions is an `Open/Closed Principle` violation. If you throw a checked exception from a method in your code and the catch is three levels above, you must declare that exception in the signature of each method between you and the catch. This means that a change at a low level of the code can force signature changes on many higher levels.
  - `Encapsulation` is also broken because all functions in the path of a throw must know about details of that low-level exception.

- [x] **Provide context with exceptions**
  - Create informative error messages and pass them along with your exceptions. 
  - Mention the operation that failed and the type of failure.
  - Pass on the stack trace.

- [x] **Define exception classes in terms of a caller’s needs**
  - Define the exception in such a way that the caller can take a decision based on the exception only. 
  - Use different classes only if there are times when you want to catch one exception and allow the other one to pass through.
  
- [x] **If a portion of code throws many types of exception, wrap that part and throw a common exception**
  - Using the information sent with the exception we should be able to distinguish the errors. 
  
- [x] **Wrap your third party API calls**
  - When you wrap a third-party API, you minimize your dependencies upon it. 
  - You can choose to move to a different library in the future without much penalty. 
  - Wrapping also makes it easier to mock out third-party calls when you are testing your own code.

- [x] **Instead of having a special flow for exception, use special case pattern**
  - From this
    ```
    try {
      MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
      m_total += expenses.getTotal();
    } catch (MealExpensesNotFound e) {
      m_total += getMealPerDiem();
    }
    ```
      to this
      ```
      MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
      m_total += expenses.getTotal();
      ```
      ```
      public class PerDiemMealExpenses implements MealExpenses {
        public int getTotal() {
          // return the per diem default
        }
      }
      ```
  - You basically create a class which it handles a special case for you. Hence the client code doesn’t have to deal with exceptional behavior.

- [x] **Don’t return null**
  - When we return null, the caller needs to have a null check.
  - Remedy to this can be
    - Special case object.
    - Returning empty list.

- [x] **Don’t pass null as arguments**
  - If you pass null, then the callee has to always check for null args.
    ```
    public double xProjection(Point p1, Point p2) {
      if (p1 == null || p2 == null) {
         throw InvalidArgumentException(
           "Invalid argument for MetricsCalculator.xProjection");
      }
      return (p2.x – p1.x) * 1.5;
    }
    ```
    a cleaner way to do this could be
    ```
    public double xProjection(Point p1, Point p2) {
       assert p1 != null : "p1 should not be null";
       assert p2 != null : "p2 should not be null";
       return (p2.x – p1.x) * 1.5;
    }
    ```
    But this also doesn't solve the problem, instead of `NullPointerException` we are going to get some different `RuntimeException`
  - If your language supports it, use a `optional` pattern maybe.

<br/>

---

<br/>

## Unit tests :umbrella:

- [x] **Follow three laws of TDD**
  - You may not write production code until you have written a failing unit test.
  - You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
  - You may not write more production code than is sufficient to pass the currently failing test.

- [x] **Keep test clean**
  - Tests should be first-class citizen. It must be kept as clean as production code
  - Tests must change as the production code evolves. The dirtier the tests, the harder they are to change.

- [x] **Follow the The Build-Operate-Check pattern**
  - The first part builds up the test data, the second part operates on that test data, and the third part checks that the operation yielded the expected results.
  - This is same as `given-when-then` pattern.

- [x] **A Dual Standard**
  - There are things that you might never do in a production environment that are perfectly fine in a test environment. Usually they involve issues of memory or CPU efficiency.

- [x] **One assert per test (flexible)**
  - Ideally there should be one assert per test.
  - But it's okay if we have more, at the end of the day the number of asserts in a test ought to be minimized.
  - The goal is to have one logical assert per test or to test a single behavior in a unit test.

- [x] **Single Concept per Test**
  - Do not operate on different data and then try to assert them in a single test.

- [x] **F.I.R.S.T.**
  - FAST: Tests should be fast.
  - INDEPENDENT: Tests should not depend on each other.
  - REPEATABLE: Tests should be repeatable in any environment.
  - SELF-VALIDATING: The tests should have a boolean output.
  - TIMELY: The tests need to be written in a timely fashion. 
    - Unit tests should be written just before the production code that makes them pass.

<br/>

---

<br/>

## Class :school_satchel:

- [x] **Class organization** :arrow_down:
  - Variables
    - Public static constants
    - private static variables
    - private instance variables
  - Public function
    - Related private functions
  - Public function
    - Related private functions

- [x] **Classes should maintain Encapsulation**
  - Variables and utility functions should be private

-  [x] **Classes should be small and do only one thing**
  - The name of a class should describe what responsibilities it fulfills.
  - If we cannot derive a concise name for a class, then it’s likely too large. 
  - The more ambiguous the class name, the more likely it has too many responsibilities. 
  - We should also be able to write a brief description of the class in about 25 words, without using the words "if," "and," "or," or "but". If you have to use "and" then probably the class has multiple responsibilities.

- [x] **Single Responsibility Principle**
  - Classes should have only one reason to change.

- [x] **Classes should have cohesion**
  - Classes should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables.
  - When classes lose cohesion, split them.
  - Private method behavior that applies only to a small subset of a class can be a useful heuristic, it's probably a hint that you need to extract that portion into a different class.

- [x] **Classes should depend upon abstractions, not on concrete details (Dependency Inversion)**
  
<br/>

---

<br/>

## Emergence :green_book:

- [x] **Design must produce a system that runs all tests as writing tests leads to better designs**
  - A system might have a perfect design on paper, but if there is no simple way to verify that the system actually works as intended, then all the paper effort is questionable.
  - Making our systems testable pushes us toward a design where our classes are small and single purpose. It’s just easier to test classes that conform to the Single Responsibility Principle. 
  - The more tests we write, the more we’ll continue to push toward things that are simpler to test. 
  - Tight coupling makes it difficult to write tests. So, similarly, the more tests we write, the more we use principles like DIP and tools like dependency injection, interfaces, and abstraction to minimize coupling.
  - The fact that we have these tests eliminates the fear that cleaning up the code will break it, and hence we can refactor and make changes with confidence.
  
- [x] **No duplication**
  - Duplication represents additional work, additional risk, and additional unnecessary complexity.
  
- [x] **Expressive**
  - You can express yourself by choosing good names.
  - You can also express yourself by using standard nomenclature. Design patterns names, such as COMMAND or VISITOR.
  - Well-written unit tests are also expressive. A primary goal of tests is to act as documentation by example.

- [x] **Minimal classes and methods**
  - Create small classes but create one when it's justifiable, creating classes just to reduce out on the no of lines of code is a bad practice.
  - Creating an interface for each and every class should be avoided. Or fields and behavior must always separated into data classes and behavior classes.

<br/>

---

<br/>

## Concurrency :arrows_clockwise:

- [x] **Concurrency always doesn't improve performance**

- [x] **To make a system concurrent we might need to change the overall design strategy**

- [x] **Understanding potential concurrency issue is important even though it might not be the problem at hand**

- [x] **Keep your concurrency-related code separate from other code**

- [x] **Shared data between threads create synchronization problems, hence take data encapsulation to heart, limit the access of any data that may be shared**

- [x] **Instead of sharing data, create copies of data for different thread and collect them at the end of processing**

- [x] **Threads Should Be as Independent as Possible, and should not data with any other thread**

- [x] **Use thread safe library functions**
  - Use the provided thread-safe collections.
  - Use the executor framework for executing unrelated tasks.
  - Use nonblocking solutions when possible.

- [x] **Use producer consumer model for concurrent operation**
  - One or more producer threads create some work and place it in a buffer or queue. One or more consumer threads acquire that work from the queue and complete it.

- [x] **Use Readers-Writers model for concurrent operation**
  - For read heavy systems
    - Makes writers wait until there are no readers before allowing the writer to perform an update.
  - For write heavy systems
    - Writers should be given the priority

- [x] **Use different locking strategies like**
  - Client-Based Locking
  - Server-Based Locking
  - Adapted Server Locking

- [x] **Keep your synchronized sections small and avoid side-effects**

- [x] **Have a shutdown strategy in place which works**

- [x] **Treat spurious failures as candidate threading issues**
  - Do not ignore system failures as one-offs.

- [x] **Get your non-threaded code working first**
  - Do not try to chase down nonthreading bugs and threading bugs at the same time. Make sure your code works outside of threads.

- [x] **Make your threaded code pluggable**
  - Make your thread-based code especially pluggable so that you can run it in various configurations.

- [x] **Make your threaded code tunable**
  - Allow configurations like, number of threads to be easily tuned.

- [x] **Run with more threads than processors**

- [x] **Run on different platforms**

- [x] **Instrument your code to try and force failures**

<br/>

---

<br/>

## Code smells :speak_no_evil:

- [x] **If you see commented out code. delete it**

- [x] **Unused code should be deleted**

- [x] **Implementation should be obvious**

- [x] **Look for every boundary condition and write a test for it**

- [x] **Base classes should know nothing about their derivatives**

- [x] **Code should be consistent**
  - If within a particular function you use a variable named response to hold an HttpServletResponse, then use the same variable name consistently in the other functions that use HttpServletResponse objects

- [x] **Prefer nonstatic methods to static methods**
  - If you really want a function to be static, make sure that there is no chance that you’ll want it to behave polymorphically.

- [x] **Avoid Negative Conditionals**
  - `if (buffer.shouldCompact())` is better than `if (!buffer.shouldNotCompact())`

- [x] **Encapsulate Boundary Conditions**
  - ```
    if(level + 1 < tags.length) {
     parts = new Parse(body, tags, level + 1, offset + endTag);
     body = null
     }
     ```
   `level + 1` is a boundary operation which is repeated so we can wrap that in a variable like `nextLevel = level + 1`

- [x] **Avoid Long Import Lists by Using Wildcards**

- [x] **Don’t Inherit Constants**
  - Use static imports instead

- [x] **Use enums and not `public static final ints/strings`**



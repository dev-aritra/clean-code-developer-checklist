# Clean Code Developer Checklist
A developer checklist derived from the book Clean Code by Robert C Martin 

## Table of contents :bookmark_tabs:
  - [Meaningful Names](#meaningful-names-u5272)
  - [Functions](#functions-microscope)
  - [Formatting](#formatting-rainbow)
  - [Objects and Data Structures](#objects-and-data-structures-two_men_holding_hands)
  - [Error handling](#error-handling-interrobang)

<br/>


## Meaningful Names :u5272:

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
  - A class name should not be a verb.

- [x] **Methods should have verb or verb phrase names**

- [x] **When constructors are overloaded, use static factory methods with names that describe the** **arguments**
  - `Complex fulcrumPoint = Complex.FromRealNumber(23.0)`is better than `Complex fulcrumPoint = new Complex(23.0)`

- [x] **Pick one word for one abstract concept and stick with it**
    - For instance, it’s confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes.

- [x] **Don’t add gratuitous context**
  - For application “Gas Station Deluxe,” it is a bad idea to prefix every class with `GSD`.
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
  
- [x] **Blocks inside `if`, `else`, `while` should be 1 line long, and that should probably be a function call**
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
  -  When we can read the program, descending one level of abstraction at a time as we read down the list of functions.
  
- [x] **Switch statement should be buried in a low-level class, should appear only once, to create polymorphic objects and is never repeated**
  - For example it can be in an `Abstract Factory`, but not to be seen anywhere else. 

- [x] **Functions should have at max 3 arguments**

- [x] **If a function is going to transform its input argument, the transformation should appear as the return value**

- [x] **Flag arguments should be avoided**
  - It does one thing if the flag is `true` and another if the flag is `false`, hence violating Single Responsibility.
  - We should split the function into 2 different functions and call them separately.

- [x] **When a function need more than 2 or 3 arguments, if possible wrap some of those arguments into a class of their own**

- [x] **Functions should not have any side-effects**
  - It should do one thing, which the name suggests and not do anything else.

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
  - Detail should increase as we move downward, until at the end we find the lowest level functions and details in the source file. i.e. the `private methods`

- [x] **Vertical Openness Between Concepts**
  - Each line represents an expression or a clause, and each group of lines represents a complete thought. Those thoughts should be separated from each other with blank lines.
  - i.e. methods should be vertically separated by breaks

- [x] **Variables should be declared as close to their usage as possible**
  
- [x] **Instance variables should be declared at the top of the class**

- [x] **If one function calls another, they should be vertically close**
  - The caller should be above the callee.
  - The `private` method which is being called from a `public` method, should appear bellow the `public` method.

- [x] **Codes having strong conceptual affinity between them should have less vertical separation between them**
  For example
  - ```
    static public void assertTrue(boolean condition) {
       assertTrue(null, condition);
     }
 
     static public void assertFalse(String message, boolean condition) {
       assertTrue(message, !condition);
     }
 
     static public void assertFalse(boolean condition) {
       assertFalse(null, condition);
     }
     ```


- [x] **Lines should not be more than 120 characters**
  
- [x] **Use spaces between `operators`, `parameters`, and `commas`**

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
    • C
    • An object created by f
    • An object passed as an argument to f
    • An object held in an instance variable of C
  - The method should not invoke methods on objects that are returned by any of the allowed functions.

- [x] **Train Wrecks**
  - ```
    final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
    ```
    This kind of chaining operations are called train wrecks and should be avoided.
  - This is a violation of law of demeter as well, as we are invoking methods on objects that are returned.
  - And this is only permitted if data structures are used instead of objects, as objects are not supposed to expose their data.

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
           “Invalid argument for MetricsCalculator.xProjection”);
      }
      return (p2.x – p1.x) * 1.5;
    }
    ```
    a cleaner way to do this could be
    ```
    public double xProjection(Point p1, Point p2) {
       assert p1 != null : “p1 should not be null”;
       assert p2 != null : “p2 should not be null”;
       return (p2.x – p1.x) * 1.5;
    }
    ```
    But this also doesn't solve the problem, instead of `NullPointerException` we are going to get some different `RuntimeException`

  
  




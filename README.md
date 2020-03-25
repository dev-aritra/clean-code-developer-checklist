# Clean Code Developer Checklist
A developer checklist derived from the book Clean Code by Robert C Martin 

## Table of contents :bookmark_tabs:
  - [Meaningful Names](#meaningful-names-u5272)
  - [Functions](#functions-microscope)
  - [Formatting](#formatting-rainbow)

<br/>


## Meaningful Names :u5272:

- [x] ****Name should reveal intent****
  - It should tell you why it exists, what it does, and how it is used.
  - Name should depict the context.

- [x] ****Avoid using abbreviations****
  - Use `hypotenuse` instead of `hp`.

- [x] ****Do not encode name with data structure****
  - Use `accounts` instead of `accountList`.

- [x] ****Do not use names which vary in small ways****
  - Find the difference between `ControllerForEfficientHandlingOfStrings` and `ControllerForEfficientStorageOfStrings` :dancers:

- [x] ****Do not name variables just to satisfy the compiler****
  - Don't name something `name1` cause `name` is already taken.

- [x] ****Avoid using noise words****
  - `ProductData` and `ProductInfo` kind of means the same thing.
  - Similarly words like `a`, `an`, `the` are also noise words.
  - Noise words are also **redundant**, use `name` instead of `nameString`.

- [x] ****Distinguish names in such a way that the reader knows which one to call.****

- [x] ****Use pronounceable names****

- [x] ****Use searchable names****
  - Use constants instead of hard coding a value, `WORK_DAYS_PER_WEEK = 5` instead of just using 5.

- [x] ****The length of a name should correspond to the size of its scope****
  - There can be a variable `i` inside a `for loop` but `i` should never be a `instance variable`.

- [x] ****Classes and objects should have noun or noun phrase names.****
  - Avoid words like `Manager`, `Processor`, `Data`, or `Info` in the name of a class.
  - A class name should not be a verb.

- [x] ****Methods should have verb or verb phrase names****

- [x] ****When constructors are overloaded, use static factory methods with names that describe the** **arguments****
  - `Complex fulcrumPoint = Complex.FromRealNumber(23.0)`is better than `Complex fulcrumPoint = new Complex(23.0)`

- [x] ****Pick one word for one abstract concept and stick with it****
    - For instance, it’s confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes.

- [x] ****Don’t add gratuitous context****
  - For application “Gas Station Deluxe,” it is a bad idea to prefix every class with `GSD`.
  - For example use `AccountAddress` instead of `GSDAccountAddress`

- [x] ****It's okay to use computer science terms, algorithm names, pattern names, math terms****
  - Always using the problem domain to get names might result in complication, hence we can use solution domain names on need.

- [x] ****Add no more context to a name than is necessary****
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

- [x] Vertical size of a file should be typically be within the 200 lines limit
  
- [x] We would like a source file to be like a newspaper article
  - The name should be simple but explanatory.
  - The topmost parts of the source file should provide the high-level concepts and algorithms. i.e. the `public methods`
  - Detail should increase as we move downward, until at the end we find the lowest level functions and details in the source file. i.e. the `private methods`

- [x] Vertical Openness Between Concepts
  - Each line represents an expression or a clause, and each group of lines represents a complete thought. Those thoughts should be separated from each other with blank lines.
  - i.e. methods should be vertically separated by breaks

- [x] Variables should be declared as close to their usage as possible
  
- [x] Instance variables should be declared at the top of the class

- [x] If one function calls another, they should be vertically close
  - The caller should be above the callee.
  - The `private` method which is being called from a `public` method, should appear bellow the `public` method.

- [x] Codes having strong conceptual affinity between them should have less vertical separation between them. 
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


- [x] Lines should not be more than 120 characters
  
- [x] Use spaces between `operators`, `parameters`, and `commas`

- [x] Indentation
  - Collapsing everything in one line with short `ifs`, `loops`, `functions` is not a good idea.
  - Even for one line `ifs`, one line `whiles` - expand them into multiline and add indent.



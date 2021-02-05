# Tech Interview Workbook

###### This is part of Codecool's curriculum Self Instructed Practice. It contains answers to questions from the "Programming Basics", "Web with Python", "Java OOP" and "Advanced .NET C#" Modules.

---

1. ## [Programming Basics module](#Programming-Basics-Questions)
2. ## [Web with Python module](#Web-with-Python-Questions)
3. ## [Java OOP module](#OOP-Questions)
4. ## [Advanced .NET C# module](#Advanced)

---

<br/><br/>
<br/><br/>
<br/><br/>

# Programming Basics Questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!

- The purpose of a list is to collect objects in an orderly manner.
- Some list methods are: _append()_, _extend()_, _insert()_, _remove()_, or _pop()_.

#### What is the difference between a list/array and a set?

- A list is ordered, can be accessed using an index, can have duplicate elements and are mutable (elements can be added,deleted, or moved around).
- A set is unordered, its elements are unique and are immutable (they can't be changed once they have been assigned).

#### What is the purpose and methods of a dictionary/map data structure?

- The purpose of a dictionary is to map keys to values and store them in an array or collection.
- The methods of a dictionary are: _items()_, _keys()_, _values()_, _get()_ and _popitem()_.

---

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.

```
def fibonacci(n):
    terms = [0, 1]
    i = 2
    while i <= n:
        terms.append(terms[i - 1] + terms[i - 2])
        i += 1
    return terms
```

#### How do you find a max value in a list/array if you can’t use any built-in functions?

```
def max_in_list(listOfNr):
    maxi = -1.8e308
    for number in listOfNr:
        if maxi < number:
            maxi = number
    return maxi
```

#### How do you find the average of values in a list/array if you can’t use any built-in functions?

```
def find_avg(array):
    sum_of_values = 0
    for value in array:
        sum_of_values += value
    return sum_of_values / len(array)
```

#### What do we call an _in-place_ sort?

- We call _sort()_ an in-place method because it modifies a given list in-place (it modifies the actual list on the spot without returning a new one) by using _<_ comparisons between items.

#### Explain an algorithm which sorts a list!

- Example of _Bubble Sort_ algorithm:

```
finished = False                    # declare a boolean variable to check if we finished sorting the list
list_length = len(a_list)           # get the number of items in a list so that we don't call len() for each iteration
while not finished:                 # we keep looping until we finished sorting (finished == True)
    finished = True                 # we assume it's finished (the condition to break out of the while loop)
    for i in range(list_length - 1):               # iterate through the list without the last item
        if a_list[i] > a_list[i + 1]:              # if the current item is bigger than the next..
            a_list[i], a_list[i + 1] = a_list[i + 1], a_list[i]         # we swap them
            finished = False        # keep looping until we have nothing left to swap
```

---

### Programming paradigms - procedural

#### What is the call stack?

- The _call stack_ is a frame where Python stores information about functions which have been called.
- Whenever a function is called, a new stack frame is added to the stack – all of the function’s parameters are added to it, and as the body of the function is executed, local variables will be created there.
- When the function finishes executing, its stack frame is discarded, and the flow of control returns to wherever you were before you called the function, at the previous level of the stack.

#### What is “Stack overflow”?

- _Stack overflow_ is a filled up stack frame. Python’s stack has a finite size – if we keep placing instances of the function on the stack we will eventually fill it up and cause a stack overflow.

#### What are the main parts of a function?

- The main parts of a function are: _parameters_, _function body_, _variables_, _statements_, _expressions_, _function call_ and _arguments (input parameters)_.

---

### Programming languages - Python

#### How do you use a dictionary in Python?

- We can use a dictionary to store key-value pairs. To define a dictionary literal, we put a comma-separated list of key-value pairs between curly brackets. We use a colon to separate each key from its value. We access values in the dictionary by using keys instead of indices.

#### What does it mean that an object is immutable in Python?

- _Immutable_ means we cannot alter the existing value in any way. Some values in Python can be modified, and some cannot.
- Integers, floating-point numbers and strings are all immutable types. Tuples are immutable data types.

#### What is conditional expression in Python?

- A _conditional expression_ is a selection control statement that allows programmers to change the flow of control.
- Conditionals (the _if/elif/else_ family) can be used to pick a code block based upon the truth value of the conditions in them.

#### What are different types of arguments in Python?

- There are 3 types of arguments:
  1. _optional_ => To make a parameter optional, we need to supply a default value for it. Optional parameters must come after all the required parameters in the function definition:
  ```
  def make_greeting(title, name, surname, formal=True):
      if formal:
          return "Hello, %s %s!" % (title, surname)
      return "Hello, %s!" % name
  make_greeting("Mr", "John", "Smith")
  make_greeting("Mr", "John", "Smith", False)
  ```
  2. _positional_ => a tuple of values which are matched up with parameters in the function signature based on their positions:
  ```
  def make_greeting(title, name, surname, formal=True, time=None):
      if formal:
          fullname =  "%s %s" % (title, surname)
      else:
          fullname = name
      if time is None:
          greeting = "Hello"
      else:
          greeting = "Good %s" % time
      return "%s, %s!" % (greeting, fullname)
  make_greeting("Mr", "John", "Smith", False, "evening")
  ```
  3. _keyword_: => explicitly specify the parameter names along with the values:
  ```
  make_greeting(title="Mr", name="John", surname="Smith", formal=False, time="evening")
  ```

#### What is variable shadowing? (context: variable scope)

- _Variable shadowing_ occurs when a variable declared within a certain scope (decision block, method, or inner class) has the same name as a variable declared in an outer scope:

```
x = 0
def outer():
    x = 1
    def inner():
        x = 2
        print("inner:", x)
    inner()                # prints //inner: 2
    print("outer:", x)
outer()                    # prints //outer: 1
print("global:", x)        # prints //global: 0
```

#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?

- You may encounter an IndexError: list index out of range.

#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?

- The "golden rule" of variable scoping in Python (context: LEGB, L = Local, E = Enclosed (function is wrapped inside another function), G = Global, B =Built-in): when local as well as global variable is present, _preference is given to the local variable_.
- The lifetime of a variable: it exists for as long as the function is executing.

#### If you need to access the iterator variable after a for loop, how would you do it in Python?

- The built-in Python function _iter()_, which returns something called an iterator. The built-in function _next()_ is used to obtain the next value from in iterator:

```
a = ['foo', 'bar', 'baz']
itr = iter(a)
next(itr)
next(itr)
next(itr)
```

- If all the values from an iterator have been returned already, a subsequent next() call raises a StopIteration exception.

#### What type of elements can a list contain in Python?

- A list can contain basically any type of elements.

#### What is slice operator in Python and how to use?

- The slice operator is a method that extracts a subset of a list, which will itself be a list.
- In order to use it, you need to specify an upper and lower bound. Note that our sublist will include the element at the lower bound, but _exclude_ the element at the upper bound:

```
animals = ['cat', 'dog', 'fish', 'bison']
print(animals[1:3]) # ['dog', 'fish']
print(animals[1:-1]) # ['dog', 'fish']
```

#### What arithmetic operators (+,\*,-,/) can be used on lists in Python? What do they do?

- The arithmetic operators that can be used on lists are:
  - **+** addition
  - **-** subtraction
  - **\*** multiplication
  - **/** division
  - **%** modulo (the remainder of division)
  - **\*\*** exponentiation

#### What is the purpose of the in and not in membership operators in Python?

- Membership operators like _in_ and _not in_ are operators used to validate the membership of a value. They test for membership in a sequence, such as strings, lists, or tuples.

#### What does the + operator mean when used with strings in Python?

- When used with strings, the **+** operator means concatenation: a method to add multiple strings together.

#### Explain f strings in Python?

- Python 3.6 added a new string formatting approach called formatted string literals or “f-strings”. This new way of formatting strings lets you use embedded Python expressions inside string constants:

```
>>> f'Hello, {name}!'
'Hello, Bob!'
```

#### Name 4 iterable types in Python!

- Lists, tuples, dictionaries and sets are all iterable types in Python.

#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?

- List Comprehension allows us to create a list using for loop with lesser code.
- The Generator Expression allows us to create a generator without the yield keyword. Instead of creating a list/set/dictionary and keeping the whole sequence in the memory, the generator generates the next element in demand.

```
list_comprehension = [i for i in range(11) if i % 2 == 0]
generator_expression = (i for i in range(11) if i % 2 == 0)
```

- The generator yields one item at a time and generates item only when in demand. Whereas, in a list/set/dictionary comprehension, Python reserves memory for the whole list. Thus we can say that the generator expressions are memory efficient than the lists/set/dictionary comprehensions. Also generator expressions are faster than list/set/dictionary comprehensions and hence time efficient.

#### Does the order of the function definitions matter in Python? Why?

- Yes, the order of the function definitions does matter in Python, because any call to a function must come after that function definition.

#### What does unpacking mean in Python?

- We can use \* or \*\* when we are calling a function to _unpack_ a sequence or a dictionary into a series of individual parameters:

```
my_list = ["one", "two", "three"]
print_args(*my_list)
my_dict = {"name": "Jane", "surname": "Doe"}
print_kwargs(**my_dict)
```

#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?

- A function without an explicit return statement returns _None_. The variable will have the value of _None_.

---

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?

- We can use the following techniques for debugging:
  - insert a _print()_ statement after every line which outputs the intermediate results which were calculated on that line.
  - an IDE debugger tool or the _pdb_, a built-in Python module which we can use to debug a program while it’s running.
  - some automated tools which can help us to debug errors:
    - _Pyflakes_ parses code instead of importing it, which means that it can’t detect as many errors as other tools (but it is also safer to use, since there is no risk that it will execute broken code which does permanent damage to our system).
    - _Pylint_ and _PyChecker_ do import the code that they check, and they produce more extensive lists of errors and warnings.
    - _Pep8_ specifically targets bad coding style – it checks whether our code conforms to Pep 8, a specification document for good coding style.

#### What does step over, step into and step out mean while using the debugger?

- **_step into_** A function is about to be invoked and you want to debug into the code of that function, so the next step is to go into that function and continue debugging step-by-step.
- **_step over_** A function is about to be invoked, but you're not interested in debugging this particular invocation, so you want the debugger to execute that function completely as one entire step.
- **_step out_** You're done debugging this function step-by-step and you just want the debugger to run the entire function until it returns as one entire step.

#### How can you start to debug a program from a certain line using the debugger?

- **_line breakpoint_** You don't care how it got there, but if execution reaches a particular line of code, you want the debugger to temporarily pause execution there so you can decide what to do.

---

### Version control

#### What are the advantages of using a version control system?

- The primary benefits you should expect from version control are as follows:
  1. A complete long-term change history of every file (enables going back to previous versions to help in root cause analysis for bugs and it is crucial when needing to fix problems in older versions of software).
  2. Branching and merging. Individuals working on their own can benefit from the ability to work on independent streams of changes. There are many different workflows that teams can choose from when they decide how to make use of branching and merging facilities.
  3. Traceability. Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

#### What is the difference between the working directory, the staging area and the repository in git?

- Git has 3 areas:
  - The _working directory_ = contains the latest downloaded version from the repository together with any changes that have yet to be committed. As you're working on a project, all changes are made in this working directory.
  - The _staging area_ = helps to maintain this workflow by allowing you to only promote certain files at a time instead of all the changes in your working directory. Users move, otherwise referred to as promote, changes from the working directory, to a staging area before committing them into the repository.
  - The _repository_ = a virtual storage of your project. It allows you to save versions of your code, which you can access when needed.

#### What are remote repositories in git?

- Remote repositories are versions of your project that are hosted on the Internet or network somewhere. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.

#### Why does a merge conflict occur?

- Merge conflicts happen when you merge branches that have competing commits, and Git needs your help to decide which changes to incorporate in the final merge.

#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?

- In Terminal, add the URL for the remote repository where your local repository will be pushed:
  - $ git remote add origin remote repository URL # Sets the new remote
  - $ git remote -v # Verifies the new remote URL
- Push the changes in your local repository to GitHub:
  - $ git push origin master # Pushes the changes in your local repository up to the remote repository you specified as the origin

#### What does it mean atomic commits and descriptive commit messages?

- When making code changes, you want to make commits that are generally smaller and that encompass only one irreducible feature, fix, or improvement.

#### What’s the difference between git and GitHub?

- Git is a version control system that lets you manage and keep track of your source code history.
- GitHub is a web-based hosting service that lets you manage Git repositories. If you have open-source projects that use Git, then GitHub is designed to help you better manage them.

---

## Software design

### Clean code

#### What does clean code mean?

- Code is clean if it can be understood easily – by everyone on the team. Clean code can be read and enhanced by a developer other than its original author. With understandability comes readability, changeability, extensibility and maintainability.

#### What steps do we usually do during a clean code refactoring?

- Read through the whole code.
- Summarize what is the purpose of the script in one sentence.
- Run the code to see what is the end result.
- The code should keep runnable and show the same content when you finish the refactor.
- Run the code frequently to check you are on the right track.
- Actual refactoring:
  - Remove clutter: Clutter is anything in your code that does not add value
    - Format your code
    - Delete comments
  - Remove complexity:
    - bad names
    - long methods
    - deep conditionals
    - improper variable scopes (global, local)
  - Remove cleverness: If it's simple and elegant you wouldn't refer to it as 'clever'
  - Remove the 3 D's: duplication, duplication, duplication
    - this can be applied by extracting the duplicated code parts into functions

---

### Error handling

#### What is exception handling?

- _Exception handling_ is a method that handles unexpected errors in a Python program. Instead of letting the error crash our program we can intercept it, do something about it, and allow the program to continue.
- Errors are called exceptions in Python and all exceptions are subclasses of the Exception class.

#### What are the basics of exception handling in Python?

- The basics of _exception handling_ consist of _try-except_ blocks. Python will try to process all the statements inside the _try_ block.
- If an error occurs at any point as it is executing them, the flow of control will immediately pass to the except block, and any remaining statements in the try block will be skipped.
  > - It is good practice if the only code inside the try block is the single line that is the potential source of the error that we want to handle.

#### In which case should we catch an exception? Why?

- We should catch an exception when we want to protect small blocks of code against specific errors (better than to wrap large blocks of code and write vague, generic error recovery code).
- We catch exceptions because:
  - Exception handling separates normal code from code that handles errors.
  - Exceptions can easily be passed along functions in the stack until they reach a function which knows how to handle them.
  - Exceptions come with lots of useful error information built in – for example, they can print a traceback which helps us to see exactly where the error occurred.

#### What can/should we do with an exception in the ‘except’ block?

- In the ‘except’ block we should write code that the program will execute when there is an exception.
- We can raise exceptions ourselves using the _raise_ statement - perhaps we may want to handle it partially in the current function, but also want to respond to it in the code which called the function.
- We can also write our own custom exception classes which are based on existing exception classes.

#### What does the else and finally statement do in a try-except block in Python?

- The _else_ statement will be executed only if the try clause doesn’t raise an exception.
- The _finally_ clause will be executed at the end of the try-except block no matter what – if there is no exception, if an exception is raised and handled, if an exception is raised and not handled, and even if we exit the block using _break_, _continue_ or _return_. We can use the _finally_ clause for cleanup code that we always want to be executed.

---

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?

According to Agile software development:

> - A retrospective meeting is a meeting that's held at the end of a single development cycle, usually measured as one week or two.
> - The main goal of the retrospective is to reflect on what happened in the development and identify actions for improvement and going forward.
> - Each member of the team members answers the following questions:
>   - What worked well for us?
>   - What did not work well for us?
>   - What actions can we take to improve our process going forward?

---

## Programming environment

### Unix

#### What is UNIX and what is Linux?

- UNIX is an operating system that was born in the late 1960s, when AT&T Bell Labs released an operating system called Unix written in C, which allows quicker modification, acceptance, and portability. It began as a one-man project under the leadership of Ken Thompson of Bell Labs. It went on to become one of the most widely used operating systems. Unix is a proprietary operating system.
- Linux is a replica of UNIX that does not use its code, built by Linus Torvalds at the University of Helsinki in 1991. The name "Linux" comes from the Linux kernel. It is free and open source software.

#### What do we call the shell in Linux?

- Shell = command line interpreter

#### What does root means in a Linux environment?

- Root is the user name or account that by default has access to all commands and files on a Linux or other UNIX-like operating systems. It is also referred to as the _root account_, _root user_ or the _superuser_.

#### How do you access your personal files in Linux?

- In Linux, personal data is stored in /home/username folder.

#### How can you install an application in Linux?

- Run the command in the Terminal (text input/output environment):

```
sudo apt install <name_of_application>
```

#### What is package management in Linux, what are repositories?

- Package management system allows users to install, update, remove and get information about software installed.
- Repositories are storage locations where the packages are downloaded from.
- Users can use _apt_ and _dpkg_ commands to query and update the database of software available in repositories and installed on the system, to install or remove software and upgrade installed packages, and clean up obsolete programs.

#### How do you navigate in the filesystem with the command line?

- _cd_ Change directory. Used to navigate between folders.
- _pwd_ Display current directory.
- _ls_ Display a list of files in the current directory.
- _stat_ Display when a file was last accessed, modified, or changed.

#### What does the following commands do: mkdir, rm, cat, cp, touch?

- _mkdir_ Create a directory.
- _rm_ Remove a file or set of files.
- _cat_ Display the contents of a text file.
- _cp_ Makes a copy of a file.
- _touch_ Create a file.

#### How can you look up what does a command do in Linux if you have no internet connection?

- _command --help_ or _man command_

#### What does the following commands do: head, tail, more, less?

- _head_ Output the first 10 lines of file.
- _tail_ Output the last 10 lines of file.
- _more_ Output the contents of file.
- _less_ View and paginate file.

#### How do you download a file from internet using the terminal?

- _wget file_

---

---

<br/><br/>
<br/><br/>
<br/><br/>

# Web with Python Questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!

1. Include the **_AS_** keyword for creating aliases: the first letter of each word in the object’s name
2. Use uppercase for the reserved keywords like **_SELECT_** and **_WHERE_**.
3. Indentation: can really help the readability
4. Try to use only standard SQL functions
5. Only use letters, numbers and underscores in names.

#### What layers can you name in a simple web application?

- Presentation layer (UI layer, view layer, presentation tier)
- Business layer (business logic: determines how data can be created, stored, and changed. )
- Data access layer (persistence layer, logging, managing a database and other services which are required to support
  a particular business layer)

---

### Error handling

#### What error can occur, when an array does not have an element on the requested index?

- IndexOutOfRangeException

#### What is the “finally” block, and how would you use it?

- **_finally_** block is always executed after leaving the **_try_** statement
- **_finally_** block is used to deallocate the system resources.

#### Why should we catch special exception types?

- In Python, we use special exception types for control-flow, for pulling error-handling outside loops and can simplify
  code quite a bit in common situations where the ability to handle an issue is far removed from where the issue arose.
- The use of exceptions in Python does not slow the surrounding code and calling code.

---

### Security

#### What is SQL injection? How to protect an application against it?

- A SQL injection (SQLi) is a type of security exploit in which the attacker adds Structured Query Language (SQL) code
  to a Web form input box in order to gain access to unauthorized resources or make changes to sensitive data.
- The only sure way to prevent SQL Injection attacks is input validation and parametrized queries including prepared
  statements. The application code should never use the input directly.
- The developer must sanitize all input, not only
  web form inputs such as login forms.

#### What is XSS? How to protect an application against it?

- Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise
  benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code,
  generally in the form of a browser side script, to a different end user.
- For example, the attacker could send the victim a misleading email with a link containing malicious JavaScript. If
  the victim clicks on the link, the HTTP request is initiated from the victim's browser and sent to the vulnerable web
  application.
- How to prevent XSS attacks:
  - Filter input on arrival. At the point where user input is received, filter as strictly as possible based on what
    is expected or valid input.
  - Encode data on output. At the point where user-controllable data is output in HTTP responses, encode the output
    to prevent it from being interpreted as active content.
  - Use appropriate response headers. To prevent XSS in HTTP responses that aren't intended to contain any HTML or
    JavaScript, you can use the Content-Type and X-Content-Type-Options headers to ensure that browsers interpret the
    responses in the way you intend.

#### How to properly store passwords?

- The best way to protect passwords is to employ salted password hashing.
- To Store a Password:
  1. Generate a long random salt using a CSPRNG.
  2. Prepend the salt to the password and hash it with a standard password hashing function like Argon2, bcrypt
     , scrypt, or PBKDF2.
  3. Save both the salt and the hash in the user's database record.
- To Validate a Password:
  1. Retrieve the user's salt and hash from the database.
  2. Prepend the salt to the given password and hash it using the same hash function.
  3. Compare the hash of the given password with the hash from the database. If they match, the password is correct.
     Otherwise, the password is incorrect.

#### What is HTTPS?

- Hypertext Transfer Protocol Secure (HTTPS) is an extension of the Hypertext Transfer Protocol (HTTP). It is used for
  secure communication over a computer network, and is widely used on the Internet.
- HTTPS takes the HTTP protocol, and simply layers a SSL/TLS encryption layer on top of it. Servers and clients still
  speak exactly the same HTTP to each other, but over a secure SSL connection that encrypts and decrypts their requests
  and responses.

#### What is encryption and decryption?

- **_Encryption_** is the process of translating plain text data (plaintext) into something that appears to be random and
  meaningless (cipher text).
- **_Decryption_** is the process of converting cipher text back to plaintext.

#### What is hashing?

- A method of generating from a data collection a fixed length string.

#### What is the difference between encryption and hashing? When would you use which?

- Encryption is reversible, while hashing is one way.

#### What encryption methods do you know?

- Symmetric:
  - encrypter, and decrypter — need access to the same key.
  - make the key available only to the software that needs it.
- Asymmetric:
  - known as public key cryptography, uses public and private keys to encrypt and decrypt data.
  - Either of the keys can be used to encrypt a message; the opposite key from the one used to encrypt the message
    is used for decryption.
- Hash:
  - used only to verify data
  - the same input will always produce the same output
  - impossible to reverse it back to the original data

#### What hashing methods do you know?

- SHA-1: This is the second version of the Secure Hash Algorithm standard, SHA-0 being the first.
  SHA-1 creates 160-bit outputs.
- SHA-2: This is actually a suite of hashing algorithms. The suite contains SHA-224, SHA-256, SHA-384, and SHA-512.
  Each algorithm is represented by the length of its output. SHA-2 algorithms are more secure than SHA-1 algorithms

#### How/where would you store sensitive data (like db password, API key, ...) of your application?

- Sensitive data should never be used or stored in non-production systems, and access passwords should be stored in a
  password manager rather than entrusted to individuals.

---

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?

- The main differences between stack and queue are that **_Stack_** uses LIFO (last in first out) method to access and
  add data elements whereas **_Queue_** uses FIFO (First in first out) method to access and add data elements.

#### What is BubbleSort? Describe the main logic of this sorting algorithm.

- A sorting algorithm that repeatedly steps through the list, compares adjacent elements and swaps them if
  they are in the wrong order. The pass through the list is repeated until the list is sorted.

#### Explain the process of finding the maximum and minimum value in a list of numbers!

- Declare two variables max and min to store maximum and minimum. Assume first array element as maximum and minimum
  both, say max = arr[0] and min = arr[0] .
- Iterate through array to find maximum and minimum element in array.

#### Explain the process of calculating the average value in an array of numbers!

- Collect integer values in an array A of size N. Add all values of A. Divide the output with N. Display the
  output as average.

#### What is Big O complexity? Explain time and space complexity!

- Big O notation is used in Computer Science to describe the performance or complexity of an algorithm.
- Big O specifically describes the worst-case scenario, and can be used to describe the execution time required or the
  space used (e.g. in memory or on disk) by an algorithm:
  _ Different steps get added:
  _ O(a + b)
  _ Drop constants:
  _ <del>O(2n)</del> &rarr; O(n)
  _ Different inputs &rarr; different variables:
  _ <del>O(n<sup>2</sup>)</del> &rarr; O(a _ b)
  _ Drop non-dominate terms: \* <del>O(n + n<sup>2</sup>)</del> &rarr; O(n<sup>2</sup>)

#### Explain the process of calculating the average value in a linked list of numbers!

- Start traversing the linked list using a loop until all the nodes get traversed. Add the value of current node to
  the sum i.e. sum += ptr -> data.
- Increment the pointer to the next node of linked list i.e. ptr = ptr ->next . Divide sum by total number of node
  and Return the average.

---

### Procedural

#### How the CASE condition works in SQL?

- CASE expression is the same as IF/ELSE statement in other programming languages:

```
SELECT name, continent, indep_year,
    CASE WHEN indep_year < 1900 THEN 'before 1900'
    WHEN indep_year <= 1930 THEN 'between 1900 and 1930'
    ELSE 'after 1930'
    END AS indep_year_group
FROM countries
ORDER BY indep_year_group;
```

#### How the switch-case condition works in JavaScript?

```
let a = 2 + 2;
switch (a) {
  case 3:
    alert( 'Too small' );
    break;
  case 4:
    alert( 'Exactly!' );
    break;
  case 5:
    alert( 'Too large' );
    break;
  default:
    alert( "I don't know such values" );
}
```

#### How to achieve a switch-case-like structure in Python?

```
def week(i):
    switcher={
            0:'Sunday',
            1:'Monday',
            2:'Tuesday',
            3:'Wednesday',
            4:'Thursday',
            5:'Friday',
            6:'Saturday'
         }
    return switcher.get(i, "Invalid day of week")
```

#### Explain variable scoping in Python!

- A variable created inside a function is available inside that function
- The local variable can be accessed from a function within the function
- A variable created outside of a function is global and can be used by anyone

#### What’s the difference between const and var in JavaScript?

- var: The scope of a variable defined with the keyword “var” is limited to the “function” within which it is defined.
  If it is defined outside any function, the scope of the variable is global.
- var is “function scoped”.
- let: The scope of a variable defined with the keyword “let” or “const” is limited to the “block” defined by curly
  braces i.e. {}.
- “let” and “const” are“block scoped”.
- const: The scope of a variable defined with the keyword “const” is limited to the block defined by curly braces.
- “const” cannot be re-assigned to a new value.
- value of the variable defined within the "const" keyword is mutable

#### How the list comprehension looks like in Python?

```
new_list = [expression for member in iterable (if conditional)]
sentence = 'the rocket came back from mars'
vowels = [i for i in sentence if i in 'aeiou']
```

#### How the “ternary expression” looks like in Python?

```
a if a > b else b
'yes' if ('qux' in ['foo', 'bar', 'baz']) else 'no'
```

#### How the ternary expression looks like in JavaScript?

```
var age = 19;
var canDrive = age > 16 ? 'yes' : 'no';
```

#### How to import a function from another module in Python?

```
import mod
from mod import s, foo
```

#### How to import a function from another module in JavaScript?

```
models/course.js
export function Course() {
    this.id = '';
    this.name = '';
};
models/student.js
import { Course } from './course.js';
```

---

### Functional

#### What is recursion?

- Recursion is the process which comes into existence when a function calls a copy of itself to work on a smaller
  problem. Any function which calls itself is called recursive function, and such function calls are called recursive
  calls.

#### Write a recursive function which calculates the Fibonacci numbers!

```
def fib(n):
    if n < 0:
        return "Incorrect input"
    elif n == 1:
        return 0
    elif n == 2:
        return 1
    else:
        return fib(n - 1) + fib(n - 2)
def fib_seq(n):
    result = []
    for i in range(1, n + 1):
        temp = fib(i)
        result.append(temp)
    return result
```

#### How to store a function in a variable in Python?

```
def greet(name):
    def get_message():
        return "Hello "

    result = get_message() + name
    return result
```

#### List the ways of defining a callable logical unit in JavaScript!

- Function expression:

```
const square = function(number) {
    return number * number
}
```

- Function declaration:

```
function square(number) {
  return number * number;
}
```

- IIFE (Immediately Invoked Function Expression):

```
(function(number) {
    return number * number
})();
```

#### What is an event listener? How to attach one?

- A function that is called whenever an event of the specified type occurs:

```
const buttonElement = document.getElementById('btn');
buttonElement.addEventListener('click', function (event) {
  alert('Element clicked through function!');
});
```

#### How to trigger an event in JavaScript?

```
var el = document.querySelector('input[type="text"]');
el.click(); // for any element
el.focus(); // for inputs and textareas
el.blur();
var my_form = document.querySelector('form'); // for form elements
my_form.submit();
my_form.reset();
```

#### What is a callback function? Tell some examples of its usage.

- A **_callback function_** is a function passed into another function as an argument.

```
function greeting(name) {
  alert('Hello ' + name);
}
function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}
processUserInput(greeting);
```

#### What is a Python decorator? How does it work? Tell some examples of its usage.

- **_Decorators_** wrap functions, modifying the behavior of the code before and after a target function execution,
  without the need to modify the function itself:

```
def decorator(func):
    def func_wrapper(name):
        print("Wrapper function first part")
        print(func(name))
        print("Wrapper function last part")
    return func_wrapper
@decorator
def function_to_wrap(text_parameter):
   return "Wrapped function. Its parameter: " + text_parameter
```

#### What is the difference between synchronous and asynchronous execution?

- When you execute something synchronously, you wait for it to finish before moving on to another task. When you
  execute something asynchronously, you can move on to another task before it finishes.

---

## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?

- In order to connect to the database, we create a connection to it. Any queries and operations are performed
  using the connection, which is closed after the work is finished.
- Use environment variables to save personal data, like database password, database name, host and user name.

#### When do you use the DISTINCT keyword in SQL?

- The SQL DISTINCT keyword is used in conjunction with the SELECT statement to eliminate all the duplicate records and
  fetching only unique records.

#### What are aggregate functions in SQL? Give 3 examples.

- Aggregate expressions (or functions) allow you to summarize information about a group of rows of data:
- i.e. ARRAY_AGG function is used to concatenate the input values including null into an array.

```
SELECT COUNT(*) FROM table WHERE name='Paul';
SELECT name, AVG(salary) FROM table GROUP BY name;
SELECT ARRAY_AGG(salary) FROM table;
```

#### What kind of JOIN types do you know in SQL? Could you give examples?

- INNER JOIN is a process that matches rows from the first table and the second table which have the same key (as
  defined by the ON constraint) to create a result row with the combined columns from both tables.
- When joining table A to table B, a LEFT JOIN includes rows from A regardless of whether a matching row is
  found in B.
- The RIGHT JOIN is similar, but reversed, keeping rows in B regardless of whether a match is found in A.
- FULL OUTER JOIN means that rows from both tables are kept, regardless of whether a matching row exists in
  the other table.

#### What are the constraints in sql?

- Constraints are the rules enforced on data columns on table.
- Defining a data type for a column is a constraint in itself.

```
CREATE TABLE department1(
   id INT PRIMARY KEY      NOT NULL,
   dept           CHAR(50) NOT NULL,
   emp_id         INT      references company6(id)
);
```

#### What is a cursor in SQL? Why would you use one?

- The major function of a cursor is to retrieve data, one row at a time, from a result set, unlike the SQL commands
  which operate on all the rows in the result set at one time.
- Cursors are used when the user needs to update records in a singleton fashion or in a row by row manner, in a
  database table.

#### What are database indexes? When to use?

- Indexes are special lookup tables that the database search engine can use to speed up data retrieval.
- An index is a pointer to data in a table. An index in a database is very similar to an index in the back of a book.
- An index helps to speed up SELECT queries and WHERE clauses; however, it slows down data input, with UPDATE and
  INSERT statements.
- Indexes can be created or dropped with no effect on the data.

#### What are database transactions? When to use?

- A transaction is a unit of work that is performed against a database.
- For example, if you are creating a record, updating a record, or deleting a record from the table, then you are
  performing transaction on the table.
- It is important to control transactions to ensure data integrity and to handle database errors. Practically, you
  will club many SQL queries into a group and you will execute all of them together as a part of a transaction:

```
BEGIN;
...
COMMIT;
[ROLLBACK;]
```

#### What kind of database relations do you know? How to define them?

- There are three specific types of relationships that can exist between a pair of tables:
  - one-to-one = when a single record in the first table is related to only one record in the second table, and a
    single record in the second table is related to only one record in the first table.
  - one-to-many = when a single record in the first table can be related to one or more records in the second table,
    but a single record in the second table can be related to only one record in the first table.
  - many-to-many = when a single record in the first table can be related to one or more records in the second table
    and a single record in the second table can be related to one or more records in the first table.

#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?

```
SELECT * FROM table WHERE address LIKE '%Miskolc%';
```

#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?

- Call a stored procedure on your database server to write a log of the database changes.
- To track those changes made to tables in PostgreSQL you can write a generic changelog trigger.

---

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?

- XML is abbreviation for Extensible Markup Language whereas HTML stands for Hypertext Markup Language.
- XML is a markup language that defines a set of rules for encoding documents in a format that is both
  human-readable and machine-readable.
- XML is strict for closing tag while HTML is not strict. XML tags are extensible whereas HTML has limited tags.
- XML tags are not predefined whereas HTML has predefined tags.
- XHTML stands for EXtensible HyperText Markup Language and is a stricter, more XML-based version of HTML.
- XHTML is HTML defined as an XML application and is supported by all major browsers.

#### How to include a JavaScript file in a webpage?

- Internal:

```
<script>
    alert("Hello, world.");
</script>
```

- External:

```
<script src="script.js"></script>
```

#### How to include a CSS file in a webpage?

- Inline:

```
<p style="color: red">text</p>
```

- Internal:

```
<head>
    <title>CSS Example</title>
    <style>
        p {
            color: red;
        }
        a {
            color: blue;
        }
    </style>
</head>
```

- External (separate CSS file):

```
p {
    color: red;
}

a {
    color: blue;
}
```

#### How to select an element using its id in CSS?

```
#top {
    background-color: #ccc;
    padding: 20px
}
```

#### How to select elements using their class in CSS?

```
.intro {
    color: red;
    font-weight: bold;
}
```

#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?

```
.alpha.beta {
    color: red;
    font-weight: bold;
}
```

#### How to select all list items in all ordered lists on the page in CSS?

```
ol li {
    color: red;
    font-weight: bold;
}
```

#### How to select elements using their attributes in CSS?

```
input[type=text] { width: 200px; }
```

#### What are UX and UI?

- UX deals with the purpose and functionality of the product.
- UI deals with the quality of the interaction that the end-user has with the product.
- UI design has an artistic component as it relates to the design and interface with the product.

#### Please list some points that an application should fulfill to have good UX.

- Contrast - make the font bright not the background
- Font size
- Precise positioning
- Make it work with keyboard
- Cover all visual info with textual

#### What is XML, XSLT, DTD?

- XSLT (eXtensible Stylesheet Language Transformations) is the recommended style sheet language for XML. XSLT is far
  more sophisticated than CSS.
- With XSLT you can add/remove elements and attributes to or from the output file.
- A document type definition (DTD) is a set of markup declarations that define a document type for an SGML-family
  markup language (GML, SGML, XML, HTML).
- The purpose of a DTD (Document Type Definition) is to define the legal building blocks of an XML document

#### What is the difference between HTML and XML?

- Hypertext Markup Language (HTML) is the standard markup language for documents designed to be displayed in a
  web browser.
- XML stands for Extensible Markup Language. It is a text-based markup language derived from Standard Generalized
  Markup Language (SGML).
- HTML is used for the data presentation whereas the main purpose of XML was to store and transfer the data.
- HTML is a simple, predefined language while XML is the standard markup language to define other languages.

---

### Javascript

#### What is javascript?

- JavaScript is a lightweight, interpreted programming language. It is designed for creating network-centric
  applications.
- It is easy to implement because it is integrated with HTML. It is open and cross-platform.
- While it is most well-known as the scripting language for Web pages, many non-browser environments also use it,
  such as Node.js, Apache CouchDB and Adobe Acrobat.

#### When to use AJAX? Bring examples of its usage.

- AJAX = Asynchronous JavaScript and XML. AJAX is a technique for creating fast and dynamic web pages.
- AJAX allows web pages to be updated asynchronously by exchanging small amounts of data with the server behind the
  scenes.
- Almost all sites that pull in new content without a page reload (like Facebook, Gmail, Google Maps etc) use this
  same technique:

```
async function getUsersAsync(count) {
    let response = await fetch(`https://randomuser.me/api/?results=${count}`);
    let data = await response.json()
    let results = data.results;
    for (let result of results) {
        list.innerHTML += populateCard(result);
    }
}
getUsersAsync(5);
```

#### What is DOM and how to manipulate it from Javascript?

- DOM is the Document Object Model. It is the API in HTML and XML document.
- JavaScript Methods For DOM Manipulation:
  - querySelector() The querySelector() method returns the first element that matches one or more CSS selectors
  - querySelectorAll()
  - addEventListener()
  - removeEventListener()
  - createElement()
  - appendChild()
  - removeChild()
  - replaceChild()
  - cloneNode() When you have to create a new element that needs to be the same as an already existing element on
    the web page
  - insertBefore() method adds a specified child element before another child element.
  - createDocumentFragment() method insert multiple elements in bulk, such as adding multiple rows to a table.
  - getComputedStyle() returns the read-only computed values of all the CSS properties of a specified HTML element.
  - setAttribute()
  - getAttribute()
  - removeAttribute()

#### What are events and how/why to use them in Javascript?

- JavaScript's interaction with HTML is handled through events that occur when the user or the browser manipulates
  a page.
- When the page loads, it is called an event. When the user clicks a button, that click too is an event. Other
  examples include events like pressing any key, closing a window, resizing a window, etc.
- Events are a part of the Document Object Model (DOM) Level 3 and every HTML element contains a set of events
  which can trigger JavaScript Code.
- These events are used to execute JavaScript coded responses, which cause buttons to close windows,
  messages to be displayed to users, data to be validated, and virtually any other type of response imaginable.

#### What is event bubbling/capturing? How would you use it?

- Event bubbling and capturing are two ways of event propagation in the HTML DOM API, when an event occurs in an
  element inside another element, and both elements have registered a handle for that event.
- bubbling = the event is first captured and handled by the innermost element and then propagated to outer elements.
- capturing = the event is first captured by the outermost element and propagated to the inner elements.
- We can use the **_addEventListener(type, listener, useCapture)_** to register event handlers for in either
  bubbling (default, useCapture=false) or capturing mode.
- To use the capturing model pass the third argument as true.

#### What is JSON and how do we use it?

- JSON is JavaScript Object Notation = format is often used for serializing and transmitting structured data over
  a network connection.
- It is used primarily to transmit data between a server and web application, serving as an alternative to XML.

---

## Software engineering

### Version control

#### What type of branching strategy would you use?

1. Centralized Workflow:
   - uses a central repository to serve as the single point-of-entry for all changes to the project.
   - the default development branch is called master and all changes are committed into this branch.
   - This workflow doesn’t require any other branches besides master.
2. Feature branching:
   - all feature development should take place in a dedicated branch instead of the master branch.
   - the master branch should never contain broken code.
3. Forking Workflow:
   - gives every developer a server-side repository.
   - each contributor has not one, but two Git repositories: a private local one and a public server-side one.
   - does not use a single server-side repository to act as the “central” codebase.

#### What would you do if you find a bug on the production code (master branch)?

- Create a hotfix branch from your "production" commit, fix bug, and merge it to master and develop.

#### How can you move changes from one branch to another in GIT?

- You can create a new branch pointing to the current commit using "git branch branchname"
  (or "git checkout -b branchname" if you want to check it out directly).
- This will basically duplicate your master branch, so you can continue working on there.

#### How does a VCS help with code reviews?

- Because VCS keeps track of:
  - a complete long-term change history of every file. This means every change made by many individuals over time.
  - the ability to work on independent streams of changes.
  - each change made to the software and connects it to project management and bug tracking software such as
    Jira, and being able to annotate each change with a message describing the purpose and intent of the change

#### What is your favorite git command? Why?

```
git log --graph --decorate --oneline
```

- It will draw a text based graph of the commits on the left hand side of the commit messages, with the names of
  branches or tags of the commits on a single line.

#### What does remote/local mean in Git?

- **_git remote_** = lists the remote connections you have to other repositories.
- **_git remote -v_** = same including the URL of each connection.
- **_git remote add \<name> \<url>_** = create a new connection to a remote repository.
- **_git remote rm \<name>_** = remove the connection to the remote repository called <name>.

---

### DevOps

#### Why is it good to use a package manager software?

- A package manager software is a programming language’s tool to create project environments and easily import external
  dependencies.
- **_pip_** allows you to add dependencies to your projects for your given Python instalments.

#### Why is it good to use a virtual environment for a project?

- **_virtualenv_** is a tool to create isolated Python environments. It solves a very specific problem: it allows
  multiple Python projects that have different (and often conflicting ) requirements, to coexist on the same computer.

---

### Networks

#### What kind of HTTP status codes do you know?

- 1xx Informational
  - Request received, continuing process.
- 2xx Success
  - action requested by the client was received, understood, accepted and processed successfully.
- 3xx Redirection
  - client must take additional action to complete the request.
- 4xx Client Error
  - client seems to have erred.
- 5xx Server Error
  - server failed to fulfill an apparently valid request.

#### What is a API?

- is a gate (interface) in a software, that allows connectivity for the outside word. Usually one API endpoint lets
  you interact with one certain part of the given software.

#### What is REST API?

- Representational state transfer (REST) or RESTful is an architectural style used for web development, aiming for fast
  performance, reliability and the ability to scale (to grow and easily support extra users).
- RESTful API ensures other developers can understand the structure easily compared to creating endpoints without a
  standard.

#### What is JSON? When to use?

- JSON or JavaScript Object Notation is a lightweight text-based open standard designed for human-readable data
  interchange.
- JSON format is used for serializing and transmitting structured data over network connection.
- It is primarily used to transmit data between a server and web applications.
- Web services and APIs use JSON format to provide public data.

#### What is TCP/IP? What layers does it define, what are they responsible for?

- The Internet works by using a protocol called TCP/IP, or Transmission Control Protocol/Internet Protocol.
- TCP/IP allows one computer to talk to another computer via the Internet through compiling packets of data and
  sending them to right location.
- TCP/IP model is practical model and is used in the Internet, which combines the two layers (Physical and Data link
  layer) into one layer i.e. Host-to-Network layer:
  - **_Application Layer_**
    - provides different services such as manipulation of information, retransferring the files
      of information, distributing the results etc.
    - functions such as LOGIN or password checking are also performed by the application layer.
    - Protocols used in this layer: TELNET, FTP, SMTP, DN, HTTP, NNTP
  - **_Transport Layer_**
    - uses TCP and UDP protocols for end to end transmission.
    - TCP is reliable and connection oriented protocol, that also handles flow control.
  - **_Internet Layer_**
    - allows the host to insert packets into network and then make them travel independently to the destination.
    - the order of receiving the packet can be different from the sequence they were sent.
    - Protocols used in this layer: Internet Protocol (IP).
  - **_Host-to-Network Layer_**
    - the host has to connect to network using some protocol, so that it can send IP packets over it.
    - Protocols used in this layer: ARPANET, SATNET, LAN, packet radio

#### What’s the difference between TCP and UDP?

- User Datagram Protocol is used for broadcast and multicast type of network transmission.
- UDP protocol works almost similar to TCP, but it throws all the error-checking out.
- TCP is a connection-oriented protocol, whereas UDP is a connectionless protocol.
- TCP reads data as streams of bytes, and the message is transmitted to segment boundaries. TCP rearranges data
  packets in the specific order.
- UDP messages contain packets that were sent one by one. It also checks for integrity at the arrival time. UDP
  protocol has no fixed order because all packets are independent of each other.
- The speed for TCP is slower while the speed of UDP is faster.
- UDP is used if both client and server may separately send packets, and occasional delay is also not acceptable. (e.g
  . multiplayer games).

#### How does an HTTP Request look like? What are the most relevant HTTP header fields?

- HTTP header fields provide required information about the request or response, or about the object sent in the
  message body. There are four types of HTTP message headers:
  - _General-header_: These header fields have general applicability for both request and response messages.
    - Connection
  - _Client Request-header_: These header fields have applicability only for request messages.
    - Accept-Language
    - Accept-Encoding
  - _Server Response-header_: These header fields have applicability only for response messages.
    - Location : absoluteURI
    - Set-Cookie: NAME=VALUE; OPTIONS
  - _Entity-header_: These header fields define meta information about the entity-body or, if no body is present
    , about the resource identified by the request.
    _ Allow: GET, HEAD, PUT, POST
    _ Content-Length \* Content-Type
- **_GET_** request

```
GET /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.tutorialspoint.com

Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive
```

- **_POST_** request

```
POST /cgi-bin/process.cgi HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.tutorialspoint.com

Content-Type: application/x-www-form-urlencoded
Content-Length: length

Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive

licenseID=string&content=string&/paramsXML=string
```

#### How does an HTTP Response look like? What are the most relevant HTTP header fields?

- The request method indicates the method to be performed on the resource identified by the given Request-URI.
- Most relevant request methods:
  - GET method is used to retrieve information from the given server using a given URI. Requests using GET
    should only retrieve data and should have no other effect on the data.
  -     POST request is used to send data to the server, for example, customer information, file upload, etc
    . using HTML forms.
  -     PUT Replaces all the current representations of the target resource with the uploaded content.
  - DELETE Removes all the current representations of the target resource given by URI.
- HTTP Response example:

```
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
Content-Length: 88
Content-Type: text/html
Connection: Closed
```

#### What is DNS? How does it work?

- DNS (Domain Name Server) is a host name to IP address translation service. It is a distributed database
  implemented in a hierarchy of name servers. It is an application layer protocol for message exchange between clients
  and servers.
- Domain name system comprises of:
  - Domain Name
    - a symbolic string associated with an IP address.
    - there are several domain names available; some of them are generic such as com, edu, gov, net etc,
    - some country level domain names such as au, in, za, us etc.
  - Domain Name Space
    - refers a hierarchy in the internet naming structure, which has multiple levels (from 0 to 127), with a
      root at the top: edu &rarr; colorado &rarr; cs &rarr; kim
    - each domain can be partitioned into sub domains and these can be further partitioned and so on.
  - Name Server
    - contains the DNS database, that comprises of various names and their corresponding IP addresses.
    - it is not possible for a single server to maintain entire DNS database, the information is distributed
      among many DNS servers.
    - The entire name space is divided into the zones
  - Zones
    - a collection of nodes (sub domains) under the main domain. The server maintains a database called zone file
      for every zone.

#### What is a web server?

- It is a computer where the web content is stored. Basically web server is used to host the web sites but there exists
  other web servers also such as gaming, storage, FTP, email etc.

#### Explain the client-server architecture.

- works with a system of request and response. The client sends a request to the server and the server responds with
  the desired information.
- The client and server follow a common communication protocol so they can easily interact with each other. All the
  communication protocols are available at the application layer.
- A server can only accommodate a limited number of client requests at a time. So it uses a system based to priority
  to respond to the requests.
- A web server is a client server computing system. It returns the web pages to the clients that requested them.

#### What would you use a session for?

- A session creates a file in a temporary directory on the server where registered session variables and their
  values are stored. This data will be available to all pages on the site during that visit.
- A session ends when the user closes the browser or after leaving the site, the server will terminate the session
  after a predetermined period of time, commonly 30 minutes duration.

#### What would you use a cookie for?

- Cookies are text files stored on the client computer and they are kept for tracking purposes. Server script
  sends a set of cookies to the browser.
- For example name, age, or identification number etc. The browser stores this information on a local machine for
  future use.
- When next time browser sends any request to web server then it sends those cookies information to the server and
  server uses that information to identify the user.

---

## Software Development Methodologies

#### What kind of software development methodologies do you know? What are the main features of these?

- **_Waterfall Model_**
  - Requirement Gathering and analysis
  - System Design
  - Implementation
  - Integration and Testing
  - Deployment of system
  - Maintenance
- **_Agile Model_**
  - User Stories &rarr; features customers might one day like to see in their software.
  - Estimation &rarr; make some really accurate predictions about the future while based on what was done in the past.
  - Iterations &rarr; a short one to two week period where a team takes a couple of their customers most important
    user stories and builds them completely as running-tested-software.
  - Planning &rarr; measuring the speed a team can turn user stories into working, production-ready software and
    then using that to figure out when they’ll be done.
  - Unit Testing &rarr; snippets of test code developers write to prove to themselves that what they are developing
    actually works.
  - Refactoring &rarr; maintaining order in the design
  - Burndown Charts &rarr; a chart that shows how quickly the customer's user stories are burned. It shows the total
    effort against the amount of work delivered for each iteration.

#### What are the SCRUM roles?

- Scrum is an efficient framework within which you can develop software with teamwork. It is based on agile principles.
- The Scrum Team consists of three roles, namely a ScrumMaster, a Product Owner, and the Team:
  - ScrumMaster &rarr; the keeper of the scrum process. He/she is responsible for:
    - making the process run smoothly
    - removing obstacles that impact productivity
    - organizing and facilitating the critical meetings
  - Product Owner &rarr; is the sole person responsible for managing the Product Backlog. Product Backlog
    management includes:
    - Expressing Product Backlog items clearly.
    - Ordering the Product Backlog items to best achieve goals and missions.
    - Optimizing the value of the work the Team performs.
    - Ensuring that the Product Backlog is visible, transparent, and clear to all, and shows what the Team will
      work on further.
    - Ensuring that the Team understands items in the Product Backlog to the level needed.
  - The Team &rarr; comprises of analysts, designers, developers, testers, etc. as appropriate and as relevant to
    the project.
    - The Team size should be kept in the range from five to nine people, if possible.

#### What are the SCRUM ceremonies?

- Sprint Planning Meeting &rarr; discuss and estimate the high priority user stories, and forecast the work which
  can be consummate in the current sprint.
- Daily Stand-up Meeting &rarr; enhances the team communications, increases visibility of the work, allows quick
  decisions making abilities, identifying and removing the obstacles.
- Sprint Review Meeting &rarr; also called as Demo or Showcase meeting held at the end of the sprint to demonstrate
  the actual working software to review and get the feedback.
- Sprint Retrospective Meeting &rarr; collect the feedback on how the team worked in the just concluded sprint. And
  based on those input the team identify the improvements for the next sprints.

#### What are the SCRUM artifacts?

- Scrum Artifacts provide key information that the Scrum Team and the stakeholders need to be aware of for
  understanding the product under development, the activities done, and the activities being planned in the project:
  - Product Backlog &rarr; list of items that have the attributes of a description, order, estimate, and value. These
    items are normally termed as User Stories.
  - Sprint Backlog &rarr; set of Product Backlog items selected for the Sprint, plus a plan for delivering the
    product Increment and realizing the Sprint Goal.
  - Increment &rarr; the sum of all the Product Backlog items completed during a Sprint combined with the
    increments of all previous Sprints.
  - Sprint Burn-Down Chart &rarr; the total work remaining in the Sprint Backlog.

#### What is the main goal of a retrospective meeting?

- A lesson learned discussions to improve the way of work for the betterment of the team and the project.

#### Explain, when would you recommend to use the waterfall methodology?

- Waterfall methodology is recommended when:
  - Requirements are very clear and fixed.
  - There are no ambiguous requirements.
  - Ample resources with required expertise are available freely.
  - The client has high confidence in the organization.

---

---

<br/><br/>
<br/><br/>
<br/><br/>

# OOP Questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?

- In systems design, a **_fail-fast_** system is one which immediately reports at its interface any condition that is
  likely to indicate a failure.
- **_Fail-fast_** systems are usually designed to stop normal operation rather than attempt to continue a possibly flawed
  process.
- The **_fail fast_** principle stands for stopping the current operation as soon as any unexpected error occurs.
- Adhering to this principle generally results in a more stable solution.

---

## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?

- A "singly linked list" is a type of linked list that is unidirectional, that is, it can be traversed in only one direction from head to the last node (tail).
- Traverse linked list using two pointers.
- Move one pointer by one and other pointer by two.
- When the fast pointer reaches end slow pointer will reach middle
  of the linked list.

```java
// Java program to find middle of linked list
class LinkedList
{
    Node head; // head of linked list

    /* Linked list node */
    class Node
    {
        int data;
        Node next;
        Node(int d)
        {
            data = d;
            next = null;
        }
    }

    /* Function to print middle of linked list */
    void printMiddle()
    {
        Node slow_ptr = head;
        Node fast_ptr = head;
        if (head != null)
        {
            while (fast_ptr != null && fast_ptr.next != null)
            {
                fast_ptr = fast_ptr.next.next;
                slow_ptr = slow_ptr.next;
            }
            System.out.println("The middle element is [" +
                                slow_ptr.data + "] \n");
        }
    }
}
```

#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?

1. Declare and initialize an array.
2. Duplicate elements can be found using two loops.
3. The outer loop will iterate through the array from 0 to length of
   the array. The outer loop will select an element.
4. The inner loop will be used to compare the selected element with the rest of the elements of the array.
5. If a match is found which means the duplicate element is found then, display the element.

```java
public class DuplicateElement {
    public static void main(String[] args) {
        System.out.println("Duplicate elements in given array: ");
        //Searches for duplicate element
        for(int i = 0; i < arr.length; i++) {
            for(int j = i + 1; j < arr.length; j++) {
                if(arr[i] == arr[j])
                    System.out.println(arr[j]);
            }
        }
    }
}
```

#### What is a linked list? How to find if a linked list has a loop?

1. **_Linked List_** is a part of the Collection framework present in _java.util_ package.
2. This class is an implementation of the LinkedList data structure which is a linear data structure where the elements
   are not stored in contiguous locations and every element is a separate object with a data part and address part.
3. The elements are linked using pointers and addresses. Each element is known as a **node**.
4. The nodes cannot be accessed directly instead we need to start from the head and follow through the link to reach
   to a node we wish to access.
5. Advantages of **_Linked List_**:
   - Insertion and Deletion Operations are Easier.
   - Efficient Memory Utilization, i.e. no need to pre-allocate memory.
   - Faster Access time,can be expanded in constant time without memory overhead.

- To find if a linked list has a loop:
  - Have two references to the list and move them at different speeds.
  - If the linked list has a loop they will definitely meet.
  - Else either of the two references(or their next) will become null.

```java
public class LinkedList {
    boolean hasLoop(Node first) {

        if(first == null) // list does not exist..so no loop either
            return false;

        Node slow, fast; // create two references.

        slow = fast = first; // make both refer to the start of the list

        while(true) {

            slow = slow.next;          // 1 hop

            if(fast.next != null)
                fast = fast.next.next; // 2 hops
            else
                return false;          // next node null => no loop

            if(slow == null || fast == null) // if either hits null..no loop
                return false;

            if(slow == fast) // if the two ever meet...we must have a loop
                return true;
        }
    }
}
```

#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?

- ArrayList has O(n) time complexity for arbitrary indices of add/remove, but O(1) for the operation at the end of the list.
- LinkedList has O(n) time complexity for arbitrary indices of add/remove, but O(1) for operations at end/beginning of
  the List.
- Hashmap has O(1) time complexity for both get and put operation.
- A Binary Search Tree data structure, first creates a binary search tree from the elements of the input list or
  array and then performs an in-order traversal on the created binary search tree to get the elements in sorted order.
- Average Case Time Complexity in a Binary Search Tree O(n log n).

#### How does HashMap work?

- HashMap implementation is based on the the principles of a hashtable: key-value pairs are stored in what is known as
  buckets which together make up what is called a table, which is actually an internal array.
- When a value is added to the map under a key, the hashCode() API of the key object is called to retrieve what is
  known as the initial hash value.
- Next, the hash() API of the hash map is called internally to compute the final hash value using the initial hash value.
- This final hash value ultimately boils down to an index in the internal array or what we call a bucket location.

#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)

- If immutable, the object's hashcode wont change and it allows caching the hashcode of different keys which makes
  the overall retrieval process very fast.
- Since Strings are very popular as HashMap key, it's important for them to be immutable so that they can retrieve
  the value object which was stored in HashMap.

---

### Other

#### What is a garbage collector, in a nutshell?

- The garbage collector, or just collector, attempts to reclaim garbage, or memory occupied by objects that are no
  longer in use by the program.
- In Java, as long as an object is being referenced, the JVM considers it alive. Once an object is no longer referenced
  and therefore is not reachable by the application code, the garbage collector removes it and reclaims the unused memory.

---

## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?

- Casting is the process of making a variable behaves as a variable of another type.
- Casting from a subclass to a superclass is called upcasting. Typically, the upcasting is implicitly performed by
  the compiler.
- Downcasting is casting from a superclass to a subclass.

```java
// Parent class
class Parent {
	String name;
	// A method which prints the signature of the parent class
	void method() { System.out.println("Method from Parent"); }
}

// Child class
class Child extends Parent {
	int id;
	// Overriding the parent method to print the signature of the child class
	@Override
	void method() { System.out.println("Method from Child"); }
}
// Upcasting and downcasting
public class Example {
	public static void main(String[] args) {
		// Upcasting
		Parent p = new Child();
		p.name = "Test";
		// This parameter is not accessible p.id = 1;
		System.out.println(p.name);
		p.method();

		// Trying to Downcasting Implicitly
		// Child c = new Parent(); - > compile time error

		// Downcasting Explicitly
		Child c = (Child) p;

		c.id = 1;
		System.out.println(c.name);
		System.out.println(c.id);
		c.method();
	}
}
```

#### Which order should we catch the exceptions? Why?

- The order is whatever matches first, gets executed.
- If the first catch matches the exception, it executes, if it doesn't, the next one is tried and on and on until one
  is matched or none are.
- When catching exceptions you want to always catch the most specific first and then the most generic (as
  RuntimeException or Exception).

---

### Object-oriented

#### What is a class?

- A class is a blueprint from which individual objects are created. Simply put, a class represent a definition or a
  type of object. In Java, classes can contain fields, constructors, and methods.
- A class is a group of objects which have common properties. It is a logical entity. It can't be physical.
- A class in Java can contain:
  - Fields
  - Methods
  - Constructors
  - Blocks
  - Nested class and interface

#### What is an object?

- An object is an instance of a class. An entity that has state and behavior is known as an object.
- State: represents the data (value) of an object.
- Behavior: represents the behavior (functionality) of an object.

#### What is a constructor?

- A Java constructor is special method that is called when an object is instantiated. In other words, when you use
  the "new" keyword.
- The purpose of a Java constructor is to initializes the newly created object before it is used.
- It has no return type, because a constructor implicitly returns the type of the object that it creates.

#### Do we require parameter for constructors?

- There are two types of constructors in Java: no-arg constructor, and parameterized constructor:
  - a _no-argument constructor_ takes no arguments. It is called "Default Constructor" when it doesn't have any
    parameter.
  - a constructor which has a specific number of parameters is called a _parameterized constructor_. It is used to
    provide different values to distinct objects. However, you can provide the same values also.

#### What is an interface?

- A Java interface is a bit like a Java class, except a Java interface can only contain method signatures and fields.
- A Java interface is not intended to contain implementations of the methods, only the signature (name, parameters
  and exceptions) of the method.

```java
public interface MyInterface {

    public String hello = "Hello";

    public void sayHello();
}
```

#### What are access modifiers?

- A Java access modifier specifies which classes can access a given class and its fields, constructors and methods.
- Access modifiers can be specified separately for a class, its constructors, fields and methods.
- Classes, fields, constructors and methods can have one of four different Java access modifiers:
  1. default (no keyword): all members are visible within the same package but aren't accessible from other packages.
  2. public: all other classes in all packages will be able to use it.
  3. private: is accessible from the same class only.
  4. protected: same package (as with package-private access level) and in addition from all subclasses of its class.

#### What is data hiding?

- It is hiding the state or internal representation of an object from the consumer of an API and providing publicly
  accessible methods bound to the object for read-write access.
- This allows for hiding specific information and controlling access to internal implementation (Encapsulation).

#### Can a static method use non-static members?

- If a field is declared static, then exactly a single copy of that field is created and shared among all instances
  of that class
- Non-static data _cannot_ be used in static methods because there is no well-defined variable to operate on.
- Non-static variables are part of the objects themselves. To use a non-static variable, you need to specify which
  instance of the class the variable belongs to.

#### What is the difference between hiding a static method and overriding an instance method?

- If a subclass defines a static method with the same signature as a static method in the superclass, then the
  method in the subclass _hides_ the one in the superclass.
- The distinction between hiding a static method and overriding an instance method has important implications:
  - The version of the overridden instance method that gets invoked is the one in the subclass.
  - The version of the _hidden static method_ that gets invoked depends on whether it is invoked from the superclass
    or the subclass.

#### Define the following terms: Instantiation, Attribute, Method

- Instantiation: The new keyword is a Java operator that creates the object.
- Attribute: another term for a field. It's typically a public constant or a public variable that can be accessed
  directly.
- Method: a collection of statements that are grouped together to perform an operation.

#### Could we access a static variable (or method) from a non-static method? Why?

- Non-static methods can access any static method and static variable also, without using the object of the class, because static variables belong to a class and can be called from anywhere, depending upon their access modifier.

#### Could we access a non-static variable (or method) from a static method? Why?

- In static method, the method can only access only static data members and static methods of another class or same class but cannot access non-static methods and variables, because for the non-static variable, there is a need for an object instance to call the variables.
- However, in order to access a non-static variable/method from a static method in Java, you need to first create an object of the class whose non-static members or non-static method you want to access.

#### How many instances you have of a static variable of a given class?

- Only one instance of a static member exists, even if you create multiple objects of the class, or if you don't
  create any.

#### Why is it not a good practice to write a lot of static methods?

- The problem is the code becomes hard wired to that static method. There is no easy way to replace the reference to
  the static method with something else, and if you are testing your code using automated tests, this is exactly what
  you want to do.

#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?

- Since static variables belong to a class, they can be accessed directly using class name and don't need any object
  reference.
- Static fields can be accessed without object initialization.
- Static methods also belong to a class instead of the object, and so they can be called without creating the object
  of the class in which they reside.
- Reasons to Use static Fields:
  - When the value of variable is independent of objects.
  - When the value is supposed to be shared across all objects.

#### What is the ‘this’ reference?

- The **_this_** is a keyword in Java which is used as a reference to the object of the current class, within an
  instance method or a constructor.
- Using this you can refer the members of a class such as constructors, variables and methods.

#### What are base class, subclass and superclass?

- A class that is derived from another class is called a _**subclass**_ (also a _**derived class**_, _**extended
  class**_, or _**child class**_).
- The class from which the subclass is derived is called a _**superclass**_ (also a _**base class**_ or a _**parent
  class**_).

#### Draw an object oriented family (as entities, with relations) on the whiteboard.

![UML Diagram](WardrobeUMLDiagram.png)

#### Difference between overloading and overriding?

- _**Overloading**_ occurs when two or more methods in one class have the same method name but different parameters.
- _**Overriding**_ means having two methods with the same method name and parameters (i.e., method signature). One of
  the methods is in the parent class and the other is in the child class.

#### What are the Object Oriented Principles? Explain the concepts with realistic examples!

1. Encapsulation: hiding the state or internal representation of an object from the consumer of an API.

```java
public class Car {

    // ...
    private int speed;

    public int getSpeed() {
        return color;
    }

    public void setSpeed(int speed) {
        this.speed = speed;
    }
    // ...
}
```

2. Inheritance: mechanism that allows one class to acquire all the properties from another class by inheriting the
   class.

```java
public class Vehicle {
    private int wheels;
    private String model;
    public void start() {
        // the process of starting the vehicle
    }

    public void stop() {
        // process to stop the vehicle
    }

    public void honk() {
        // produces a default honk
    }

}
public class Car extends Vehicle {
    private int numberOfGears;

    public void openDoors() {
        // process to open the doors
    }
}
```

3. Polymorphism: the ability of an OOP language to process data differently depending on their types of inputs.

- method overloading (method read() has three different forms with different functionalities):

```java
public class TextFile extends GenericFile {
    //...

    public String read() {
        return this.getContent()
          .toString();
    }

    public String read(int limit) {
        return this.getContent()
          .toString()
          .substring(0, limit);
    }

    public String read(int start, int stop) {
        return this.getContent()
          .toString()
          .substring(start, stop);
    }
}
```

- method overrriding (A child class overrides the getFileInfo() method):

```java
public class GenericFile {
    private String name;

    //...

    public String getFileInfo() {
        return "Generic File Impl";
    }
}
public class ImageFile extends GenericFile {
    private int height;
    private int width;

    //... getters and setters

    public String getFileInfo() {
        return "Image File Impl";
    }
}
```

4. Abstraction: hiding the complex implementation details of a program, exposing only the API required to use the
   implementation. In Java, we achieve abstraction by using interfaces and abstract classes.

```java
public abstract class BoardGame {
    public abstract void play();
    //... concrete methods
}
public interface Electronic {
    // Constant variable
    String LED = "LED";
    // Abstract method
    int getElectricityUse();
    // Static method
    static boolean isEnergyEfficient(String electtronicType) {
        if (electtronicType.equals(LED)) {
            return true;
        }
        return false;
    }
    //Default method
    default void printDescription() {
        System.out.println("Electronic Description");
    }
}
```

#### What is method overloading?

- Overloading allows different methods to have the same name, but different signatures where the signature can differ
  by the number of input parameters or type of input parameters or both.
- Overloading is related to compile-time (or static) polymorphism.

```java
class Adder{
    static int add(int a,int b){return a+b;}
    static int add(int a,int b,int c){return a+b+c;}
}
```

#### What is method overriding?

- Overriding is a feature that allows a subclass or child class to provide a specific implementation of a method that
  is already provided by one of its super-classes or parent classes.
- When a method in a subclass has the same name, same parameters or signature, and same return type(or sub-type) as a
  method in its super-class, then the method in the subclass is said to override the method in the super-class.

```java
// Base Class
class Parent {
    void show()
    {
        System.out.println("Parent's show()");
    }
}

// Inherited class
class Child extends Parent {
    // This method overrides show() of Parent
    @Override
    void show()
    {
        System.out.println("Child's show()");
    }
}
```

#### Explain how object oriented languages attempt to simplify memory management for Programmers.

- Java objects reside in an area called the heap. The heap is created when the JVM starts up and may increase or
  decrease in size while the application runs.
- When the heap becomes full, garbage is collected. During the garbage collection objects that are no longer used are
  cleared, thus making space for new objects.

#### Explain the “Single Responsibility” principle!

- This principle states that each class should have one responsibility, one single purpose.
- This means that a class will do only one job, which leads us to conclude it should have only one reason to change.

#### What is an object oriented program? Explain, show.

- An OOP program model real-life entities: classes are blueprints or templates for objects. We use them to describe
  types of entities.
- On the other hand, objects are living entities, created from classes. They contain certain states within their
  fields and present certain behaviors with their methods.

```java
class Car {
    // fields
    String type;
    String model;
    String color;
    int speed;
    // constructor
    Car(String type, String model, String color) {
        this.type = type;
        this.model = model;
        this.color = color;
    }
    // methods
    int increaseSpeed(int increment) {
        this.speed = this.speed + increment;
        return this.speed;
    }
}
public class Implement {
    public static void main(String[] args) {
        Car focus = new Car("Ford", "Focus", "red");
        Car auris = new Car("Toyota", "Auris", "blue");
        Car golf = new Car("Volkswagen", "Golf", "green");
    }
}
```

#### How do you make a class immutable? What do you need to watch out for?

- Immutable class means that once an object is created, we cannot change its content.
- In Java, all the wrapper classes (like Integer, Boolean, Byte, Short) and String class is immutable.
- Following are the requirements:
  - The class must be declared as final (So that child classes can’t be created)
  - Data members in the class must be declared as final (So that we can’t change the value of it after object creation)
  - A parameterized constructor
  - Getter method for all the variables in it
  - No setters(To not have the option to change the value of the instance variable)

#### How many instances can be created for an abstract class?

- We cannot create an instance of an abstract class because it does not have a complete implementation.

---

## Programming languages

### Java

#### What is autoboxing and unboxing?

- _**Autoboxing**_ is the automatic conversion that the Java compiler makes between the primitive types and their
  corresponding object wrapper classes.
- For example, converting an int to an Integer, a double to a Double, and so on.
- If the conversion goes the other way, this is called _**unboxing**_.

#### If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?

- The positive number could be stored in an _**int**_.

#### What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?

- "Golden rule": limit the scope of variables and constants to the smallest necessary.
- Lifetime of a variable refers to how long the variable stays alive in memory.

#### What is the purpose of the ‘equals()’ method?

- The equals method for class Object implements the most discriminating possible equivalence relation on objects;
- That is, for any non-null reference values x and y, this method returns true if and only if x and y refer to the
  same object (x == y has the value true).

#### What is the difference between '==' and 'equals()'?

- '==' checks if both objects point to the same memory location whereas 'equals()' evaluates to the comparison of
  values in the objects

#### What does the ‘static’ keyword mean?

- The keyword static indicates that the particular member belongs to a type itself, rather than to an instance of
  that type.
- This means that only one instance of that static member is created which is shared across all instances of the class.

#### Why is the main() method declared as static? Explain.

- Java main() method is always static, so that compiler can call it without the creation of an object or before the
  creation of an object of the class.

#### What is the default access modifier in a class?

- Default access modifier means we do not explicitly declare an access modifier for a class, field, or method.
- A variable or method declared without any access control modifier is available to any other class in the same package.

#### What is the JVM?

- JVM (Java Virtual Machine) is an abstract machine.
- It is a specification that provides runtime environment in which java bytecode can be executed.

#### What is the difference between the JRE and the JDK?

- JDK is an abstract machine. It is a specification that provides runtime environment in which Java bytecode can be
  executed.
- The difference between JDK and JRE is that JDK is the software development kit for java while JRE is the place
  where you run your programs.

#### What is the difference between long and Long?

- A Long is a class, or a reference type, defined in the standard library. It stores a reference to an object
  containing a value (a "box").
- A long on the other hand, is a primitive type and part of the language itself.

#### Can a long store bigger numbers than a Long?

- Every object contains a single value of the corresponding primitive type.
- Java has a two-fold type system consisting of primitives such as int, boolean and reference types such as Integer
  , Boolean. Every primitive type corresponds to a reference type.
- The process of converting a primitive type to a reference one is called _autoboxing_, the opposite process is called
  _unboxing_.

```
Integer j = 1;          // autoboxing
int i = new Integer(1); // unboxing
```

#### What kind of packages do you know under java.util.\* ? Bring at least 3 examples.

- Examples: ArrayList, Date, HashMap<K,V>, Random

#### What are the access modifiers in Java? Which one could we use for class?

- The access modifiers in Java specifies the accessibility or scope of a field, method, constructor, or class.
- Four access modifiers in java include public, private, protected and default.
- Private and Protected keywords cannot be used for classes and interfaces.

#### Can an “enum” contain methods in Java? Explain.

- The enum class body can include methods and other fields.
- The compiler automatically adds some special methods when it creates an enum. (For example, they have a static
  values method that returns an array containing all of the values of the enum in the order they are declared.)

#### When would you use a private/protected/public attribute? What is the difference?

- Private: only the class in which it is declared can see it.
- Protected: can be seen by subclasses or package members.
- Public: Everyone can see it.

#### How do you prevent developers from subclassing a class?

- Create Private Constructor.
- make each method final, so people can't override them.
- put check into constructor for class:

```
if (this.getClass() != abc.class) { throw new RuntimeException("Subclasses not allowed"); }
```

#### How do you prevent developers from overriding a method in a subclass?

- You can use private and static modifier to prevent method overriding.
- You should use final modifier to prevent overriding

#### How do you prevent developers from changing the value of a variable?

- Mark the fields as final. A final keyword in declaration of object instance means the variable can't be reassigned.

#### Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!

- Java has Currency class that represents the ISO 4217 currency codes.
- BigDecimal is the best type for representing currency decimal values.

#### What happens if you try to call something, that you have no access to, because of data hiding?

- Receive IllegalAccessException: access to method denied.

#### What happens if you try to delete/drop an item from an array, while you are iterating over it?

- Receive ConcurrentModificationException.

#### What happens if you try to delete/drop/add an item from a List, while you are iterating over it?

- A ConcurrentModificationException is thrown.

#### What happens if you try to add an item to the end of an array, while you are iterating over it?

- ConcurrentModificationException.

#### If you need to access the iterator variable after a for loop, how would you do it?

- You can provide your own counter.

#### Which interfaces extend the Collection interface in Java. Which classes?

1. Iterable Interface: The collection interface extends the iterable interface.
2. Collection Interface: This interface contains all the basic methods which every collection has like adding the
   data into the collection, removing the data, clearing the data.
3. List Interface: This is a child interface of the collection interface. This interface is dedicated to the data of
   the list type in which we can store all the ordered collection of the objects.

#### What is the connection between equals() and hashCode()? How are they used in HashMap?

- If two objects are equal according to the equals(Object) method, then calling the hashcode() method on each of the
  two objects must produce the same integer result.
- In HashMap, hashCode() is used to calculate the bucket and therefore calculate the index.
- equals() method is used to check that 2 objects are equal or not.

#### What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?

- Checked exceptions: are the exceptions that are checked at compile time.
  - eg: FileNotFoundException, IOException
- Unchecked exceptions: are the exceptions that are checked at run time (error inside the program logic).
  - eg: NullPointerException, ArrayIndexOutOfBoundsException, IllegalArgumentException.

#### What is Error in Java and how does it relate to Exception?

- Exceptions and errors both are subclasses of Throwable class.
- The error indicates a problem that mainly occurs due to the lack of system resources.
- Some of the examples of errors are system crash error and out of memory error.

#### When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?

- The finally block always executes when the try block exits.
- This ensures that the finally block is executed even if an unexpected exception occurs.

```java
public class Example {
    public void writeList() {
        PrintWriter out = null;

        try {
            System.out.println("Entering" + " try statement");

            out = new PrintWriter(new FileWriter("OutFile.txt"));
            for (int i = 0; i < SIZE; i++) {
                out.println("Value at: " + i + " = " + list.get(i));
            }
        } catch (IndexOutOfBoundsException e) {
            System.err.println("Caught IndexOutOfBoundsException: " +  e.getMessage());

        } catch (IOException e) {
            System.err.println("Caught IOException: " +  e.getMessage());

        } finally {
            if (out != null) {
                System.out.println("Closing PrintWriter");
                out.close();
            }
            else {
                System.out.println("PrintWriter not open");
            }
        }
    }
}
```

#### What is the largest number you can work with in Java?

- Integer MAX_VALUE is approx 2^31, which exceeds the 32bit memory.
- A guess is that BigInteger can grow as large as your ram.

#### When you use method overriding, can you change the access level of the method, from protected to public? Why?

- Yes, we can override a method by changing only the access modifiers in java pertaining the following rule:
  - The access level cannot be more restrictive than the overridden method's access level.

#### Can the main method be overridden? Explain your answer!

- You cannot override static methods and since the public static void main() method is static we cannot override it.

#### When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?

- If SuperClass does not declare an exception, then the SubClass can only declare unchecked exceptions, but not the checked exceptions.
- If SuperClass declares an exception, then the SubClass can only declare the child exceptions of the exception
  declared by the SuperClass, but not any other exception.
- If SuperClass declares an exception, then the SubClass can declare without exception.

#### When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?

- The overriding method can throw those checked exceptions, which have less scope than the exception(s) declared in
  the overridden method.

#### What does "final" mean in case of a variable, method or a class?

- When a variable is declared with final keyword, its value can't be modified, essentially, a constant.

#### What is the super keyword?

- The super keyword refers to superclass (parent) objects.
- It is used to call superclass methods, and to access the superclass constructor.

#### What are “generics”? When to use? Show examples.

- Generics enable types (classes and interfaces) to be parameters when defining classes, interfaces and methods.
- The difference is that the inputs to formal parameters are values, while the inputs to type parameters are types.

```java
/**
 * Generic version of the Box class.
 * @param <T> the type of the value being boxed
 */
public class Box<T> {
    // T stands for "Type"
    private T t;

    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```

- To instantiate this class, use the new keyword, as usual, but place <Integer> between the class name and the
  parenthesis:

```
Box<Integer> integerBox = new Box<Integer>();
```

#### What is the benefit of having “generic” containers?

- A Java compiler applies strong type checking to generic code and issues errors if the code violates type safety.
- Fixing compile-time errors is easier than fixing runtime errors, which can be difficult to find.

#### Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?

- Java Socket programming is used for communication between the applications running on different JRE.
- The client in socket programming must know two information: IP Address of Server, and Port number.

#### What is an annotation? What can be annotated and how? Show examples.

- Annotations are used to provide supplement information about a program.
- Annotations start with ‘@’ and do not change action of a compiled program.
- Annotations help to associate metadata (information) to the program elements (instance variables, constructors
  , methods, classes).
- Annotations are not pure comments as they can change the way a program is treated by compiler.

```java
class Base
{
     public void display()
     {
         System.out.println("Base display()");
     }
}
class Derived extends Base
{
     @Override
     public void display(int x)
     {
         System.out.println("Derived display(int )");
     }

     public static void main(String args[])
     {
         Derived obj = new Derived();
         obj.display();
     }
}
```

---

### C&#35;

#### Explain the purpose of IL and how does it relate to CLR?

- Intermediate Language (IL) is a product of compilation of code written in high-level .NET languages (such as C#, Visual Basic, F#). Once you compile your code written in one of these languages, you will get a _binary_ that is made out of IL. IL is independent from any specific language that runs on top of the runtime. Intermediate Language is sometimes also called Common Intermediate Language (CIL) or Microsoft Intermediate Language (MSIL).
- Common Language Runtime (CLR), regardless of the implementation (for example, Mono, .NET Framework, or .NET Core/.NET 5+) is in charge of taking the Intermediate Language code, compiling it into machine code and then executing it. CLR starts the process of Just-In-Time compiling, or JIT-ing your code from IL to machine code that can actually be run on a CPU.

#### What does “managed code” mean?

- “managed code” is just that: code whose execution is managed by a runtime. In .NET case, the runtime in question is called the CLR.
- This is in contrast with "unmanaged code" that is, essentially, a binary that the operating system (OS) loads into memory and starts. Everything else, from memory management to security considerations are a burden of the programmer.
- Managed code is written in one of the high-level languages that can be run on top of .NET. When you compile code written in those languages with their respective compiler, you don't get machine code. You get Intermediate Language code which the runtime then compiles and executes

#### What is an assembly?

- Assemblies form the fundamental units of deployment, version control, reuse, activation scoping, and security permissions for .NET-based applications.
- An assembly is a collection of types and resources that are built to work together and form a logical unit of functionality.
- Assemblies take the form of executable (.exe) or dynamic link library (.dll) files, and are the building blocks of .NET applications. They provide the common language runtime with the information it needs to be aware of type implementations.

#### What is the difference between an EXE and a DLL?

- If an assembly is compiled as a class library and provides types for other assemblies to use, then it has the file extension .dll (dynamic link library).
  - DLL cannot be executed standalone.
  - DLL cannot be directly executed as they're designed to be loaded and run by other programs.
  - DLL would share the same process and memory space of the calling application.
- If an assembly is compiled as an application, then it has the file extension .exe (executable file format).
  - EXE can be executed standalone.
  - EXE creates its separate process and memory space.

#### What is strong-typing versus weak-typing? Which is preferred? Why?

- Languages like Java, C# and Python are strongly typed. In these the type conversion needs to be explicitly handled.
- Strong typing means that the type check is done at compile time and weak typing means that the type check is done at run time. .NET languages incorporate strong typing.
- For scripts(JavaScript), you will usually want weak typing, because you want to write as much less code as possible.
- In big programs, strong typing can reduce errors at compile time.

#### What is a namespace?

- A namespace is a declarative region that provides a scope to the identifiers (the names of types, functions, variables, etc) inside it.
- Namespaces are used to organize code into logical groups and to prevent name collisions that can occur especially when your code base includes multiple libraries.

#### Explain sealed class in C#?

- Classes can be declared as sealed by putting the keyword _sealed_ before the class definition.
- A sealed class cannot be used as a base class. For this reason, it cannot also be an abstract class. Sealed classes prevent derivation.

#### What is explicit vs. implicit conversion? Give examples of both of them.

- Type conversions are operations of changing a value into a variable or method parameter of another type.

  - Implicit conversions: No special syntax is required because the conversion always succeeds and no data will be lost. Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes:

    ```c#
    int number = 128;
    double bigger = number;

    DerivedClass d = new DerivedClass();
    BaseClass b = d;
    ```

  - Explicit conversions (casts): Explicit conversions require a cast expression. Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons. Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.

  ```c#
    double mypi = 3.14;
    int a;
    a = (int)mypi;

    Opel o = new Opel();
    Car c = o;
    Opel oo = (Opel)c;
  ```

#### Is a struct stored on the heap or stack?

- In C#, Structs are not stored anywhere, local variables and fields are.
- Local variables are stored on stack no matter what type (class or struct) they have. The difference is that a local variable of struct type stores the struct instance and a local variable of reference types stores a reference to the class instance that's stored on the heap.
- Fields are stored in the object they belong too. If the object is of reference type then it's stored on the heap and so are its fields. If the object is of struct type then it may be stored on stack (as a local variable) or on the heap (as a field of another object).

#### Can a struct have methods?

- Structures can have methods, fields, indexers, properties, operator methods, and events.
- You can't declare a parameterless constructor. Every structure type already provides an implicit parameterless constructor that produces the default value of the type.
- A structure type can't inherit from other class or structure type and it can't be the base of a class. However, a structure type can implement interfaces.

#### Can DateTimes be null?

- DateTime itself is a value type. It cannot be null. No, DateTime is a struct in C# and structs (value types) can not be null.

#### List out the differences between Array and ArrayList in C#?

- Array must include System namespace to use array.
- ArrayList must include System.Collections namespace to use ArraList.
- Array Declaration & Initialization:
  ```c#
    int[] arr = new int[5]
    int[] arr = new int[5]{1, 2, 3, 4, 5};
    int[] arr = {1, 2, 3, 4, 5};
  ```
- ArrayList Declaration & Initialization:
  ```c#
      ArrayList arList = new ArrayList();
      arList.Add(1);
      arList.Add("Two");
      arList.Add(false);
  ```
  - Array stores a fixed number of elements. The size of an Array must be specified at the time of initialization.
  - ArrayList grows automatically and you don't need to specify the size.
  - Array is strongly typed. This means that an array can store only specific type of items\elements.
  - ArrayList can store any type of items\elements.
  - ArrayList performs slower than Array because of boxing and unboxing.

#### How is the using() pattern useful? What is IDisposable? How does it support deterministic finalization?

- The using() pattern is useful because it ensures that Dispose() will always be called when a disposable object (defined as one that implements IDisposable, and thus the Dispose() method) goes out of scope, even if it does so by an exception being thrown, and thus that resources are always released.
- IDisposable is an interface that contains a single method, Dispose(), for releasing unmanaged resources, like files, streams, database connections and so on.
- You can deterministically finalize any object that implements the IDisposable interface by invoking its Dispose() method. In C#, the using() statement allows you to define a scope at the end of which an object will be disposed.

#### How can you make sure that objects using dedicated resources (database connection, files, hardware, OS handle, etc.) are released as early as possible?

- For the majority of the objects that your app creates, you can rely on the .NET garbage collector to handle memory management. However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them.
- If your types use unmanaged resources, you should do the following:
  1. Implement the dispose pattern. This requires that you provide an IDisposable.Dispose implementation to enable the deterministic release of unmanaged resources. A consumer of your type calls Dispose when the object (and the resources it uses) are no longer needed. The Dispose method immediately releases the unmanaged resources.
  2. In the event that a consumer of your type forgets to call Dispose, provide a way for your unmanaged resources to be released. There are two ways to do this:
     - Use a safe handle to wrap your unmanaged resource. This is the recommended technique. Safe handles are derived from the System.Runtime.InteropServices.SafeHandle abstract class and include a robust Finalize method. When you use a safe handle, you simply implement the IDisposable interface and call your safe handle's Dispose method in your IDisposable.Dispose implementation. The safe handle's finalizer is called automatically by the garbage collector if its Dispose method is not called.

#### Why to use keyword “const” in C#? Give an example.

- You use the const keyword to declare a constant field or a constant local. Constant fields and locals aren't variables and may not be modified.
  ```c#
      const int X = 0;
      public const double GravitationalConstant = 6.673e-11;
      private const string ProductName = "Visual C#";
  ```

#### What is the difference between “const” and “readonly” variables in C#?

- a "readonly" field can't be assigned after the constructor exits.
- const fields have to be initialized whith declaration only, while readonly fields can be initialized at declaration or in the constructor.
- const variables can declared in methods ,while readonly fields cannot be declared in methods.
- const fields cannot be used with static modifier, while readonly fields can be used with static modifier.
- A const field is a compile-time constant, the readonly field can be used for run time constants.

#### What is a property in C#?

- A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.
- Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.
- Properties can be used as if they are public data members, but they are actually special methods called _accessors_.
- A get property accessor is used to return the property value, and a set property accessor is used to assign a new value.

#### List out two different types of errors in C#?

- Errors refer to the mistake or faults which occur during program development or execution. If you don't find them and correct them, they cause a program to produce wrong results.
- In programming language errors can be divided into three categories:

  1. Syntax Errors

     - Syntax errors occur during development, when you make type mistake in code. For example, instead of writing while, you write WHILE then it will be a syntax error since C# is a case sensitive language:

     ```c#
     bool flag=true;
     WHILE (flag) //syntax error, since c# is case sensitive
     {
     //TO DO:
     }
     ```

  2. Runtime Errors (Exceptions)

     - Runtime errors occur during execution of the program. These are also called exceptions. This can be caused due to improper user inputs, improper design logic or system errors:

     ```c#
     int a = 5, b = 0;
     int result = a / b; // DivideByZeroException
     ```

     - Exceptions can be handled by using try-catch blocks.

  3. Logical Errors

     - Logic errors occur when the program is written fine but it does not produce desired result. Logic errors are difficult to find because you need to know for sure that the result is wrong:

     ```c#
     int a = 5, b = 6;
     double avg = a + b / 2.0; // logical error, it should be (a + b) / 2.0
     ```

#### What is the difference between “out” and “ref” parameters in C#?

- They're pretty much the same - the only difference is that a variable you pass as an out parameter doesn't need to be initialized but passing it as a ref parameter it has to be set to something:

```c#
int x;
Foo(out x); // OK

int y;
Foo(ref y); // Error: y should be initialized before calling the method
```

“ref” parameters are for data that might be modified, “out” parameters are for data that's an additional output for the function (eg int.TryParse) that are already using the return value for something.

#### Can we override private virtual method in C#?

- The “virtual” keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.
- You cannot use the “virtual” modifier with the static, abstract, private, or override modifiers.
- By default, methods are non-virtual. You cannot override a non-virtual method.

#### What's the difference between IEquatable and just overriding Object.Equals()?

- The main difference is performance. IEquatable<T> lets a structure implement a strongly typed Equals() method so no boxing is required. Thus much better performance when using value types with generic collections.

* boxing = Boxing is the process of converting a value type to the type object or to any interface type implemented by this value type.
  - When the common language runtime (CLR) boxes a value type, it wraps the value inside a System.Object instance and stores it on the managed heap.
  - Unboxing extracts the value type from the object. Boxing is implicit; unboxing is explicit.
  - The concept of boxing and unboxing underlies the C# view in which a value of any type can be treated as an object.

#### Explain the differences between public, protected, private and internal. Explain access modifier – “protected internal” in C#!

- All types and type members have an accessibility level. The accessibility level controls whether they can be used from other code in your assembly or other assemblies.
  - _public_: The type or member can be accessed by any other code in the same assembly or another assembly that references it.
  - _private_: The type or member can be accessed only by code in the same class or struct.
  - _protected_: The type or member can be accessed only by code in the same class, or in a class that is derived from that class.
  - _internal_: The type or member can be accessed by any code in the same assembly, but not from another assembly.
  - _protected internal_: The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived class in another assembly.
  - _private protected_: The type or member can be accessed by types derived from the containing class, but only within its containing assembly. .

#### What’s the difference between using `override` and `new` keywords when defining method in child class?

- The “override” modifier extends the base class virtual method, and the “new” modifier hides an accessible base class method.
- If the method in the derived class is not preceded by “new” or “override” keywords, the compiler will issue a warning and the method will behave as if the “new” keyword were present.
- If the method in the derived class is preceded with the “new” keyword, the method is defined as being independent of the method in the base class.
  - The base class method can be called from within the derived class using the base keyword.
- If the method in the derived class is preceded with the “override” keyword, objects of the derived class will call that method instead of the base class method.
- In order to apply the “override” keyword to the method in the derived class, the base class method must be defined “virtual”.

#### Explain StringBuilder class in C#!

- The String object is immutable. Every time you use one of the methods in the System.String class, you create a new string object in memory, which requires a new allocation of space for that new object.
- Mutability means that once an instance of the class has been created, it can be modified by appending, removing, replacing, or inserting characters.
- The System.Text.StringBuilder class can be used when you want to modify a string without creating a new object. For example, using the StringBuilder class can boost performance when concatenating many strings together in a loop.

#### How we can sort the array elements in descending order in C#?

```c#
string[] ArrStr = new string[] { "Abundant Code", "Test Code", "Abundant Code1" };
Array.Sort(ArrStr);
Array.Reverse(ArrStr);
```

#### Can you use a value type as a generic type argument in C#? For example when implementing an interface like (IEquatable).

- In a generic type or method definition, a _type parameter_ is a placeholder for a specific type that a client specifies when they create an instance of the generic type.
- C# allows you to define generic classes, interfaces, abstract classes, fields, methods, static methods, properties, events, delegates, and operators using the type parameter and without the specific data type.
- In C#, data types are categorized based on how they store their value in the memory:
  1. Value type
     - A data type is a value type if it holds a data value within its own memory space. It means the variables of these data types directly contain values.
     - The following data types are all of value type: bool, byte, char, decimal, double, enum, float, int, long, sbyte,short, struct, uint, ulong, ushort.
  2. Reference Type
     - Unlike value types, a reference type doesn't store its value directly. Instead, it stores the address where the value is being stored. In other words, a reference type contains a pointer to another memory location that holds the data.
     - The followings are reference type data types: String, Arrays (even if their elements are value types), Class, Delegate
     - The default value of a reference type variable is null when they are not initialized. Null means not refering to any object.

#### What are Nullable Types in C#?

- A nullable type can represent the correct range of values for its underlying value type, plus an additional null value. For example, `Nullable<int>` can be assigned any value from -2147483648 to 2147483647, or a null value.
- The Nullable types are instances of `System.Nullable<T>` struct.
- A nullable of type int is the same as an ordinary int plus a flag that says whether the int has a value or not (is null or not).
  - _Flag_ variable is used as a signal in programming to let the program know that a certain condition has met. It usually acts as a boolean variable indicating a condition to be either true or false.
- A value type cannot be assigned a null value. For example, int i = null will give you a compile time error.
- You can use the '?' null-conditional operator to shorthand the syntax e.g. int?, long? instead of using `Nullable<T>`.
  ```c#
  int? i = null;
  double? D = null;
  ```

#### Conceptually, what is the difference between early-binding and late-binding?

- The key difference between early and late binding involves type conversion.
- While early binding provides compile-time checking of all types so that no implicit casts occur, late binding checks types only when the object is created or an action is performed on the type.

#### What is delegate, event, callback, multicast delegate?

- In computer programming, a _callback_ is executable code that is passed as an argument to other code.
- C# has delegates for that purpose. They are heavily used with events, as an event can automatically invoke a number of attached delegates (event handlers).

1. The delegate is a reference type data type that defines the method signature.

   ```c#
   public delegate void MyDelegate(string msg);
   // set target method
   MyDelegate del = new MyDelegate(MethodA);
   // or set lambda expression
   MyDelegate del = (string msg) =>  Console.WriteLine(msg);
   // target method
   static void MethodA(string message)
   {
      Console.WriteLine(message);
   }
   // Invoke a Delegate
   del("Hello World!");
   // Multicast Delegate
   MyDelegate del2 = ClassB.MethodB;
    del += del2;
    del -= del2;
   ```

   - The delegate can point to multiple methods. A delegate that points multiple methods is called a _multicast delegate_. The "+" or "+=" operator adds a function to the invocation list, and the "-" and "-=" operator removes it.

2. An event is a notification sent by an object to signal the occurrence of an action.

   - The class who raises events is called Publisher, and the class who receives the notification is called Subscriber.

   ```c#
   public delegate void Notify();  // delegate
   public class ProcessBusinessLogic
   {
     public event Notify ProcessCompleted; // event
   }
   ```

#### What is enum in C#?

- An enumeration type (or enum type) is a value type defined by a set of named constants of the underlying integral numeric type. To define an enumeration type, use the _enum_ keyword and specify the names of enum members.
- By default, the associated constant values of enum members are of type int; they start with zero and increase by one following the definition text order.
- You can explicitly specify any other integral numeric type as an underlying type of an enumeration type. You can also explicitly specify the associated constant values.

#### What is null-conditional operator?

- null-conditional operator _?._ and _?[]_ is an expression you can use to perform a member or element access operation only if an operand is non-null:
  ```c#
  a?.x
  a?.[x]
  ```
- If "a" evaluates to null, the result of a?.x or a?[x] is null.
- If a evaluates to non-null, the result of a?.x or a?[x] is the same as the result of a.x or a[x], respectively.
- If a.x or a[x] throws an exception, a?.x or a?[x] would throw the same exception for non-null a. For example, if a is a non-null array instance and x is outside the bounds of a, a?[x] would throw an IndexOutOfRangeException.
- null-conditional operators are short-circuiting: if one operation in a chain of conditional member or element access operations returns null, the rest of the chain doesn't execute.

#### What is null-coalescing operator?

- null-coalescing operator _??_ returns the value of its left-hand operand if it isn't null; otherwise, it evaluates the right-hand operand and returns its result.
- The _??_ operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.
  ```c#
  int a = null;
  int b = a ?? -1;
  ```
- The null-coalescing assignment operator ??= assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null. The ??= operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.
  ```c#
  int a = null;
  numbers.Add(a ??= 0);
  ```

#### What is serialization?

- in C#, Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file.
- Its main purpose is to save the state of an object in order to be able to recreate it when needed. The reverse process is called deserialization.

#### What is the difference between Finalize() and Dispose() methods?

- Finalize () is called by Garbage Collector implicitly to free unmanaged resources. The garbage collector calls this method at some point after there are no longer valid references to the object.
- There are some resources like _windows handles_, _database connections_ which cannot be collected by the garbage collector. Therefore the programmer needs to call Dispose() method of IDisposable interface.
- Dispose () of IDisposable interface is called by the programmer to explicitly release resources when they are no longer being used. Dispose () can be called even if other references to the object are alive.

#### How do you inherit a class from another class in C#?

- Inheritance enables you to create new classes that reuse, extend, and modify the behavior defined in other classes.
- The class whose members are inherited is called the base class, and the class that inherits those members is called the derived class. A derived class can have only one direct base class.
  ```c#
  public class Animal
  {
    public void Greet()
    {
        Console.WriteLine("Hello, I'm some sort of animal!");
    }
  }
  public class Dog : Animal
  {
    public Dog() : base()
    {
    }
  }
  Animal animal = new Animal();
  animal.Greet();
  Dog dog = new Dog();
  dog.Greet();
  ```

#### What is difference between “is” and “as” operators in C#?

- The “is” operator checks if an object can be cast to a specific type:

  ```c#
  if (someObject is StringBuilder) ...
  ```

- The “as” operator attempts to cast an object to a specific type, and returns null if it fails.
  ```c#
  StringBuilder b = someObject as StringBuilder;
  if (b != null) ...
  ```
- The “is” operator is used to check if the run-time type of an object is compatible with the given type or not whereas “as” operator is used to perform conversion between compatible reference types or Nullable types.
- The “is” operator is of boolean type whereas “as” operator is not of boolean type.
- The “is” operator returns true if the given object is of the same type whereas “as” operator returns the object when they are compatible with the given type.
- The “is” operator returns false if the given object is not of the same type whereas “as” operator return null if the conversion is not possible.
- The “is” operator is used for only reference, boxing, and unboxing conversions whereas “as” operator is used only for nullable, reference and boxing conversions

#### What are indexers in C# .NET?

- An indexer is a special type of property that allows a class or a structure to be accessed like an array for its internal collection. C# allows us to define custom indexers, generic indexers, and also overload indexers.

  ```c#
  class StringDataStore
  {
    private string[] strArr = new string[10]; // internal data storage

    public string this[int index]
    {
        get => strArr[index];
        set => strArr[index] = value;
    }
  }
  StringDataStore strStore = new StringDataStore();
  strStore[0] = "One";
  strStore[1] = "Two";
  strStore[2] = "Three";
  strStore[3] = "Four";
  ```

#### What is the difference between returning IQueryable<T> vs. IEnumerable<T>?

- The difference is that IQueryable<T> is the interface that allows LINQ-to-SQL (LINQ.-to-anything really) to work. So if you further refine your query on an IQueryable<T>, that query will be executed in the database, if possible.
- For the IEnumerable<T> case, it will be LINQ-to-object, meaning that all objects matching the original query will have to be loaded into memory from the database.
  ```c#
  IQueryable<Customer> custs = ...;
  var goldCustomers = custs.Where(c => c.IsGold);
  ```
  - That code will execute SQL to only select gold customers. The following code, on the other hand, will execute the original query in the database, then filtering out the non-gold customers in the memory:
  ```c#
  IEnumerable<Customer> custs = ...;
  var goldCustomers = custs.Where(c => c.IsGold);
  ```
- This is quite an important difference, and working on IQueryable<T> can in many cases save you from returning too many rows from the database.
- Another prime example is doing paging: If you use Take and Skip on IQueryable, you will only get the number of rows requested; doing that on an IEnumerable<T> will cause all of your rows to be loaded in memory.

#### What is LINQ? Explain the idea of extension methods.

- LINQ (Language Integrated Query) is uniform query syntax in C# and VB.NET to retrieve data from different sources and formats, thereby eliminating the mismatch between programming languages and databases, as well as providing a single querying interface for different types of data sources.
- Extension methods, as the name suggests, are additional methods. Extension methods allow you to inject additional methods without modifying, deriving or recompiling the original class, struct or interface. Extension methods can be added to your own custom class, .NET framework classes, or third party classes or interfaces.
- The only difference between a regular static method and an extension method is that the first parameter of the extension method specifies the type that it is going to operator on, preceded by the this keyword.

  ```c#
  namespace ExtensionMethods
  {
    public static class IntExtensions
    {
      public static bool IsGreaterThan(this int i, int value)
      {
        return i > value;
      }
    }
  }
  ```

  ```c#
  using ExtensionMethods;
  class Program
  {
    static void Main(string[] args)
    {
      int i = 10;
      bool result = i.IsGreaterThan(100);
      Console.WriteLine(result);
    }
  }
  ```

#### What are the advantages and disadvantages of lazy loading?

- Lazy loading (also called on-demand loading) is an optimization technique for the online content, be it a website or a web app.
- Instead of loading the entire web page and rendering it to the user in one go as in bulk loading, the concept of lazy loading assists in loading only the required section and delays the remaining, until it is needed by the user.

1. Advantages of Lazy loading:

- reduces time consumption and memory usage thereby optimizing content delivery.
- Unnecessary code execution is avoided.
- Optimal usage of time and space resources makes it a cost-effective approach from the point of view of business persons. (website owners)

2. Disadvantages of Lazy loading:

- the extra lines of code, to be added to the existing ones, to implement lazy load makes the code a bit complicated.
- lazy loading may affect the website’s ranking on search engines sometimes, due to improper indexing of the unloaded content.

#### How to use of “yield” keyword? Mention at least one practical scenario where it can be used?

- When you use the “yield” contextual keyword in a statement, you indicate that the method, operator, or "get" accessor in which it appears is an iterator.
- You use a “yield” return statement to return each element one at a time.
- You can use a “yield” break statement to end the iteration.
- Using yield to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration) when you implement the IEnumerable and IEnumerator pattern for a custom collection type.

  ```c#
  using System;
  using System.Collections.Generic;

  public class YieldSample
  {
    static void Main()
    {
      foreach (var number in GenerateWithoutYield())
        Console.WriteLine(number);
    }
    public static IEnumerable<int> GenerateWithoutYield()
    {
      var i = 0;
      var list = new List<int>();

      while (i < 5)  // yield gives the control to this part and will hit only this part everytime we call GenerateWithoutYield
        yield return ++i;
    }
  }
  ```

#### What are attributes in C#? Give some examples of usage of them.

- Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth). After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called reflection.

```c#
[Serializable]
public class SampleClass
{
    // Objects of this type can be serialized.
}
[Conditional("DEBUG"), Conditional("TEST1")]
void TraceMethod()
{
    // ...
}
```

#### By what mechanism does NUnit know what methods to test?

- By using the _Act_ section (calling the method we are targeting that particular test) of the AAA (Arrange, Act, Assert) testing pattern.

#### What is the GAC? What problem does it solve?

- Each computer where the Common Language Runtime(CLR) is installed has a machine-wide code cache called the Global Assembly Cache (GAC). The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.
- GAC solves the problem of DLL versioning. GAC can hold two assemblies of the same name but different version. This ensures that applications which access a particulat assembly, continue to access the same assembly, even if another version of that assembly is installed on that machine.

#### What is the largest number you can work with in C#?

- It depends on the numeric type. The limits for integer types are listed in Microsoft's table for max.
- For example,
  - the largest _sbyte (8-bit signed integer)_ is: 127;
  - the largest _int (32-bit signed integer type)_ is: 2,147,483,647;
  - the largest _ulong (64-bit unsigned integer type)_ is: 18,446,744,073,709,551,615;
  - the largest _double (64-bit double-precision floating point type)_ is: 1.79769313486232e308;
  - the largest _decimal (128-bit decimal type for financial and monetary calculations)_ is: 7.9 x 10e28.

---

### Database

#### How can you connect your application to a database server? What are the possible ways?

1. Install or locate the database you want to access.
2. Include the JDBC library.
3. Ensure the JDBC driver you need is on your classpath.
4. Use the JDBC library to obtain a connection to the database.
5. Use the connection to issue SQL commands.

#### What do you know about database normalization?

- Database normalization is the process of organizing the attributes of the database to reduce or eliminate data
  redundancy (having the same data but at different places) .

---

---

<br/><br/>
<br/><br/>
<br/><br/>

# Advanced

# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?

- N-tier architecture would involve dividing an application into three different tiers. These would be the:
  1. Presentation Tier
     - The top-most level of application is the user interface (UI). The main function of the interface is to translate tasks and results to something the user can understand.
  2. Logic Tier
     - This layer coordinates the application, processes commands, makes logical decisions and evaluations and performs calculations. It also moves and processes data between the two surrounding layers.
  3. Data Tier
     - Here information is stored and retrieved from database or file system. The information is then passed back to the logic tier for processing, and then eventually back to the user.

#### What are microservices? Advantages and disadvantages?

- A microservices architecture consists of a collection of small, autonomous services. Each service is self-contained and should implement a single business capability.
- Microservices are small, independent, and loosely coupled. Each service is a separate codebase, can be deployed independently; a team can update an existing service without rebuilding and redeploying the entire application.
- Services are responsible for persisting their own data or external state. This differs from the traditional model, where a separate data layer handles data persistence.
- Services communicate with each other by using well-defined APIs. Internal implementation details of each service are hidden from other services.
- Services don't need to share the same technology stack, libraries, or frameworks.
  ![Microservices Architecture Example](microservices-logical.png)
- Advantages
  - _Agility_: it's easier to manage bug fixes and feature releases.
  - _Small, focused teams_: promote greater agility.
  - _Small code base_: minimizes dependencies, and that makes it easier to add new features.
  - _Mix of technologies_: Teams can pick the technology that best fits their service.
  - _Fault isolation_: If an individual microservice becomes unavailable, it won't disrupt the entire application.
  - _Scalability_: Services can be scaled independently, letting you scale out subsystems that require more resources, without scaling out the entire application.
    - Scalability is the ability of a system to handle increased load.
  - _Data isolation_: easier to perform schema updates, because only a single microservice is affected.
- Disadvantages
  - _Complexity_: has more moving parts than the equivalent monolithic application.
  - _Development and testing_: existing tools are not always designed to work with service dependencies; challenging to test service dependencies, especially when the application is evolving quickly.
  - _Lack of governance_: so many different languages and frameworks that the application becomes hard to maintain; especially applies to cross-cutting functionality such as logging.
  - _Network congestion and latency_: many small, granular services can result in more interservice communication.
  - _Data integrity_: data consistency can be a challenge.
  - _Management_: Correlated logging across services can be challenging.
  - _Versioning_: Updates to a service must not break services that depend on it.
  - _Skillset_: teams have to have the skills and experience to be successful.

#### What is Separation of Concerns?

- It is architectral design principle which asserts that software should be separated based on the kinds of work it performs.
- Applications can be logically built to follow this principle by separating core business behavior from infrastructure and user-interface logic.
- Business rules and logic should reside in a separate project, which should not depend on other projects in the application. Separation helps ensure that the business model is easy to test and can evolve without being tightly coupled to low-level implementation details.

#### What is a layered design and why is it important in enterprise applications?

- As applications grow in complexity, one way to manage that complexity is to break up the application according to its responsibilities or concerns. This approach follows the separation of concerns principle.
- By organizing code into layers, common low-level functionality can be reused throughout the application, following the don't repeat yourself (DRY) principle.
- Layers can also make it easier to swap out implementations for testing purpose; these layers can be replaced at test time with fake implementations that provide known responses to requests, which makes tests much easier to write and much faster to run.

#### What is Dependency Injection?

- When class A uses some functionality of class B, then its said that class A has a _dependency_ of class B.
- Dependencies can be injected at runtime rather than at compile time.
- _Dependency Injection_ is a software design pattern for transferring the task of creating the object to someone else and directly using the dependency.
- There are basically three types of dependency injection:
  1. constructor injection: the dependencies are provided through a class constructor.
  2. setter injection: the client exposes a setter method that the injector uses to inject the dependency.
  3. interface injection: the dependency provides an injector method that will inject the dependency into any client passed to it. Clients must implement an interface that exposes a setter method that accepts the dependency.
- _Inversion of control (IoC)_ — the concept behind DI - states that a class should not configure its dependencies statically but should be configured by some other class from outside.
  - It is the fifth principle of S.O.L.I.D — the five basic principles of object-oriented programming and design by Uncle Bob — which states that a class should depend on abstraction and not upon concretions (in simple terms, hard-coded).
  - According to the principles, a class should concentrate on fulfilling its responsibilities and not on creating objects that it requires to fulfill those responsibilities. And that’s where dependency injection comes into play: it provides the class with the required objects.
- Benefits of using DI
  - Helps in Unit testing.
  - Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
  - Extending the application becomes easier.
  - Helps to enable loose coupling, which is important in application programming.

#### What is the DAO pattern? When and how to implement?

- The Data Access Object (DAO) pattern is a structural pattern that allows us to isolate the application/business layer from the persistence layer (usually a relational database, but it could be any other persistence mechanism) using an abstract API.
- The functionality of this API is to hide from the application all the complexities involved in performing CRUD operations in the underlying storage mechanism. This permits both layers to evolve separately without knowing anything about each other.

#### What is SOA? When to use?

- Service-Oriented Architecture (SOA) means that you structure the architecture of your application by decomposing it into several services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.
- SOA provides the infrastructure for the idea of how two independent business entities communicate and work together. For example, a bank that offers Stock services, a travel site with the feature to book a flight, a hotel, a car or even a holiday package and so on., weather updates and currency rates, and so on. All such activities take place due to B2B integration and SOA is the oxygen for such type of business activities.
- SOA is intended to provide loosely-coupled interaction among applications. Benefits offered by SOA are as follows:
  - Agility. Enables your business to adapt to changes quickly.
  - Productivity. Can implement complex applications using SOA more easily than with other architectural styles.
  - Reusability. Able to reuse your services across systems instead of rewriting the same modules again and again in every system or specific to an individual system.
  - Reduced cost. Software Architects think of Build vs. Buy vs. Reuse, SOA based approach allows either buying or reusing this feature/functionality, hence in most cases the cost is saved by reusing the existing services There are many commonly used services available for free.

### Testing

#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?

- _Unit testing_ is a level of software testing where individual units/components of a software are tested. The purpose is to validate that each unit of the software performs as designed. A unit is the smallest testable part of any software. In most programming languages, that is a function, a subroutine, a method or property.
- _Integration testing_ is a level of software testing where individual units are combined and tested as a group. The purpose of this level of testing is to expose faults in the interaction between integrated units. Test drivers and test stubs(programs that simulate the behaviours of software components) are used to assist in Integration Testing.
- _Regression testing_ is a type of software testing that intends to ensure that changes (enhancements or defect fixes) to the software have not adversely affected it. The likelihood of any code changes impacting functionalities that are not directly associated with the code is always there and it is essential that regression testing is conducted to make sure that fixing one thing has not broken another thing.
- _Acceptance testing_ is a level of software testing where a system is tested for acceptability. The purpose of this test is to evaluate the system’s compliance with the business requirements and assess whether it is acceptable for delivery.
- _System testing_ is a level of software testing where a complete and integrated software is tested. The purpose of this test is to evaluate the system’s compliance with the specified requirements.

#### What is code coverage? Why is it used? How you can measure?

- Code coverage is the percentage of code which is covered by automated tests. Code coverage measurement simply determines which statements in a body of code have been executed through a test run, and which statements have not. In general, a code coverage system collects information about the running program and then combines that with source information to generate a report on the test suite's code coverage.
- To calculate the code coverage percentage, simply use the following formula:
  - Code Coverage Percentage = (Number of lines of code executed by a testing algorithm/Total number of lines of code in a system component) \* 100.

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?

- Mocking is a process used in unit testing when the unit being tested has external dependencies.
- The purpose of mocking is to isolate and focus on the code being tested and not on the behavior or state of external dependencies.
- In mocking, the dependencies are replaced by closely controlled replacements objects that simulate the behavior of the real ones. There are three main possible types of replacement objects - fakes, stubs, and mocks.
- _Dummy_: objects that are passed around but never actually used. Usually they are just used to fill parameter lists.
- _Fake_: objects with limited capabilities (for the purposes of testing), e.g. a fake web service.
- _Stubs_: objects that provide predefined answers to method calls.
- _Spies_ are stubs that also record some information based on how they were called. One form of this might be an email service that records how many messages it was sent.
- _Mocks_: objects on which you set expectations.

  ```c#
  public class UserDetail
  {
    public string Name { get; set; }
    public string Role { get; set; }
  }

  public interface IUserStore
  {
    string GetUserRole(string username);
  }

  public class StubUserStore : IUserStore
  {
    public string GetUserRole(string username)
    {
      return "contributor";
    }
    public List<UserDetail> GetAllUsers()
    {
      return new List<UserDetail>()
      {
        new UserDetail{ Role = "administrator", Name = "admin"},
        new UserDetail(){ Role = "contributor", Name = "User 1"}
      };
    }
  }

  public class FakeUserStore : IUserStore
  {
    public string GetUserRole(string username)
    {
      if (username == "admin")
        return "administrator";
      else
        return "contributor";
    }
  }

  public class SpyUserStore : IUserStore
  {
    private static int Counter { get; set; }
    public SpyUserStore()
    {
      Counter = 0;
    }
    public string GetUserRole(string username)
    {
      if (Counter >= 1)
        throw new Exception("Function called more than once");
      Counter++;
      if (username == "admin")
        return "administrator";
      else
        return "contributor";
    }
  }

  Mock<IUserStore> mockedUserStore = new Mock<IUserStore>();
  mockedUserStore.Setup(func => func.GetUserRole("admin")).Returns("administrator");
  mockedUserStore.Setup(func => func.GetUserRole("user1")).Returns("contributor");
  mockedUserStore.Setup(func => func.GetUserRole("user2")).Returns("basic");
  ```

#### What is a test case? What is an assertion? Give examples!

- A _test case_ is a set of actions executed to verify a feature or functionality of your software application. A test case contains test steps, test data, precondition, postcondition developed for specific test scenario to verify any requirement. Examples:
  1. Enter valid User Name and valid Password
  2. Enter valid User Name and invalid Password
  3. Enter invalid User Name and valid Password
  4. Enter invalid User Name and invalid Password
- An _assertion_ is a bool expression at a specific point in a program which will be true unless there is a bug in the program. A test assertion is defined as an expression, which encapsulates some testable logic specified about a target under test.
  ```c#
  int IntegerDivide (int dividend , int divisor)
  {
    Debug.Assert(divisor != 0);
    return (dividend / divisor);
  }
  ```

#### What is TDD? What are the benefits?

- Test Driven Development (TDD) is a software development practice enabling developers to create proper specifications about how their code should be written and implemented. Fundamentally, TDD is a practice when a programmer writes a functional test before building a code.
- This process includes the following stages:
  1. Writing a test that fails because of code absence (red).
  2. Writing a code after which the test is passed (green).
  3. Refactoring - checking the code structure and its improvement without changing its external behavior. The expected result of refactoring is obtaining a perfectly written code.
- Benefits:
  - Better program design and higher code quality
  - Detailed project documentation
  - Reduces the time required for project development
  - Code flexibility and easier maintenance
  - Reliability of the developed solution
  - Save project costs in the long run

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)

- Good test name
- Arrange your test in Arrange, Act and Assert
- Write minimal passing tests
- Avoid magic strings
- Avoid logic in tests
- Avoid multiple asserts (only one assert per test)
- Test public interfaces
- Verify one use case per test

#### What is arrange/act/assert pattern?

- The AAA (Arrange, Act, Assert) pattern is a common way of writing unit tests for a method under test.
- The _Arrange_ section of a unit test method initializes objects and sets the value of the data that is passed to the method under test.
- The _Act_ section invokes the method under test with the arranged parameters.
- The _Assert_ section verifies that the action of the method under test behaves as expected.

  ```c#
  [TestMethod]
  public void Withdraw_ValidAmount_ChangesBalance()
  {
    // arrange
    double currentBalance = 10.0;
    double withdrawal = 1.0;
    double expected = 9.0;
    var account = new CheckingAccount("JohnDoe", currentBalance);

    // act
    account.Withdraw(withdrawal);

    // assert
    Assert.AreEqual(expected, account.Balance);
  }
  ```

### DevOps

#### What is continuous integration? Why is CI important?

- Continuous integration (CI) is the practice of automating the integration of code changes from multiple contributors into a single software project. It allows developers to frequently merge code changes into a central repository where builds and tests then run. Automated tools are used to assert the new code’s correctness before integration.
- A source code version control system is the crux of the CI process. The version control system is also supplemented with other checks like automated code quality tests, syntax style review tools, and more.
- Benefits:
  - Enable scaling: enables organizations to scale in engineering team size, codebase size, and infrastructure, by minimizing code integration bureaucracy and communication overhead, CI helps build DevOps and agile workflows.
    - _Scalability_ is the ability of a system to handle growing amount of load without degrading performance.
  - Improve the feedback loop: Faster feedback on business decisions. Changes can be rapidly pushed and measured for success. Bugs or other issues can be quickly addressed and repaired.
  - Enhance communication: improves overall engineering communication and accountability, which enables greater collaboration between development and operations in a DevOps team. By introducing pull request workflows tied to CI, allows developers to observe and comment on code from other team members.

#### Why are tests important in the CI workflow?

- If you test and deploy code more frequently, it will eventually reduce the risk level of the project you are working on as you can detect bugs and code defects earlier. This means they are easier to fix and you can fix them sooner which makes it cheaper to fix them.

#### Name some software that help the CI workflow!

- Software development tool providers have started offering full CI-as-a-service offerings:
  - Bitbucket Pipelines (offered by Atlassian)
  - Jenkins
  - AWS CodePipeline (Amazon Web Services)
  - CircleCI
  - Azure Pipelines
  - GitLab
  - Atlassian Bamboo

#### What is Continuous Delivery?

- Continuous Delivery is the ability to get changes of all types — including new features, configuration changes, bug fixes and experiments — into production, or into the hands of users, safely and quickly in a sustainable way.
- Continuous delivery is an extension of continuous integration since it automatically deploys all code changes to a testing and/or production environment after the build stage.

#### What is Continuous Deployment?

- Continuous Deployment (CD) is a software release process that uses automated testing to validate if changes to a codebase are correct and stable for immediate autonomous deployment to a production environment.
- Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers.

#### What is DevOps?

- DevOps is a set of practices that works to automate and integrate the processes between software development and IT teams, so they can build, test, and release software faster and more reliably. It unites agile, git, continuous delivery, automation, and much more, to help development and operations teams be more efficient, innovate faster, and deliver higher value to businesses and customers.

### Software Methodologies

#### What kind of software-lifecycle models do you know?

- Agile development
  - Advantages
    - Decrease the time required to avail some system features.
    - Face to face communication and continuous inputs from customer representative leaves no space for guesswork.
    - The end result is the high-quality software in the least possible time duration and satisfied customer.
  - Disadvantages
    - The ability and collaboration of the customer to be interactive to express user needs.
    - Needs special skills for the team.
- Waterfall Model
  - Advantages
    - Easy to explain to the users.
    - Stages and activities are well defined.
    - Verification at each stage ensures early detection of errors/misunderstanding.
  - Disadvantages
    - Assumes that the requirements of a system can be frozen.
    - Very difficult to go back to any stage after it finished.
    - A little flexibility and adjusting scope is difficult and expensive.
    - Costly and required more time, in addition to the detailed plan.
- Other examples: V-Shaped Model, Spiral Model, Iterative and Incremental Method, Evolutionary Prototyping Model and more.

#### What is a UML diagram? What kind of diagram types do you know?

- UML stands for Unified Modeling Language. It’s a rich language to model software solutions, application structures, system behavior and business processes.
- There are two main UML diagram types; structure diagrams and behavioral diagrams
  - Structure Diagrams Examples: Class Diagram, Component Diagram, Deployment Diagram, Object Diagram, Package Diagram, Profile Diagram, Composite Structure Diagram.
  - Behavioral Diagrams Examples: Use Case Diagram, Activity Diagram, State Machine Diagram, Sequence Diagram, Communication Diagram, Interaction Overview Diagram, Timing Diagram.

#### What is a UML class diagram? What are the typical elements?

- The UML Class diagram is a graphical notation used to construct and visualize object oriented systems. A class diagram in the Unified Modeling Language (UML) is a type of static structure diagram that describes the structure of a system by showing the system's:
  - classes,
  * their attributes,
  * operations (or methods),
  * and the relationships among objects.

#### What kind of design patterns do you know? Bring at least 3 examples.

- In software engineering, a design pattern is a general repeatable solution to a commonly occurring problem in software design. A design pattern isn't a finished design that can be transformed directly into code. It is a description or template for how to solve a problem that can be used in many different situations.
  - Creational design patterns examples:
    - Abstract Factory: Creates an instance of several families of classes
    - Builder: Separates object construction from its representation
    - Factory Method: Creates an instance of several derived classes
    - Singleton: A class of which only a single instance can exist
  - Structural design patterns examples:
    - Adapter: Match interfaces of different classes
    - Bridge: Separates an object’s interface from its implementation
    - Composite: A tree structure of simple and composite objects
    - Decorator: Add responsibilities to objects dynamically
  - Behavioral design patterns examples:
    - Chain of responsibility: A way of passing a request between a chain of objects
    - Command: Encapsulate a command request as an object
    - Interpreter: A way to include language elements in a program
    - Iterator: Sequentially access the elements of a collection

#### What is the purpose of the Iterator Pattern?

- The Iterator Pattern is a behavioral design pattern that provides a way to access the elements of an aggregate object (like a list) sequentially without exposing its underlying representation.
- The key idea is to take the responsibility for access and traversal out of the aggregate object and put it into an Iterator object that defines a standard traversal protocol.
- The Iterator abstraction is fundamental to an emerging technology called "generic programming". This strategy seeks to explicitly separate the notion of "algorithm" from that of "data structure". The motivation is to: promote component-based development, boost productivity, and reduce configuration management.

#### What do you know about the SOLID principles?

- SOLID is an acronym for the first five object-oriented design (OOD) principles by Robert C. Martin (also known as Uncle Bob).

1. S - Single-responsiblity Principle
   - A class should have one and only one reason to change, meaning that a class should have only one job.
2. O - Open-closed Principle
   - Objects or entities should be open for extension but closed for modification. This means that a class should be extendable without modifying the class itself.
3. L - Liskov Substitution Principle
   - Every subclass or derived class should be substitutable for their base or parent class.
4. I - Interface Segregation Principle
   - A client should never be forced to implement an interface that it doesn’t use, or clients shouldn’t be forced to depend on methods they do not use.
5. D - Dependency Inversion Principle
   - Entities must depend on abstractions, not on concretions. It states that the high-level module must not depend on the low-level module, but they should depend on abstractions.

#### How would you separate data storage code and business logic code (which uses stored data) in an application?

- Using the The Model-View-Controller (MVC) design pattern.
- It separates an application into three main groups of components: Models(data storage code ), Views(presentation code), and Controllers (business logic code ).

---

## Computer science

### Data Structures

#### What is the difference between Stack and Queue data structure?

- A _stack_ is a linear data structure in which elements can be inserted and deleted only from one side of the list, called the top. A _stack_ follows the LIFO (Last In First Out) principle, i.e., the element inserted at the last is the first element to come out.
- A _queue_ is a linear data structure in which elements can be inserted only from one side of the list called rear, and the elements can be deleted only from the other side called the front. The _queue_ data structure follows the FIFO (First In First Out) principle, i.e. the element inserted at first in the list, is the first element to be removed from the list

#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?

- A Graph is a non-linear data structure consisting of nodes and edges. There are two main parts of a graph:
  - The vertices (nodes) where the data is stored
  - The edges (connections, lines) which connect the nodes.
- A _simple graph_ is a graph with no loops(a graph which joins a vertex to itself, also called a self-loop) and no multiple edges(two or more edges connecting the same two vertices ).
- A _directed graph (or digraph)_ is a graph where the edges point in a direction. It is a set of vertices and a collection of directed edges that each connects an ordered pair of vertices. We say that a directed edge points from the first vertex in the pair and points to the second vertex in the pair.
- An _undirected graph_ is a set of objects (called vertices or nodes) that are connected together, where all the edges are bidirectional. An _undirected graph_ is sometimes called an _undirected network_.
- A _weighted graph_ is a graph in which each branch is given a numerical weight. A weighted graph is therefore a special type of labeled graph in which the labels are numbers (which are usually taken to be positive).

#### What are trees? What are binary trees? What are binary search trees?

- A _tree_ is an undirected graph in which any two vertices are connected by exactly one path, and does not contain even a single cycle.
- A _binary tree_ is a tree-type non-linear data structure in which each node has at most two children, which are referred to as the left child and the right child.
- A _binary tree_ has the benefits of both an ordered array and a linked list as search is as quick as in a sorted array and insertion or deletion operation are as fast as in linked list.
- A _binary search tree_ is a binary tree data structure which has the following properties:
  - The left subtree of a node contains only nodes with keys lesser than the node’s key.
  * The right subtree of a node contains only nodes with keys greater than the node’s key.
  * The left and right subtree each must also be a binary search tree.

#### How can you store graphs in programs? What are the advantages/disadvantages per each?

- You can store a graph using:
  - Nodes as objects with pointers to one another
  - A matrix of edge weights
- Nodes as objects with pointers to one another
  - The memory complexity for this approach is O(n) because you have as many objects as you have nodes. The number of pointers (to nodes) required is up to O(n^2) as each node object may contain pointers for up to n nodes.
  - The time complexity for this data structure is O(n) for accessing any given node.
- Storing a matrix of edge weights

  - This would be a memory complexity of O(n^2) for the matrix.
  - The advantage with this data structure is that the time complexity to access any given node is O(1).

  ```c#
  // Binary Tree
  using System;

  /* Class containing left and right child
  of current node and key value*/
  public class Node
  {
    public int key;
    public Node left, right;

    public Node(int item)
    {
      key = item;
      left = right = null;
    }
  }

  public class BinaryTree
  {
    // Root of Binary Tree
    Node root;

    // Constructors
    BinaryTree(int key)
    {
      root = new Node(key);
    }

    BinaryTree()
    {
      root = null;
    }

    // Driver Code
    public static void Main(String[] args)
    {
      BinaryTree tree = new BinaryTree();

      /*create root*/
      tree.root = new Node(1);

      /* following is the tree after above statement
        1
        / \
      null null	 */
      tree.root.left = new Node(2);
      tree.root.right = new Node(3);

      /* 2 and 3 become left and right children of 1
        1
        / \
        2	 3
      / \ / \
      null null null null */
      tree.root.left.left = new Node(4);

      /* 4 becomes left child of 2
            1
          /	 \
        2		 3
        / \	 / \
        4 null null null
      / \
      null null
      */
    }
  }
  ```

#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?

- Graph traversal algorithms are used to visit nodes in graph.
- The Breadth First Search (BFS) traversal is an algorithm, which is used to visit all of the nodes of a given graph. In this traversal algorithm one node is selected and then all of the adjacent nodes are visited one by one. After completing all of the adjacent vertices, it moves further to check another vertices and checks its adjacent vertices again.
- The Depth First Search (DFS) is a graph traversal algorithm. In this algorithm one starting vertex is given, and when an adjacent vertex is found, it moves to that adjacent vertex first and try to traverse in the same manner.

#### How does dictionary work?

- Dictionary is a collection that stores key-value pairs in no particular order.
- In C# language:
  - Keys must be unique and cannot be null.
  - Values can be null or duplicate.
  - Values can be accessed by passing associated key in the indexer e.g. myDictionary[key].

#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

- If immutable, the object's hash code won’t change and it allows caching the hash code of different keys which makes the overall retrieval process very fast.

### Algorithms

#### What is QuickSort? Describe the main logic of this sorting algorithm.

- Quicksort is a divide-and-conquer algorithm.
- It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively.

  1. Consider the first element of the list as pivot (i.e., Element at first position in the list).
  2. Define two variables i and j. Set i and j to first and last elements of the list respectively.
  3. Increment i until list[i] > pivot then stop.
  4. Decrement j until list[j] < pivot then stop.
  5. If i < j then exchange list[i] and list[j].
  6. Repeat steps 3,4 & 5 until i > j.
  7. Exchange the pivot element with list[j] element.

  ```c#
  /* arr[] --> Array to be sorted,
    low --> Starting index,
    high --> Ending index */
  static int partition(int []arr, int low, int high)
  {
    int pivot = arr[high];
    int i = (low - 1);  // index of smaller element
    for (int j = low; j < high; j++)
    {
      if (arr[j] < pivot)  // If current element is smaller than the pivot
      {
        i++;
        int temp = arr[i];   // swap arr[i] and arr[j]
        arr[i] = arr[j];
        arr[j] = temp;
      }
    }
    int temp1 = arr[i + 1]; // swap arr[i + 1] and arr[high] (or pivot)
    arr[i + 1] = arr[high];
    arr[high] = temp1;
    return i + 1;
  }

  static void quickSort(int []arr, int low, int high)
  {
    if (low < high)
    {
      int pi = partition(arr, low, high);
      quickSort(arr, low, pi - 1);
      quickSort(arr, pi + 1, high);
    }
  }
  ```

---

## Software design

### Security

#### What is OAuth2?

- OAuth 2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Facebook, GitHub, and DigitalOcean.
- It works by delegating user authentication to the service that hosts the user account, and authorizing third-party applications to access the user account. OAuth 2 provides authorization flows for web and desktop applications, and mobile devices.

#### What is Basic Authentication?

- Basic authentication is a simple authentication scheme built into the HTTP protocol. The client sends HTTP requests with the Authorization header that contains the word Basic followed by a space and a base64-encoded string username:password. For example, to authorize as demo / p@55w0rd the client would send:
  ```
  Authorization: Basic ZGVtbzpwQDU1dzByZA==
  ```
- Basic authentication, or “basic auth” is formally defined in the Hypertext Transfer Protocol standard, RFC 1945. When a client (your browser) connects to a web server, it sends a “WWW-Authenticate: Basic” message in the HTTP header.
  - Shortly after that, it sends your login credentials to the server using a mild obfuscation technique called base64 encoding. When HTTPS is used, these credentials are protected, so it’s not considered insecure, which is why basic auth gained widespread use over the years.
    -The biggest problem with basic auth has to do with the logging off the server, as most browsers tend to cache sessions and have inconsistently dealt with the need to properly close and clear connection states (or sessions) so that another (different) user couldn’t log back in by refreshing the browser.

#### What is CORS, why it’s needed in browsers?

- Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any other origins (domain, scheme, or port) than its own from which a browser should permit loading of resources.
- Is a W3C standard that allows a server to relax the same-origin policy.
- An API is not safer by allowing CORS. For example, a malicious actor could use Cross-Site Scripting (XSS) against your site and execute a cross-site request to their CORS enabled site to steal information.
- Allows a server to explicitly allow some cross-origin requests while rejecting others.
- Is safer and more flexible than earlier techniques, such as JSONP (JSON with Padding).

#### How can you initialize a CSRF attack?

- Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application in which they’re currently authenticated.
- With social engineering (such as sending a link via email or chat), an attacker may trick the users of a web application into executing actions of the attacker’s choosing.
- A successful CSRF attack can force the user to perform state changing requests like transferring funds, changing their email address, and so forth. If the victim is an administrative account, CSRF can compromise the entire web application.
- For example, in a typical GET request for a bank transfer, a hacker can modify this script so it results in a transfer to their own account.
  - The hacker can embed the request into an innocent looking hyperlink, and distribute the hyperlink via email to a large number of bank customers.
    - Those who click on the link while logged into their bank account will unintentionally initiate the transfer.
      - If the bank’s website is only using POST requests, the attack could be delivered in a <form> tag with automatic execution of the embedded JavaScript.

#### What is JWT used for? Where to store it on client side?

- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
- JWT is a token that is issued by the server. The token has a JSON payload that contains information specific to the user. This token can be used by clients when talking to APIs (by sending it along as an HTTP header) so that the APIs can identify the user represented by the token, and take user specific action.
- JWT also contains a signature. This signature is created by the server that issued the token (let’s say your login endpoint) and any other server that receives this token can independently verify the signature.
- JWTs have an expiry value. Common practice is to keep it around 15 minutes, so that any leaked JWTs will cease to be valid fairly quickly.
- The token is stored in an HttpOnly cookie. The other methods are all prone to XSS attacks and as such they should be avoided. An HttpOnly cookie is not accessible from JavaScript, and is automatically sent to the origin server upon every request, so it perfectly suits the use case.

### Threaded programming

#### When do you need to use threads in an application?

- A thread is a flow of execution through the process code, with its own program counter that keeps track of which instruction to execute next, system registers which hold its current working variables, and a stack which contains the execution history.
- You need use threads when you are in this situation:
  - Asynchronous operations
  - Operations that can be parallelized
  - Continual running background operations

#### What is a daemon thread?

- Daemon thread is a low priority thread that runs in background to perform tasks such as garbage collection.
- A daemon thread will run until it completes or until all User Threads have completed.
- Daemon threads make "behind the scenes" processes for things that must happen in the background but can be terminated when the application ends - garbage collection is a great example of a process that could be handled with a daemon thread. Once all User Threads complete, any daemon Threads that are still running are automatically halted and the application terminates.

#### What is the difference between concurrent and parallel execution of code?

- Concurrency means that an application is making progress on more than one task at the same time (concurrently).
- Parallelism means that an application splits its tasks up into smaller subtasks which can be processed in parallel, for instance on multiple CPUs at the exact same time.

#### What is the most important problem developers are faced when using threads?

- Deadlocks

#### In what kind of situations can deadlocks occur?

- Mutual Exclusion : At least one unsharable resource - processes claim exclusive control of resources they need
- Hold and Wait : Process holds one resource while waiting for another
- No Preemption : Resources only released voluntarily - no interruption possible (i.e. cannot be forcefully withdrawn by another process)
- Circular Wait : Circular chain of processes - each waiting for a resource held by another

#### What are possible ways to prevent deadlocks from occurring?

- Using the wait – die scheme method or wound – wait scheme.

#### What does critical section or critical region mean in the context of concurrent programming?

- In concurrent programming, concurrent accesses to shared resources can lead to unexpected or erroneous behavior, so parts of the program where the shared resource is accessed need to be protected in ways that avoid the concurrent access. This protected section is the critical section or critical region.

---

# Enterprise module (C# branch)

### ASP.NET Core, WCF

#### What Is the difference between .NET Core and .NET Standard? How do them relate to “classic” .NET?

- .NET is a free, cross-platform, open source developer platform for building many different types of applications.
- .NET Core It is an open-source and cross-platform implementation of .NET. It shares many of its characteristics with .NET Framework.
- All aspects of .NET Core are open-source including class libraries, runtime, compilers, languages as well as application frameworks. .NET Core also supports C#, Visual Basic and F#. It can run the application code with the same behavior on multiple architectures, including x64, x86, and ARM. It has a flexible deployment model in which it can be included in the application or installed side-by-side (user-wide or system-wide).
- .NET Standard is a specification (not an implementation of .NET) which defines the set of APIs that all .NET implementations must provide. It addresses the code sharing problem for .NET developers across all platforms by bringing APIs across different environments.
- We can think of it as another .NET Framework, except that we use it to develop class libraries only. .NET Standard is a successor of the portable class library.

#### What is ASP.NET MVC?

- ASP.NET MVC is an open-source software from Microsoft. Its web development framework combines the features of MVC (Model-View-Controller) architecture, the most up-to-date ideas and techniques from Agile development and the best parts of the existing ASP.NET platform.

#### Can you explain Model, Controller and View in MVC?

- Model
  - The Model component corresponds to all the data-related logic that the user works with. This can represent either the data that is being transferred between the View and Controller components or any other business logic-related data.
- View
  - The View component is used for all the UI logic of the application. For example, the Customer view will include all the UI components such as text boxes, dropdowns, etc. that the final user interacts with.
- Controller
  - Controllers act as an interface between Model and View components to process all the business logic and incoming requests, manipulate data using the Model component and interact with the Views to render the final output.

#### Explain the page lifecycle of MVC.

- In a MVC application, all the requests are routed to a special class called the Controller. The controller is responsible for generating the response and sending the content back to the browser. Also, there is a many-to-one mapping between URL and controller.
- When you request a MVC application, you are directly calling the action method of a controller.
- The procedure involved is:
  1. An instance of the RouteTable class is created on application start. This happens only once when the application is requested for the first time.
  2. The UrlRoutingModule intercepts each request, finds a matching RouteData from a RouteTable and instantiates a MVCHandler (an HttpHandler).
  3. The MVCHandler creates a DefaultControllerFactory (you can create your own controller factory also). It processes the RequestContext and gets a specific controller (from the controllers you have written). Creates a ControllerContext. es the controller a ControllerContext and executes the controller.
  4. Gets the ActionMethod from the RouteData based on the URL. The Controller Class then builds a list of parameters (to to the ActionMethod) from the request.
  5. The ActionMethod returns an instance of a class inherited from the ActionResult class and the View Engine renders a view as a web page.

#### What is Razor View Engine?

- Razor View engine is a markup syntax which helps us to write HTML and server-side code in web pages using C# or VB.NET. It is server-side markup language however it is not at all a programming language.
- Razor is a templating engine and ASP.NET MVC has implemented a view engine which allows us to use Razor inside of an MVC application to produce HTML. However, Razor does not have any ties with ASP.NET MVC.

#### What you mean by Routing in MVC?

- Basically, Routing is a pattern matching system that monitor the incoming request and figure out what to do with that request. At runtime, Routing engine use the Route table for matching the incoming request's URL pattern against the URL patterns defined in the Route table. You can register one or more URL patterns to the Route table at Application_Start event

#### What is Layout in MVC?

- An application may contain common parts in the UI which remains the same throughout the application such as the logo, header, left navigation bar, right bar or footer section. ASP.NET MVC introduced a Layout view which contains these common UI parts, so that we don't have to write the same code in every page.

#### What ConfigureServices() method does in Startup.cs?

- This method is used to configure services that are used by the application. When the application is requested for the first time, it calls ConfigureServices method. This method must be declared with a public access modifier, so that environment will be able to read the content from metadata.

#### What Configure() method does in Startup.cs?

- This method is used to define how the application will respond on each HTTP request i.e. we can control the ASP.net pipeline. This method is also used to configure middleware in HTTP pipeline. This method accept IApplicationBuilder as a parameter.

#### What is wwwroot folder in ASP.NET Core?

- By default, the wwwroot folder in the ASP.NET Core project is treated as a web root folder. Static files can be stored in any folder under the web root and accessed with a relative path to that root

#### What’s the usage of [InternalsVisibleTo] attribute? What are pros and cons of it?

- The InternalsVisibleTo attribute is a well-known attribute for testing assemblies. The internal methods of an assembly become visible to the test project. This allows you to test the internal methods without using reflection, so your tests are more maintainable.

#### Explain what is WCF?

- WCF stands for Windows Communication Foundation. It is basically used to create a distributed and interoperable Application. This is a framework, which is used for creating Service oriented Applications. You can send the data asynchronously from one end point to another.

#### Mention what is the endpoint in WCF and what are the three major points in WCF?

- WCF offers its services to its client using an endpoint. An endpoint comprises of three key elements, the address, binding and contract. WCF endpoints provide the necessary resources and directions, which help clients to communicate with the various services WCF offers.

### Object Relational Mapping, Entity Framework

#### What is an ORM? What are benefits, when to use?

- Object Relational Mapping is a technique that lets you query and manipulate data from a database using an object-oriented paradigm. Benefits of using an ORM:
  - DRY code
  - Database handling is done automatically
  - Abstracts the DB system so you can bring changes

#### What is Entity Framework? What are the advantages, limitations?

- Entity Framework is an open-source ORM framework for .NET applications supported by Microsoft. It enables developers to work with data using objects of domain specific classes without focusing on the underlying database tables and columns where this data is stored.
- The advantages of EF are:
  - It provides auto generated code
  - It reduces development time
  - It reduces development cost
  - It enables developers to visually design models and mapping of database
  - It provides capability of programming a conceptual model.

#### What is lazy loading?

- Lazy loading (also called on-demand loading) is an optimization technique for the online content, be it a website or a web app. Instead of loading the entire web page and rendering it to the user in one go as in bulk loading, the concept of lazy loading assists in loading only the required section and delays the remaining, until it is needed by the user.

#### What is the difference between code first and DB first approach?

- In code first approach we will first create entity classes with properties defined in it. Entity framework will create the database and tables based on the entity classes defined. So database is generated from the code. When the dot net code is run database will get created.
- In database first approach Database and tables are created first. Then you create entity Data Model using the created database.

#### What is a migration script?

- Whereas a build script creates a database, a migration script, or ‘change’ script, alters a database. It is called a migration script because it changes all or part of a database from one version to another. It ‘migrates’ it between versions. This alteration can be as simple as adding or removing a column to a table, or a complex refactoring task such as splitting tables or changing column properties in a way that could affect the data it stores.

#### What is a navigation property?

- A navigation property is an optional property on an entity type that allows for navigation from one end of an association to the other end. Unlike other properties, navigation properties do not carry data.

#### Name 3 different attributes used in EF Core, what can they do for you?

- [Required] – property’s value is required [MaxLength] – set maximum length allowed of the property value [Key] – identifies one or more properties as a Key

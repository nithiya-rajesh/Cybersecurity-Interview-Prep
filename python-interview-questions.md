# Python Interview Questions (0–5 Years)

A curated collection of beginner and intermediate level Python interview questions. Includes theory-based Q&A and real-world scenario/coding questions covering core language fundamentals, data structures, OOP, error handling, and practical application.

---

## Table of Contents
1. [Python Basics](#python-basics)
2. [Data Types & Structures](#data-types--structures)
3. [Strings](#strings)
4. [Functions](#functions)
5. [OOP (Object-Oriented Programming)](#oop-object-oriented-programming)
6. [Error Handling & Exceptions](#error-handling--exceptions)
7. [File Handling](#file-handling)
8. [Iterators, Generators & Comprehensions](#iterators-generators--comprehensions)
9. [Decorators & Closures](#decorators--closures)
10. [Modules, Packages & Memory Management](#modules-packages--memory-management)
11. [Multithreading & Multiprocessing](#multithreading--multiprocessing)
12. [Libraries (requests, pandas, etc.)](#libraries-requests-pandas-etc)
13. [Security-Relevant Python (for Security/Automation Roles)](#security-relevant-python-for-securityautomation-roles)
14. [Scenario-Based / Coding Questions (Beginner)](#scenario-based--coding-questions-beginner)
15. [Scenario-Based / Coding Questions (Intermediate)](#scenario-based--coding-questions-intermediate)
16. [Mini Case Study / Debugging Scenarios](#mini-case-study--debugging-scenarios)

---

## Python Basics

**Q1. What is Python and what are its key features?**
A: Python is a high-level, interpreted, dynamically-typed, general-purpose programming language. Key features: simple/readable syntax, extensive standard library, cross-platform support, support for multiple paradigms (procedural, OOP, functional), and a large ecosystem of third-party packages.

**Q2. What is the difference between a compiled language and an interpreted language? Is Python purely interpreted?**
A: Compiled languages convert source code into machine code ahead of execution (e.g., C). Interpreted languages execute code line-by-line at runtime. Python is technically a hybrid — source code is first compiled into bytecode (.pyc), which is then interpreted by the Python Virtual Machine (PVM).

**Q3. What is the difference between Python 2 and Python 3?**
A: Python 3 (the current standard) introduced changes like `print()` as a function (not a statement), integer division returning a float by default (`/`), Unicode strings by default, and improved standard library consistency. Python 2 reached end-of-life in 2020 and shouldn't be used for new projects.

**Q4. What is PEP 8?**
A: PEP 8 is Python's official style guide, covering conventions for naming, indentation (4 spaces), line length, whitespace, and code organization to ensure readable and consistent code across projects.

**Q5. What is the difference between `is` and `==`?**
A: `==` checks value equality (whether two objects have the same value). `is` checks identity (whether two variables point to the exact same object in memory).

**Q6. What is the difference between mutable and immutable objects? Give examples.**
A: Mutable objects can be changed after creation (lists, dictionaries, sets). Immutable objects cannot be changed after creation (strings, tuples, integers, frozensets) — any "modification" actually creates a new object.

**Q7. What is dynamic typing and how does Python implement it?**
A: Dynamic typing means variable types are determined at runtime rather than declared explicitly, and a variable can be reassigned to a different type later. Python implements this by binding names to objects rather than fixing a type to a variable.

**Q8. What is the difference between a local variable and a global variable?**
A: A local variable is defined within a function and only accessible inside it. A global variable is defined at the module level and accessible throughout the module (and inside functions, unless shadowed by a local variable of the same name, requiring the `global` keyword to modify it from within a function).

**Q9. What does the `global` keyword do?**
A: It allows a function to modify a variable defined in the global/module scope, rather than creating a new local variable with the same name inside the function.

**Q10. What is the difference between `*args` and `**kwargs`?**
A: `*args` collects extra positional arguments into a tuple. `**kwargs` collects extra keyword arguments into a dictionary, allowing functions to accept a variable number of arguments.

**Q11. What is the Python Global Interpreter Lock (GIL)?**
A: A mutex that allows only one thread to execute Python bytecode at a time within a single process, even on multi-core systems. This means CPU-bound multithreaded Python programs don't get true parallelism (multiprocessing is used instead for CPU-bound parallel work).

**Q12. What are Python's built-in data types?**
A: Numeric (int, float, complex), Sequence (str, list, tuple, range), Mapping (dict), Set types (set, frozenset), Boolean (bool), and None type (NoneType).

---

## Data Types & Structures

**Q13. What is the difference between a list and a tuple?**
A: A list is mutable (can be modified after creation) and uses `[]`. A tuple is immutable and uses `()`. Tuples are generally faster and used for fixed collections of data (e.g., coordinates), while lists are used for collections that change.

**Q14. What is the difference between a list and a set?**
A: A list is ordered, allows duplicates, and is indexable. A set is unordered, does not allow duplicates, and does not support indexing — but offers fast membership testing (O(1) average) and built-in set operations (union, intersection, difference).

**Q15. What is a dictionary and how does it differ from a list?**
A: A dictionary stores key-value pairs and provides fast lookups by key (O(1) average). A list stores ordered values accessed by integer index. Dictionaries are used when you need to associate data with unique identifiers; lists when order/sequence matters more than lookup speed.

**Q16. How does a Python dictionary work internally?**
A: Dictionaries are implemented as hash tables — each key is hashed to determine its storage location (bucket), allowing average O(1) lookup, insertion, and deletion. Since Python 3.7, dictionaries also maintain insertion order as an implementation detail (now a guaranteed language feature).

**Q17. What is a frozenset?**
A: An immutable version of a set — once created, elements cannot be added or removed. Useful as dictionary keys or set elements (since regular sets, being mutable, cannot be hashed and thus cannot be used as dict keys).

**Q18. What is list slicing and how does it work?**
A: Slicing extracts a portion of a sequence using `sequence[start:stop:step]`. For example, `my_list[1:4]` returns elements at index 1, 2, 3 (stop index excluded); `my_list[::-1]` reverses the list.

**Q19. What is the difference between `append()` and `extend()` on a list?**
A: `append()` adds a single element (even if it's a list, it gets added as one nested element) to the end of a list. `extend()` iterates over an iterable and adds each of its elements individually to the end of the list.

**Q20. What is the difference between shallow copy and deep copy?**
A: A shallow copy (`copy.copy()` or `list[:]`) creates a new outer object but nested objects (like inner lists) still reference the same objects as the original. A deep copy (`copy.deepcopy()`) recursively copies all nested objects, creating fully independent copies.

**Q21. What is a namedtuple and when would you use it?**
A: A factory function from the `collections` module that creates tuple subclasses with named fields, allowing access by name (`point.x`) instead of just index (`point[0]`) — useful for readable, lightweight, immutable data structures without defining a full class.

**Q22. What is the difference between `del`, `remove()`, and `pop()` on a list?**
A: `del list[index]` removes an element by index (no return value). `list.remove(value)` removes the first matching element by value. `list.pop(index)` removes an element by index (default last) and returns it.

**Q23. What are Python sets used for, and what's a real use case?**
A: Sets are used for storing unique items and performing fast membership tests/set operations. Real use case: deduplicating a list of items, or finding common elements between two collections (e.g., `set(list1) & set(list2)`).

---

## Strings

**Q24. Are strings mutable or immutable in Python?**
A: Immutable — once created, a string's content cannot be changed. Any operation that appears to modify a string (like concatenation) actually creates a new string object.

**Q25. What is the difference between `str.format()` and f-strings?**
A: `str.format()` uses placeholders (`{}`) filled via the `.format()` method, e.g., `"{} is {}".format(name, age)`. F-strings (Python 3.6+) embed expressions directly inside string literals prefixed with `f`, e.g., `f"{name} is {age}"`, offering more concise and often faster syntax.

**Q26. What is the difference between `split()` and `join()`?**
A: `split()` breaks a string into a list based on a delimiter (e.g., `"a,b,c".split(",")` → `['a','b','c']`). `join()` does the reverse — combines an iterable of strings into one string using a specified separator (e.g., `",".join(['a','b','c'])` → `"a,b,c"`).

**Q27. What is string interpolation and what are the different ways to do it in Python?**
A: Embedding variable values inside strings. Methods: % formatting (`"%s is %d" % (name, age)`), `.format()` method, and f-strings (most modern/preferred).

**Q28. What is the difference between `strip()`, `lstrip()`, and `rstrip()`?**
A: `strip()` removes leading and trailing whitespace (or specified characters). `lstrip()` removes only from the left (start). `rstrip()` removes only from the right (end).

**Q29. How would you check if a string contains only digits, or only alphabetic characters?**
A: Use `str.isdigit()` to check if all characters are digits, and `str.isalpha()` to check if all characters are alphabetic letters.

---

## Functions

**Q30. What is the difference between a function and a method?**
A: A function is a standalone block of reusable code defined independently. A method is a function defined inside a class and associated with object instances (called using dot notation on an object).

**Q31. What are default arguments, and what is a common pitfall with mutable default arguments?**
A: Default arguments provide a fallback value if no argument is passed (`def func(x=5)`). A common pitfall is using a mutable object (like a list) as a default argument — since default arguments are evaluated only once at function definition time, the same mutable object persists across all calls, leading to unexpected shared state bugs.

**Q32. What is a lambda function and when would you use one?**
A: An anonymous, single-expression function defined using the `lambda` keyword (e.g., `lambda x: x * 2`). Useful for short, throwaway functions, often passed as arguments to functions like `sorted()`, `map()`, or `filter()`.

**Q33. What is the difference between `map()`, `filter()`, and `reduce()`?**
A: `map()` applies a function to every item in an iterable, returning a new iterable of results. `filter()` applies a predicate function and returns only items where it evaluates `True`. `reduce()` (from `functools`) cumulatively applies a function to reduce an iterable to a single accumulated value.

**Q34. What is recursion, and what's a risk associated with it in Python?**
A: A function calling itself to solve a smaller instance of the same problem until reaching a base case. A risk is hitting Python's default recursion limit (typically 1000), causing a `RecursionError` for deeply recursive calls without proper base case termination or for problems better suited to iteration.

**Q35. What is the difference between positional arguments and keyword arguments?**
A: Positional arguments are matched to parameters based on their order in the function call. Keyword arguments are explicitly matched by parameter name, regardless of order (e.g., `func(name="Alice", age=30)`).

**Q36. What is variable scope, and what is the LEGB rule?**
A: Scope determines where a variable is accessible. LEGB describes Python's name resolution order: Local → Enclosing (in nested functions) → Global → Built-in, searched in that order when resolving a variable name.

---

## OOP (Object-Oriented Programming)

**Q37. What are the four main principles of OOP, and how does Python implement them?**
A: Encapsulation (bundling data/methods within a class, using naming conventions like `_protected`/`__private` for access control), Abstraction (hiding implementation details via abstract base classes), Inheritance (a class deriving from another using `class Child(Parent):`), and Polymorphism (the same method name behaving differently across different classes).

**Q38. What is the difference between a class and an object?**
A: A class is a blueprint/template defining attributes and behaviors. An object is a specific instance created from that class, with its own actual data.

**Q39. What is `__init__` and how is it different from a regular method?**
A: `__init__` is a special "dunder" (double underscore) method automatically called when a new object is instantiated, used to initialize the object's attributes — it's not a constructor in the strictest sense (that's `__new__`), but rather an initializer.

**Q40. What is `self` and why is it required in instance methods?**
A: `self` refers to the specific instance calling the method, allowing access to that instance's attributes/methods. It's explicitly required as the first parameter in Python instance methods (unlike some other languages where "this" is implicit) because Python doesn't automatically pass instance context.

**Q41. What is the difference between class variables and instance variables?**
A: Class variables are shared across all instances of a class (defined directly in the class body). Instance variables are unique to each object (typically defined inside `__init__` using `self.variable`).

**Q42. What is method overriding versus method overloading? Does Python support both?**
A: Overriding is when a child class redefines a method already defined in its parent class — Python fully supports this. Overloading (having multiple methods with the same name but different parameters) isn't natively supported in Python the way it is in Java/C++; Python instead handles this via default arguments, `*args`/`**kwargs`, or single-dispatch decorators.

**Q43. What is multiple inheritance, and what is the MRO (Method Resolution Order)?**
A: Multiple inheritance allows a class to inherit from more than one parent class. MRO defines the specific order Python searches through parent classes when resolving a method/attribute, calculated using the C3 linearization algorithm (viewable via `ClassName.__mro__`).

**Q44. What is a static method versus a class method versus an instance method?**
A: An instance method (default, no decorator) takes `self` and operates on instance data. A class method (`@classmethod`) takes `cls` and operates on the class itself, often used for alternative constructors. A static method (`@staticmethod`) takes neither `self` nor `cls` — it's a regular function logically grouped within the class namespace.

**Q45. What is an abstract class, and how do you create one in Python?**
A: A class that cannot be instantiated directly and is meant to be subclassed, typically defining method signatures that subclasses must implement. Created using the `abc` module (`ABC` base class and `@abstractmethod` decorator).

**Q46. What is the difference between `__str__` and `__repr__`?**
A: `__str__` defines the "informal," readable string representation of an object (used by `print()` and `str()`). `__repr__` defines the "official," unambiguous representation (ideally one that could recreate the object), used by the interactive interpreter and as a fallback if `__str__` isn't defined.

**Q47. What is encapsulation in Python, given it doesn't have true "private" access modifiers like Java?**
A: Python uses naming conventions rather than strict enforcement: a single underscore prefix (`_var`) signals "protected"/internal use by convention, and a double underscore prefix (`__var`) triggers name mangling (renamed internally to `_ClassName__var`), making accidental external access harder but not truly impossible.

**Q48. What are dunder (magic) methods? Give a few examples beyond `__init__`.**
A: Special methods surrounded by double underscores that let objects integrate with Python's built-in syntax/operators. Examples: `__len__` (for `len(obj)`), `__eq__` (for `==` comparison), `__add__` (for `+` operator overloading), `__iter__`/`__next__` (for iteration support), `__enter__`/`__exit__` (for context manager support with `with`).

---

## Error Handling & Exceptions

**Q49. What is the difference between an error and an exception in Python?**
A: An error generally refers to a problem that prevents the program from continuing (often syntax errors caught before runtime). An exception is an event that disrupts normal program flow during execution but can be caught and handled using try/except, allowing the program to continue.

**Q50. What is the purpose of `try`, `except`, `else`, and `finally`?**
A: `try` contains code that might raise an exception. `except` catches and handles specific exceptions. `else` runs only if no exception occurred in the try block. `finally` always runs regardless of whether an exception occurred, typically used for cleanup (closing files/connections).

**Q51. What is the difference between catching a specific exception (e.g., `except ValueError`) versus a bare `except:`?**
A: Catching a specific exception only handles that particular error type, allowing other unexpected exceptions to propagate (better practice, easier debugging). A bare `except:` catches all exceptions indiscriminately (including ones you didn't anticipate, like `KeyboardInterrupt`), which can hide bugs and is generally considered poor practice.

**Q52. How do you raise a custom exception in Python?**
A: Define a class inheriting from `Exception` (or a more specific built-in exception), then use `raise CustomException("message")` to trigger it explicitly when a specific error condition is detected.

**Q53. What is exception chaining, and what does `raise ... from ...` do?**
A: Exception chaining preserves the original exception's context when raising a new one in an except block. `raise NewException("msg") from original_exception` explicitly links the two, making debugging easier by showing the full causal chain in the traceback.

**Q54. What happens if an exception is raised inside a `finally` block?**
A: It will override/replace any exception that was being propagated from the try/except blocks, potentially masking the original error — generally something to avoid unless intentional.

---

## File Handling

**Q55. What is the difference between opening a file with `'r'`, `'w'`, `'a'`, and `'r+'` modes?**
A: `'r'` opens for reading only (file must exist). `'w'` opens for writing, truncating/overwriting existing content (creates file if it doesn't exist). `'a'` opens for appending to the end without truncating. `'r+'` opens for both reading and writing without truncating.

**Q56. Why is it recommended to use the `with` statement when working with files?**
A: The `with` statement (context manager) automatically handles closing the file once the block exits — even if an exception occurs — preventing resource leaks and avoiding the need to manually call `file.close()`.

**Q57. What is the difference between `read()`, `readline()`, and `readlines()`?**
A: `read()` reads the entire file content as a single string. `readline()` reads one line at a time. `readlines()` reads all lines and returns them as a list of strings.

**Q58. How would you read a very large file without loading the entire content into memory at once?**
A: Iterate over the file object directly line-by-line (`for line in file:`), which reads lazily rather than loading the whole file into memory, or read in fixed-size chunks using `file.read(chunk_size)` in a loop.

---

## Iterators, Generators & Comprehensions

**Q59. What is the difference between an iterable and an iterator?**
A: An iterable is any object capable of returning its members one at a time (implements `__iter__`), such as a list. An iterator is the object actually produced by calling `iter()` on an iterable, which implements `__next__()` to produce successive values and raises `StopIteration` when exhausted.

**Q60. What is a generator, and how is it different from a regular function?**
A: A generator is a function that uses `yield` instead of `return`, producing a sequence of values lazily (one at a time, pausing state between calls) rather than computing and returning everything at once — useful for memory-efficient iteration over large/infinite sequences.

**Q61. What is the benefit of generator expressions over list comprehensions?**
A: Generator expressions (`(x for x in range(10))`) produce values lazily on demand without storing the entire sequence in memory, making them more memory-efficient for large datasets, whereas list comprehensions (`[x for x in range(10)]`) build and store the full list immediately.

**Q62. What is a list comprehension, and how does it compare to a traditional for loop in terms of readability/performance?**
A: A concise syntax for creating a list by applying an expression to each item in an iterable, optionally with a filter condition (e.g., `[x*2 for x in range(10) if x % 2 == 0]`). It's generally more readable and often slightly faster than the equivalent explicit for loop with `.append()`, due to internal optimizations.

**Q63. What is the difference between `yield` and `return`?**
A: `return` exits a function entirely and sends back a single value, ending execution. `yield` pauses the function's execution, sends back a value, and preserves the function's state so it can resume from where it left off on the next call — enabling generator behavior.

**Q64. What does the `yield from` syntax do?**
A: It delegates iteration to a sub-generator/sub-iterable, effectively yielding all of its values directly, simplifying code that would otherwise require an explicit loop to manually yield each value from a nested generator.

---

## Decorators & Closures

**Q65. What is a closure in Python?**
A: A function object that "remembers" values from its enclosing lexical scope even after that outer function has finished executing, achieved when an inner function references variables from its enclosing function and is returned/used outside that scope.

**Q66. What is a decorator, and how does it work?**
A: A function that takes another function as input and extends/modifies its behavior without permanently changing its source code, typically applied using the `@decorator_name` syntax above a function definition. It works by wrapping the original function inside another function that adds behavior before/after calling it.

**Q67. Write/explain a simple example of a custom decorator that logs how long a function takes to execute.**
A: 
```python
import time
from functools import wraps

def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"{func.__name__} took {time.time() - start:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
```
The `@wraps(func)` preserves the original function's name/docstring metadata, which would otherwise be lost since `wrapper` replaces it.

**Q68. What is the purpose of `functools.wraps` when writing decorators?**
A: It preserves the original wrapped function's metadata (`__name__`, `__doc__`, etc.) on the decorator's returned wrapper function, which would otherwise be overwritten by the wrapper's own metadata — important for debugging, introspection, and tools relying on accurate function identity.

**Q69. Can a decorator accept its own arguments? How?**
A: Yes — by adding an extra layer of nested functions: the outermost function takes the decorator's arguments and returns the actual decorator function, which in turn returns the wrapper, e.g., `@repeat(times=3)` requires `def repeat(times): def decorator(func): def wrapper(*a, **kw): ...`.

---

## Modules, Packages & Memory Management

**Q70. What is the difference between a module and a package?**
A: A module is a single Python file (`.py`) containing code (functions, classes, variables). A package is a directory containing multiple modules along with an `__init__.py` file (making it importable as a namespace), allowing hierarchical organization of related modules.

**Q71. What does `if __name__ == "__main__":` do, and why is it commonly used?**
A: It checks whether the current script is being run directly (in which case `__name__` equals `"__main__"`) versus being imported as a module into another script (where `__name__` would equal the module's actual name). This allows code to run only when the file is executed directly, not when imported.

**Q72. What is a virtual environment, and why is it important in Python projects?**
A: An isolated Python environment with its own independent set of installed packages, separate from the system-wide Python installation. It prevents dependency conflicts between different projects requiring different versions of the same package, and is typically created using `venv` or tools like `virtualenv`/`conda`.

**Q73. What is `pip` and what is a `requirements.txt` file used for?**
A: `pip` is Python's standard package manager for installing/managing third-party libraries. A `requirements.txt` file lists a project's exact dependencies (often with pinned versions), allowing others to recreate the same environment via `pip install -r requirements.txt`.

**Q74. How does Python's garbage collection work?**
A: Python primarily uses reference counting — each object tracks how many references point to it, and when that count reaches zero, the memory is automatically freed. For circular references (objects referencing each other) that reference counting alone can't clean up, Python's garbage collector module periodically detects and collects these cycles.

**Q75. What is the difference between `==` and `is` when comparing small integers, and why might it behave unexpectedly?**
A: Due to CPython's internal optimization (integer caching/interning for small integers, typically -5 to 256), `is` may unexpectedly return `True` for small integers even without explicit interning logic in your code, but this is an implementation detail and shouldn't be relied upon — always use `==` for value comparison and reserve `is` for identity checks like `is None`.

---

## Multithreading & Multiprocessing

**Q76. What is the difference between multithreading and multiprocessing in Python?**
A: Multithreading runs multiple threads within a single process sharing the same memory space, but is limited by the GIL for CPU-bound tasks (though useful for I/O-bound tasks). Multiprocessing runs separate processes, each with its own Python interpreter and memory space, achieving true parallelism for CPU-bound tasks by bypassing the GIL entirely.

**Q77. When would you choose multiprocessing over multithreading (or vice versa)?**
A: Use multithreading for I/O-bound tasks (network requests, file I/O, waiting on external resources) where threads spend time waiting rather than computing. Use multiprocessing for CPU-bound tasks (heavy computation, data processing) where you need to fully utilize multiple CPU cores.

**Q78. What is `asyncio` and how does it differ from threading?**
A: `asyncio` provides single-threaded concurrency using an event loop and coroutines (`async`/`await`), efficiently handling many I/O-bound tasks by cooperatively yielding control during waiting periods, without the overhead/complexity of actual OS-level threads — well-suited for high-concurrency network applications.

**Q79. What is a race condition, and how can it be prevented in Python?**
A: A race condition occurs when multiple threads/processes access and modify shared data concurrently, leading to unpredictable results depending on execution timing. Prevented using synchronization primitives like `threading.Lock` to ensure only one thread modifies shared data at a time.

---

## Libraries (requests, pandas, etc.)

**Q80. What is the `requests` library used for, and how would you make a simple GET request with it?**
A: A popular third-party library for making HTTP requests easily. Example: `response = requests.get("https://api.example.com/data")`, then access `response.status_code`, `response.json()`, or `response.text`.

**Q81. What is the difference between `json.dumps()` and `json.loads()`?**
A: `json.dumps()` converts (serializes) a Python object (dict/list) into a JSON-formatted string. `json.loads()` does the reverse (deserializes) — parsing a JSON string back into a Python object.

**Q82. What is pandas primarily used for, and what is the difference between a Series and a DataFrame?**
A: Pandas is a library for data manipulation/analysis. A Series is a one-dimensional labeled array (like a single column). A DataFrame is a two-dimensional labeled data structure (like a table/spreadsheet), composed of multiple Series sharing the same index.

**Q83. What is the difference between NumPy arrays and Python lists?**
A: NumPy arrays are homogeneous (single data type), fixed-size, and stored contiguously in memory, enabling vectorized operations that are significantly faster than equivalent operations on Python lists, which are heterogeneous, dynamically resizable, and store references to objects rather than raw values.

**Q84. What is a virtual environment manager like `venv` versus a dependency/package manager like `pip`? How do they work together?**
A: `venv` creates an isolated environment (separate Python interpreter/library location); `pip` installs packages into whichever environment is currently active. They're complementary — `venv` provides isolation, `pip` populates that isolated space with the specific packages your project needs.

---

## Security-Relevant Python (for Security/Automation Roles)

**Q85. How would you read and parse a CSV file containing log data in Python?**
A: Use the built-in `csv` module (`csv.reader()` or `csv.DictReader()` for dictionary-style row access) or pandas (`pd.read_csv()`) for larger/more complex analysis needs, iterating through rows to extract/filter relevant fields.

**Q86. How would you make an HTTP request to check if a list of IP addresses are flagged as malicious using a threat intel API?**
A: Use the `requests` library to loop through the IP list, sending a GET/POST request to the API endpoint for each IP (respecting rate limits, ideally with a short delay or async/batch requests), parsing the JSON response for reputation/flag data, and aggregating results into a report.

**Q87. How would you use Python's `re` module to extract all IP addresses from a log file?**
A: Use `re.findall()` with a regex pattern matching the IPv4 format, e.g., `re.findall(r'\b(?:\d{1,3}\.){3}\d{1,3}\b', log_text)`, then optionally validate/deduplicate the matches further (e.g., excluding invalid ranges like `999.999.999.999`).

**Q88. What is the `subprocess` module used for, and what's a security consideration when using it?**
A: It allows Python scripts to spawn and interact with external system processes/commands. Security consideration: avoid using `shell=True` with untrusted/unsanitized input, as it can introduce command injection vulnerabilities — prefer passing arguments as a list and avoiding shell interpretation where possible.

**Q89. How would you securely store and use an API key/secret in a Python script rather than hardcoding it?**
A: Store it as an environment variable (accessed via `os.environ.get("API_KEY")`) or in a `.env` file loaded via a library like `python-dotenv`, ensuring the file is excluded from version control (`.gitignore`), rather than hardcoding the secret directly into the source code.

---

## Scenario-Based / Coding Questions (Beginner)

**S1. Write a function to check if a given string is a palindrome.**
A:
```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]
```
This normalizes case/spacing, then compares the string to its reverse using slicing.

**S2. Write a function to count the frequency of each word in a given sentence.**
A:
```python
def word_frequency(sentence):
    words = sentence.lower().split()
    freq = {}
    for word in words:
        freq[word] = freq.get(word, 0) + 1
    return freq
```
Alternatively, this can be done more concisely using `collections.Counter(words)`.

**S3. You have a list of numbers and need to find all duplicates. How would you do this efficiently?**
A:
```python
def find_duplicates(nums):
    seen = set()
    duplicates = set()
    for n in nums:
        if n in seen:
            duplicates.add(n)
        else:
            seen.add(n)
    return list(duplicates)
```
Using sets gives O(1) average lookup, making this O(n) overall rather than the O(n²) of a naive nested-loop approach.

**S4. How would you merge two dictionaries in Python, where overlapping keys take the value from the second dictionary?**
A: In Python 3.9+: `merged = dict1 | dict2`. In earlier versions: `merged = {**dict1, **dict2}` — in both cases, keys from `dict2` override matching keys from `dict1`.

**S5. Write a function that takes a list of integers and returns only the even numbers, using a list comprehension.**
A:
```python
def get_evens(numbers):
    return [n for n in numbers if n % 2 == 0]
```

**S6. You need to read a file and count the number of lines without loading the whole file into memory. How would you do it?**
A:
```python
def count_lines(filepath):
    count = 0
    with open(filepath) as f:
        for _ in f:
            count += 1
    return count
```
Iterating over the file object line-by-line avoids loading the entire file into memory at once.

**S7. How would you safely convert user input (a string) to an integer, handling cases where the input isn't a valid number?**
A:
```python
def safe_int(value):
    try:
        return int(value)
    except ValueError:
        print(f"'{value}' is not a valid integer")
        return None
```

**S8. Write a function to reverse a list without using the built-in `reverse()` method or slicing.**
A:
```python
def reverse_list(lst):
    result = []
    for item in lst:
        result.insert(0, item)
    return result
```
(Alternatively, using two-pointer in-place swapping is more efficient for large lists: swap elements from both ends moving toward the center.)

**S9. How would you remove duplicate values from a list while preserving the original order?**
A:
```python
def remove_duplicates(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result
```
This preserves order, unlike simply converting to a set (`set(lst)`), which loses original ordering.

**S10. Write a simple class `Employee` with attributes `name` and `salary`, and a method that gives a 10% raise.**
A:
```python
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def give_raise(self):
        self.salary *= 1.10
```

---

## Scenario-Based / Coding Questions (Intermediate)

**S11. You have a large log file (several GB) and need to find all lines containing the word "ERROR" without running out of memory. How would you approach this?**
A:
```python
def find_errors(filepath):
    errors = []
    with open(filepath) as f:
        for line in f:
            if "ERROR" in line:
                errors.append(line.strip())
    return errors
```
Processing line-by-line (rather than `read()` or `readlines()`) keeps memory usage constant regardless of file size, since only one line is held in memory at a time.

**S12. Design a function that takes a list of dictionaries (e.g., employee records) and groups them by a specified key (e.g., department).**
A:
```python
from collections import defaultdict

def group_by_key(records, key):
    grouped = defaultdict(list)
    for record in records:
        grouped[record[key]].append(record)
    return dict(grouped)
```
Using `defaultdict(list)` avoids needing to manually check/initialize each key before appending.

**S13. You need to call an external API that occasionally times out or fails. How would you implement a retry mechanism with exponential backoff?**
A:
```python
import time
import requests

def fetch_with_retry(url, max_retries=5):
    for attempt in range(max_retries):
        try:
            response = requests.get(url, timeout=5)
            response.raise_for_status()
            return response.json()
        except requests.RequestException as e:
            wait = 2 ** attempt
            print(f"Attempt {attempt+1} failed: {e}. Retrying in {wait}s...")
            time.sleep(wait)
    raise Exception("Max retries exceeded")
```
This doubles the wait time on each failure (exponential backoff), reducing load on a struggling API while still attempting recovery.

**S14. How would you implement a simple LRU (Least Recently Used) cache in Python?**
A: Use `functools.lru_cache` as a decorator for straightforward function-level caching:
```python
from functools import lru_cache

@lru_cache(maxsize=128)
def expensive_computation(n):
    return n * n
```
For a manual implementation, `collections.OrderedDict` (or a plain dict in Python 3.7+) can track insertion/access order, moving accessed items to the end and evicting from the front once `maxsize` is exceeded.

**S15. You're processing a CSV file of user records and need to validate that each row has a properly formatted email address before inserting it into a database. How would you structure this?**
A:
```python
import csv
import re

EMAIL_PATTERN = r'^[\w\.-]+@[\w\.-]+\.\w+$'

def validate_and_process(filepath):
    valid_rows, invalid_rows = [], []
    with open(filepath) as f:
        reader = csv.DictReader(f)
        for row in reader:
            if re.match(EMAIL_PATTERN, row.get("email", "")):
                valid_rows.append(row)
            else:
                invalid_rows.append(row)
    return valid_rows, invalid_rows
```
Separating valid/invalid rows allows the valid ones to proceed to database insertion while invalid ones can be logged/reported separately rather than crashing the entire batch process.

**S16. How would you write a context manager (using a class, not a decorator) to measure execution time of a code block?**
A:
```python
import time

class Timer:
    def __enter__(self):
        self.start = time.time()
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        self.elapsed = time.time() - self.start
        print(f"Elapsed: {self.elapsed:.4f}s")

# Usage:
with Timer():
    time.sleep(1)
```
Implementing `__enter__` and `__exit__` makes the class usable with the `with` statement, ensuring the timing logic runs even if an exception occurs inside the block.

**S17. You need to process a large dataset using multiple CPU cores to speed up a CPU-bound calculation. How would you approach this in Python?**
A:
```python
from multiprocessing import Pool

def square(n):
    return n * n

if __name__ == "__main__":
    numbers = list(range(1000000))
    with Pool(processes=4) as pool:
        results = pool.map(square, numbers)
```
Using `multiprocessing.Pool` distributes the workload across separate processes (bypassing the GIL), which is necessary for true parallelism on CPU-bound tasks, unlike threading which would offer no speedup here.

**S18. How would you design a custom exception hierarchy for an application that processes orders, distinguishing between validation errors and payment errors?**
A:
```python
class OrderError(Exception):
    """Base exception for order processing."""
    pass

class ValidationError(OrderError):
    """Raised when order data fails validation."""
    pass

class PaymentError(OrderError):
    """Raised when payment processing fails."""
    pass

# Usage:
try:
    process_order(order)
except ValidationError as e:
    log_and_notify_user(e)
except PaymentError as e:
    retry_payment(e)
except OrderError as e:
    handle_generic_order_error(e)
```
A common base class (`OrderError`) allows catching all order-related errors generically when needed, while specific subclasses allow precise, targeted handling for each error type.

**S19. You have a function that's being called repeatedly with the same expensive-to-compute arguments. How would you optimize this without restructuring the calling code?**
A: Apply memoization using the `functools.lru_cache` decorator directly on the function definition:
```python
from functools import lru_cache

@lru_cache(maxsize=None)
def expensive_function(x, y):
    # expensive computation
    return x ** y
```
This caches results based on input arguments, so repeated calls with the same arguments return instantly from cache rather than recomputing — transparent to any existing calling code.

**S20. Design a simple decorator that restricts how many times a function can be called (e.g., a rate limiter), raising an exception if exceeded.**
A:
```python
from functools import wraps

def rate_limit(max_calls):
    def decorator(func):
        call_count = 0
        @wraps(func)
        def wrapper(*args, **kwargs):
            nonlocal call_count
            if call_count >= max_calls:
                raise RuntimeError(f"{func.__name__} call limit exceeded")
            call_count += 1
            return func(*args, **kwargs)
        return wrapper
    return decorator

@rate_limit(max_calls=3)
def call_api():
    print("API called")
```
The `nonlocal` keyword allows the inner `wrapper` function to modify `call_count`, which lives in the enclosing `decorator` function's scope — a practical use of closures.

**S21. You're given a nested dictionary/JSON structure of arbitrary depth and need to flatten it into a single-level dictionary with dot-separated keys (e.g., `{"a": {"b": 1}}` → `{"a.b": 1}`). How would you implement this?**
A:
```python
def flatten_dict(d, parent_key=""):
    items = {}
    for key, value in d.items():
        new_key = f"{parent_key}.{key}" if parent_key else key
        if isinstance(value, dict):
            items.update(flatten_dict(value, new_key))
        else:
            items[new_key] = value
    return items
```
This uses recursion to handle arbitrary nesting depth, building up the dotted key path as it descends into nested dictionaries.

---

## Mini Case Study / Debugging Scenarios

**C1. The Mutable Default Argument Bug**
*Scenario:* A teammate wrote the following function, and it's behaving strangely — each call to `add_item()` seems to "remember" items from previous unrelated calls:
```python
def add_item(item, item_list=[]):
    item_list.append(item)
    return item_list
```
*Discussion points:* Why does this happen (relating to when default arguments are evaluated)? What's the correct fix (using `None` as the default and creating a new list inside the function if not provided)? What does this reveal about a common Python pitfall that even experienced developers fall into?

**C2. The Off-by-One Slicing Confusion**
*Scenario:* A junior developer is confused why `my_list[2:5]` doesn't include the element at index 5, and why `my_list[-1]` returns the last element instead of erroring out.
*Discussion points:* How would you explain Python's slicing semantics (start inclusive, stop exclusive) clearly with a concrete example? How does negative indexing work conceptually (counting from the end)? What's a good mental model or visualization to help someone internalize this permanently?

**C3. The Silent Failure from a Bare Except**
*Scenario:* A production script has been silently failing to process about 5% of records for weeks, but no errors ever appeared in the logs. Upon code review, you find:
```python
try:
    process_record(record)
except:
    pass
```
*Discussion points:* Why is a bare `except: pass` particularly dangerous in production code? What should have been done instead (catching specific exceptions, logging the error even if "handled")? How would you refactor this to surface failures for monitoring while still allowing the batch process to continue for other records?

**C4. The Slow Loop That Should Have Been a Set**
*Scenario:* A data pipeline processes two large lists (each with ~500,000 items) to find common elements using a nested for loop, and it's taking over 10 minutes to run:
```python
common = []
for item in list_a:
    if item in list_b:
        common.append(item)
```
*Discussion points:* Why is this O(n×m) and how does converting `list_b` to a set change the time complexity of the `in` check to O(1) average? How would you rewrite this for significant performance improvement (`set(list_a) & set(list_b)`)? What does this illustrate about choosing the right data structure for the access pattern you actually need?

**C5. The Shared Mutable State Across Threads**
*Scenario:* A multithreaded script increments a shared global counter across multiple threads to track processed items, but the final count is consistently lower than expected (e.g., expecting 10,000 but getting 9,847):
```python
counter = 0
def process_item():
    global counter
    counter += 1
```
*Discussion points:* Why does this race condition occur even though Python has a GIL (the GIL doesn't make compound operations like `+=` atomic)? How would you fix this using a `threading.Lock`? Would this issue also occur with `multiprocessing` instead of `threading`, and why or why not (separate memory spaces requiring different shared-state mechanisms like `multiprocessing.Value`)?

---

## How to Use This for Practice

- For **0–1 years**: Focus on Python Basics, Data Types & Structures, Strings, Functions, basic OOP Q&A, and Beginner Scenarios.
- For **1–3 years**: Add Error Handling, File Handling, Iterators/Generators, Decorators/Closures, basic library usage (requests/pandas), and Intermediate Scenarios.
- For **3–5 years**: Focus on Multithreading/Multiprocessing, advanced OOP (MRO, abstract classes, dunder methods), memory management internals, security-relevant Python, and be ready to debug/optimize real code in the mini case studies.

---

*Feel free to fork, expand, and contribute additional questions via pull requests.*

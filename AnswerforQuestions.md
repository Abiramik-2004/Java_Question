# Java Collection Framework – 14 Important Interview Questions

## 1. What is the Collection Framework?

The Collection Framework is a set of classes and interfaces in Java used to store and manipulate groups of objects.

Examples:

- List
- Set
- Queue
- Map

It provides ready-made methods to add, remove, search, and sort elements.

```
ArrayList<String> names = new ArrayList<>();

names.add("Abirami");
names.add("Priya");

System.out.println(names);
```

## 2. Difference between List, Set, and Map?

| List                                                    | Set                             | Map                             |
| ------------------------------------------------------- | ------------------------------- | ------------------------------- |
| Allows duplicates                                       | Does not allow duplicates       | Stores key-value pairs          |
| Maintains insertion order (depending on implementation) | Order depends on implementation | Order depends on implementation |
| Access elements using index                             | No index-based access           | Access values using keys        |
| Example: ArrayList                                      | Example: HashSet                | Example: HashMap                |

Remember:

- List → Duplicates allowed.
- Set → Duplicates not allowed.
- Map → Key-value pairs.

## 3. Difference between ArrayList and LinkedList?

| ArrayList                                                      | LinkedList                                                            |
| -------------------------------------------------------------- | --------------------------------------------------------------------- |
| Uses a dynamic array                                           | Uses a doubly linked list                                             |
| Faster for accessing elements by index                         | Slower for accessing elements by index                                |
| Insertion/deletion in the middle may require shifting elements | Insertion/deletion can be faster when the position is already reached |
| Uses less memory                                               | Uses more memory due to node references                               |

Example:

```
ArrayList<Integer> list1 = new ArrayList<>();
LinkedList<Integer> list2 = new LinkedList<>();
```

Remember:

- ArrayList → Faster random access.
- LinkedList → Efficient insertion/deletion at known positions.

## 4. Difference between HashMap and Hashtable?

| HashMap                     | Hashtable                               |
| --------------------------- | --------------------------------------- |
| Not synchronized            | Synchronized                            |
| Not thread-safe by default  | Thread-safe for individual operations   |
| Allows one null key         | Does not allow null keys                |
| Allows multiple null values | Does not allow null values              |
| Generally faster            | Generally slower due to synchronization |
| Introduced in Java 1.2      | Legacy class                            |

Remember:\
HashMap → Not synchronized.

Hashtable → Synchronized.

## 5. How does HashMap work internally?

HashMap stores data in key-value pairs.

It internally uses an array of buckets and hashing.

Working steps:

1. We insert a key-value pair using `put()`.
2. HashMap calls the key's `hashCode()` method.
3. It calculates the bucket index using the hash.
4. It stores the key-value pair in that bucket.
5. When retrieving using `get()`, it calculates the bucket index again and uses `equals()` to identify the correct key.

Example:

```
HashMap<Integer, String> map = new HashMap<>();

map.put(1, "Java");
map.put(2, "Python");

System.out.println(map.get(1));
```

Output:

```
Java
```

Remember:

- `hashCode()` → Finds the bucket.
- `equals()` → Identifies the correct key.

## 6. Difference between HashSet and TreeSet?

| HashSet                   | TreeSet                                   |
| ------------------------- | ----------------------------------------- |
| Does not allow duplicates | Does not allow duplicates                 |
| Does not guarantee order  | Stores elements in sorted order           |
| Uses hashing internally   | Uses a Red-Black Tree internally          |
| Generally faster          | Generally slower                          |
| Allows one null element   | Does not allow null with natural ordering |

Remember:

- HashSet → No duplicates, no guaranteed order.
- TreeSet → No duplicates, sorted order.

## 7. Can HashMap contain null keys and values?

Yes.

- HashMap allows only one null key.
- It allows multiple null values.

Example:

```
HashMap<Integer, String> map = new HashMap<>();

map.put(null, "Java");
map.put(1, null);
map.put(2, null);

System.out.println(map);
```

Output (order may vary):

```
{null=Java, 1=null, 2=null}
```

## 8. What is ConcurrentHashMap?

ConcurrentHashMap is a thread-safe implementation of the Map interface.

- It allows multiple threads to access and modify the map safely.
- It provides better concurrency than Hashtable.
- It does not allow null keys or null values.
- It uses fine-grained synchronization and CAS operations internally.

Example:

```
ConcurrentHashMap<Integer, String> map =
    new ConcurrentHashMap<>();

map.put(1, "Java");
map.put(2, "Python");
```

Remember: ConcurrentHashMap → Thread-safe Map for concurrent access.

## 9. Difference between Comparable and Comparator?

Both are used to sort objects in Java.

| Comparable                           | Comparator                             |
| ------------------------------------ | -------------------------------------- |
| Used for natural ordering            | Used for custom ordering               |
| Located in `java.lang`               | Located in `java.util`                 |
| Uses `compareTo()`                   | Uses `compare()`                       |
| Implemented by the class itself      | Can be implemented separately          |
| Usually defines one natural ordering | Can define multiple sorting strategies |

Comparable example:

```
class Student implements Comparable<Student> {
    int age;

    public int compareTo(Student s) {
        return this.age - s.age;
    }
}
```

Comparator example:

```
Comparator<Student> c =
    (s1, s2) -> s1.age - s2.age;
```

Remember:

- Comparable → `compareTo()`
- Comparator → `compare()`

## 10. What is Iterator?

Iterator is an interface in Java used to traverse elements of a collection one by one.

Important methods:

- `hasNext()` → Checks whether the next element exists.
- `next()` → Returns the next element.
- `remove()` → Removes the current element (optional operation).

Example:

```
ArrayList<String> list = new ArrayList<>();

list.add("Java");
list.add("Python");

Iterator<String> it = list.iterator();

while (it.hasNext()) {
    System.out.println(it.next());
}
```

Output:

```
Java
Python
```

## 11. Difference between Iterator and ListIterator?

| Iterator               | ListIterator                         |
| ---------------------- | ------------------------------------ |
| Works with collections | Works only with List                 |
| Forward direction only | Forward and backward directions      |
| Can read elements      | Can read and modify elements         |
| Uses `hasNext()`       | Uses `hasNext()` and `hasPrevious()` |
| Cannot add elements    | Can add elements                     |

Remember:

- Iterator → Forward only.
- ListIterator → Forward and backward.

## 12. What is fail-fast and fail-safe?

These terms describe how iterators behave when a collection is structurally modified during iteration.

| Fail-fast                                 | Fail-safe (informal term)                                  |
| ----------------------------------------- | ---------------------------------------------------------- |
| May throw ConcurrentModificationException | Does not throw that exception for concurrent modifications |
| Iterates over the original collection     | Often iterates over a snapshot or weakly consistent view   |
| Example: ArrayList iterator               | Example: CopyOnWriteArrayList iterator                     |

Fail-fast example:

```
ArrayList<Integer> list =
    new ArrayList<>();

list.add(10);
list.add(20);

Iterator<Integer> it = list.iterator();

while (it.hasNext()) {
    System.out.println(it.next());
    list.add(30); // May throw exception
}
```

Remember:

- Fail-fast → Detects unexpected structural modification.
- Fail-safe → Informal term for iterators that tolerate concurrent modification.

## 13. How does HashSet internally work?

HashSet internally uses HashMap to store elements.

Working:

1. When we add an element using `add()`, HashSet internally calls `HashMap.put()`.
2. The element is stored as a key in HashMap.
3. A constant dummy object is stored as its value.
4. HashSet uses `hashCode()` and `equals()` to identify duplicates.

Example:

```
HashSet<Integer> set = new HashSet<>();

set.add(10);
set.add(20);
set.add(10);

System.out.println(set);
```

Output (order may vary):

```
[10, 20]
```

Remember: HashSet = HashMap internally, where elements are stored as keys.

## 14. What happens when two keys have the same hashcode?

This situation is called a Hash Collision.

- Two different keys can have the same hashcode.
- HashMap stores them in the same bucket.
- It uses `equals()` to check whether the keys are equal.
- If they are different, both entries can exist in the same bucket.
- If they are equal, the existing value is updated.

Example:

```
HashMap<String, Integer> map = new HashMap<>();

map.put("Aa", 10);
map.put("BB", 20);
```

Both `"Aa"` and `"BB"` have the same hashcode in Java, but they are different strings.

Therefore, both entries can be stored.

Remember:

- Same hashcode + different keys → Collision.
- Same hashcode + equal keys → Existing value gets updated.

## Quick Revision – All 14 Questions

| No. | Question                 | Key point to remember               |
| --- | ------------------------ | ----------------------------------- |
| 1   | Collection Framework     | Stores and manipulates objects      |
| 2   | List vs Set vs Map       | Duplicates, unique, key-value       |
| 3   | ArrayList vs LinkedList  | Dynamic array vs doubly linked list |
| 4   | HashMap vs Hashtable     | Non-synchronized vs synchronized    |
| 5   | HashMap internal working | Hashing + buckets                   |
| 6   | HashSet vs TreeSet       | Hashing vs sorted tree              |
| 7   | HashMap null values      | One null key, multiple null values  |
| 8   | ConcurrentHashMap        | Thread-safe Map                     |
| 9   | Comparable vs Comparator | compareTo() vs compare()            |
| 10  | Iterator                 | Traversing collection               |
| 11  | Iterator vs ListIterator | Forward vs bidirectional            |
| 12  | Fail-fast vs Fail-safe   | Modification behaviour              |
| 13  | HashSet internal working | Uses HashMap                        |
| 14  | Hash collision           | Same hashcode                       |


# 4. Java 8 Features – Important Interview Questions

Java 8 is one of the most important versions of Java for interviews. It introduced features that make code shorter, cleaner, and easier to maintain.

I'll explain each question in simple English with examples, followed by coding questions with Java 8 solutions.

## 1. What are the major features of Java 8?

Java 8 introduced several important features:

| Feature                      | Purpose                                       |
| ---------------------------- | --------------------------------------------- |
| Lambda Expressions           | Write shorter code                            |
| Functional Interfaces        | Interface with exactly one abstract method    |
| Stream API                   | Process collections easily                    |
| Optional                     | Handle null values safely                     |
| Method References            | Refer to methods using `::`                   |
| Default Methods              | Methods with implementation inside interfaces |
| Static Methods in Interfaces | Define utility methods inside interfaces      |
| forEach()                    | Iterate through collection elements           |
| New Date and Time API        | Handle dates and times easily                 |

Interview answer: Java 8 introduced Lambda Expressions, Functional Interfaces, Stream API, Optional, Method References, and default and static methods in interfaces.

## 2. What is a Lambda Expression?

A Lambda Expression is a short way of writing an implementation of a functional interface without creating a separate class.

It reduces boilerplate code.

Syntax:

```
(parameters) -> { body }
```

Without Lambda:

```
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hello Java");
    }
};

r.run();
```

With Lambda:

```
Runnable r = () -> {
    System.out.println("Hello Java");
};

r.run();
```

Output:

```
Hello Java
```

Remember:

Lambda Expression = Shorter way to implement a functional interface.

## 3. What is a Functional Interface?

A Functional Interface is an interface that contains exactly one abstract method.

It can contain:

- One abstract method.
- Multiple default methods.
- Multiple static methods.

We can use the `@FunctionalInterface` annotation to indicate our intention and let the compiler check the rule.

Example:

```
@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}

class Main {
    public static void main(String[] args) {

        Calculator c = (a, b) -> a + b;

        System.out.println(c.add(10, 20));
    }
}
```

Output:

```
30
```

Important built-in functional interfaces:

| Interface | Purpose                             |
| --------- | ----------------------------------- |
| Predicate | Takes input and returns boolean     |
| Function  | Takes input and returns output      |
| Consumer  | Takes input and returns nothing     |
| Supplier  | Takes no input and supplies a value |

Remember: Functional Interface = Exactly one abstract method.

## 4. What is the Stream API?

Stream API is a Java 8 feature used to process collections of data in a clean and simple way.

It supports operations such as:

- Filtering
- Sorting
- Mapping
- Counting
- Collecting

Example:

Find even numbers from a list.

```
import java.util.*;

class Main {
    public static void main(String[] args) {

        List<Integer> numbers =
            Arrays.asList(10, 15, 20, 25, 30);

        numbers.stream()
               .filter(n -> n % 2 == 0)
               .forEach(System.out::println);
    }
}
```

Output:

```
10
20
30
```

Remember:

Stream API = Process collection data using operations like filter, map and sort.

Important points:

- A Stream does not store data.
- It does not modify the original collection by itself.
- A Stream cannot be reused after a terminal operation.
- Streams support sequential and parallel processing.

## 5. Difference between map() and flatMap()?

| map()                           | flatMap()                               |
| ------------------------------- | --------------------------------------- |
| Transforms each element         | Transforms and flattens elements        |
| One input produces one output   | One input can produce multiple outputs  |
| Does not flatten nested streams | Combines nested streams into one stream |

Example using map():

```
List<String> names =
    Arrays.asList("java", "python");

List<String> result = names.stream()
    .map(String::toUpperCase)
    .collect(Collectors.toList());

System.out.println(result);
```

Output:

```
[JAVA, PYTHON]
```

Example using flatMap():

```
List<List<Integer>> numbers =
    Arrays.asList(
        Arrays.asList(1, 2),
        Arrays.asList(3, 4)
    );

List<Integer> result = numbers.stream()
    .flatMap(list -> list.stream())
    .collect(Collectors.toList());

System.out.println(result);
```

Output:

```
[1, 2, 3, 4]
```

Remember:

- map() → Transform.
- flatMap() → Transform + Flatten.

## 6. Difference between filter() and map()?

| filter()                                  | map()                                          |
| ----------------------------------------- | ---------------------------------------------- |
| Used to select elements                   | Used to transform elements                     |
| Takes a Predicate                         | Takes a Function                               |
| Returns elements that satisfy a condition | Returns transformed elements                   |
| Output may contain fewer elements         | Normally maintains the same number of elements |

filter() example:

```
List<Integer> numbers =
    Arrays.asList(10, 15, 20, 25);

numbers.stream()
       .filter(n -> n > 15)
       .forEach(System.out::println);
```

Output:

```
20
25
```

map() example:

```
List<Integer> numbers =
    Arrays.asList(10, 20, 30);

numbers.stream()
       .map(n -> n * 2)
       .forEach(System.out::println);
```

Output:

```
20
40
60
```

Remember:

- filter() → Select.
- map() → Transform.

## 7. What is Optional?

`Optional` is a Java 8 class used to handle null values and reduce `NullPointerException`.

Instead of directly returning null, we can use Optional to represent a value that may or may not be present.

Example:

```
import java.util.Optional;

class Main {
    public static void main(String[] args) {

        String name = "Abirami";

        Optional<String> result =
            Optional.ofNullable(name);

        System.out.println(result.orElse("Default Name"));
    }
}
```

Output:

```
Abirami
```

Important methods:

| Method          | Purpose                                |
| --------------- | -------------------------------------- |
| `of()`          | Creates Optional with a non-null value |
| `ofNullable()`  | Allows null values                     |
| `isPresent()`   | Checks whether value exists            |
| `orElse()`      | Returns default value if empty         |
| `orElseThrow()` | Throws exception if empty              |
| `get()`         | Returns the value if present           |

Remember: Optional helps avoid unexpected null-related errors.

## 8. What is the purpose of the forEach() method?

`forEach()` is used to iterate through elements in a collection or Stream.

It was introduced as a default method in the Iterable interface in Java 8.

Example:

```
List<String> names =
    Arrays.asList("Abirami", "Priya", "Kavi");

names.forEach(name -> System.out.println(name));
```

Output:

```
Abirami
Priya
Kavi
```

We can also use a method reference:

```
names.forEach(System.out::println);
```

Remember: forEach() is used to perform an action on every element.

## 9. What are default and static methods in interfaces?

Java 8 introduced default and static methods in interfaces.

Default Method:

- Declared using the `default` keyword.
- Contains a method implementation.
- Can be inherited and overridden by implementing classes.

Example:

```
interface Animal {

    default void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog implements Animal {
}

class Main {
    public static void main(String[] args) {

        Dog d = new Dog();
        d.sound();
    }
}
```

Output:

```
Animal makes sound
```

Static Method:

- Declared using the `static` keyword.
- Contains a method implementation.
- Called using the interface name.
- Not inherited as an instance method by implementing classes.

Example:

```
interface Calculator {

    static void display() {
        System.out.println("Calculator");
    }
}

class Main {
    public static void main(String[] args) {

        Calculator.display();
    }
}
```

Output:

```
Calculator
```

Difference:

| Default Method                    | Static Method                              |
| --------------------------------- | ------------------------------------------ |
| Uses `default` keyword            | Uses `static` keyword                      |
| Called using an object            | Called using interface name                |
| Can be overridden                 | Cannot be overridden as an instance method |
| Inherited by implementing classes | Not inherited as an instance method        |

Remember:

- Default → Object level.
- Static → Interface level.

## 10. Difference between intermediate and terminal operations?

Stream API operations are divided into two types.

Intermediate Operations:

- Transform or filter stream elements.
- Return another Stream.
- Execute lazily (when a terminal operation triggers processing).

Examples:

- `filter()`
- `map()`
- `sorted()`
- `distinct()`
- `limit()`

Terminal Operations:

- Produce a final result or perform an action.
- Trigger stream processing.
- Stream cannot be reused after a terminal operation.

Examples:

- `forEach()`
- `collect()`
- `count()`
- `reduce()`
- `findFirst()`

Example:

```
List<Integer> numbers =
    Arrays.asList(10, 15, 20, 25, 30);

List<Integer> result = numbers.stream()
    .filter(n -> n % 2 == 0)   // Intermediate
    .map(n -> n * 2)           // Intermediate
    .collect(Collectors.toList()); // Terminal

System.out.println(result);
```

Output:

```
[20, 40, 60]
```

| Intermediate                  | Terminal                          |
| ----------------------------- | --------------------------------- |
| Returns Stream                | Returns result or performs action |
| Lazy execution                | Triggers execution                |
| Can chain multiple operations | Ends the stream pipeline          |
| Example: filter(), map()      | Example: collect(), count()       |

Remember:

Intermediate = Processing.

Terminal = Final result.

# Java 8 Important Coding Questions

These are especially important because interviewers may ask you to write programs using Streams and Lambda Expressions.

## 1. Find even numbers from a list

Question: Given a list of numbers, print only even numbers.

```
import java.util.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        List<Integer> numbers =
            Arrays.asList(10, 15, 20, 25, 30);

        List<Integer> result = numbers.stream()
            .filter(n -> n % 2 == 0)
            .collect(Collectors.toList());

        System.out.println(result);
    }
}
```

Output:

```
[10, 20, 30]
```

Logic:

1. `stream()` converts the list into a Stream.
2. `filter()` selects even numbers.
3. `collect()` converts the result back into a List.

## 2. Find duplicate elements

Question: Find duplicate numbers from a list.

```
import java.util.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        List<Integer> numbers =
            Arrays.asList(10, 20, 30, 10, 20, 40);

        Set<Integer> seen = new HashSet<>();

        Set<Integer> duplicates = numbers.stream()
            .filter(n -> !seen.add(n))
            .collect(Collectors.toSet());

        System.out.println(duplicates);
    }
}
```

Output (order may vary):

```
[10, 20]
```

Logic:

- `seen.add(n)` returns true if the element is new.
- It returns false if the element already exists.
- `!seen.add(n)` identifies duplicates.

## 3. Find the second-highest number

Question: Find the second-highest distinct number from a list.

```
import java.util.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        List<Integer> numbers =
            Arrays.asList(10, 50, 30, 40, 50, 20);

        Integer secondHighest = numbers.stream()
            .distinct()
            .sorted(Comparator.reverseOrder())
            .skip(1)
            .findFirst()
            .orElse(null);

        System.out.println(secondHighest);
    }
}
```

Output:

```
40
```

Logic:

1. `distinct()` removes duplicates.
2. `sorted()` sorts in descending order.
3. `skip(1)` skips the highest number.
4. `findFirst()` returns the second-highest number.

## 4. Sort a list of strings

Question: Sort names alphabetically.

```
import java.util.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        List<String> names =
            Arrays.asList("Ravi", "Abirami", "Priya", "Kavi");

        List<String> result = names.stream()
            .sorted()
            .collect(Collectors.toList());

        System.out.println(result);
    }
}
```

Output:

```
[Abirami, Kavi, Priya, Ravi]
```

For descending order:

```
.sorted(Comparator.reverseOrder())
```

## 5. Count the frequency of characters

Question: Count how many times each character appears in a String.

```
import java.util.*;
import java.util.function.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        String str = "programming";

        Map<Character, Long> result = str.chars()
            .mapToObj(c -> (char) c)
            .collect(Collectors.groupingBy(
                Function.identity(),
                LinkedHashMap::new,
                Collectors.counting()
            ));

        System.out.println(result);
    }
}
```

Output:

```
{p=1, r=2, o=1, g=2, a=1, m=2, i=1, n=1}
```

Logic:

- `chars()` converts the String into character values.
- `mapToObj()` converts them into Character objects.
- `groupingBy()` groups identical characters.
- `counting()` counts their occurrences.

## 6. Convert a List into a Map

Question: Convert a list of names into a Map where the name is the key and its length is the value.

```
import java.util.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        List<String> names =
            Arrays.asList("Java", "Python", "React");

        Map<String, Integer> result = names.stream()
            .collect(Collectors.toMap(
                name -> name,
                name -> name.length()
            ));

        System.out.println(result);
    }
}
```

Output (order may vary):

```
{Java=4, Python=6, React=5}
```

Logic:

- First argument → Key.
- Second argument → Value.

Note: If duplicate keys are possible, provide a merge function to `toMap()` to handle them.

## 7. Find the first non-repeated character

Question: Find the first character that appears only once in a String.

Example:

```
Input: swiss
Output: w
```

Solution:

```
import java.util.*;
import java.util.function.*;
import java.util.stream.*;

class Main {
    public static void main(String[] args) {

        String str = "swiss";

        Character result = str.chars()
            .mapToObj(c -> (char) c)
            .collect(Collectors.groupingBy(
                Function.identity(),
                LinkedHashMap::new,
                Collectors.counting()
            ))
            .entrySet()
            .stream()
            .filter(entry -> entry.getValue() == 1)
            .map(Map.Entry::getKey)
            .findFirst()
            .orElse(null);

        System.out.println(result);
    }
}
```

Output:

```
w
```

Logic:

1. Convert String into characters.
2. Count each character's frequency.
3. Use `LinkedHashMap` to preserve insertion order.
4. Filter characters whose count is 1.
5. Return the first character.

## Quick Revision – Java 8

| Interview question     | One-line answer                              |
| ---------------------- | -------------------------------------------- |
| Lambda Expression      | Short way to implement functional interfaces |
| Functional Interface   | Exactly one abstract method                  |
| Stream API             | Process collection data                      |
| map()                  | Transforms elements                          |
| flatMap()              | Transforms and flattens                      |
| filter()               | Selects elements                             |
| Optional               | Handles possible null values                 |
| forEach()              | Iterates through elements                    |
| Default Method         | Interface method with implementation         |
| Static Method          | Interface-level utility method               |
| Intermediate Operation | Returns another Stream                       |
| Terminal Operation     | Produces final result or action              |

## Important: What should you practise first?

My suggested order for your Java interview preparation:

1. Lambda Expressions
2. Functional Interfaces (Predicate, Function, Consumer, Supplier)
3. Stream API
4. `filter()` vs `map()`
5. `map()` vs `flatMap()`
6. Second-highest number
7. Duplicate elements
8. Character frequency
9. First non-repeated character
10. Optional

Interview tip: Don't just memorize the Stream API code. Understand what each method does. Interviewers often change the input or ask you to solve a similar problem with a different condition.

# Java Interview Preparation – Multithreading & Exception Handling

These are two very important Core Java interview topics. I'll explain each question in simple English, with examples and short interview answers that you can remember.

# Part 1: Multithreading

## 1. What is a Thread?

A thread is a lightweight unit of execution within a process.

- It is used to perform multiple tasks concurrently.
- Multiple threads can run within the same process.
- Threads share the process's memory and resources.

Example:

In a music application:

- One thread plays music.
- Another thread downloads songs.
- Another thread handles user interactions.

All these tasks can happen concurrently.

Interview answer: A thread is the smallest unit of execution within a process that allows multiple tasks to run concurrently.

## 2. Difference between Process and Thread?

| Process                                  | Thread                                        |
| ---------------------------------------- | --------------------------------------------- |
| Independent program in execution         | Small unit of execution inside a process      |
| Has its own memory space                 | Shares process memory                         |
| More resource-intensive                  | Less resource-intensive                       |
| Communication is comparatively expensive | Communication is easier through shared memory |
| Failure is generally isolated            | A thread failure can affect the whole process |

Example:

- Process → Running Chrome browser.
- Thread → One task running inside Chrome.

Remember:

- Process → Independent program.
- Thread → Part of a process.

## 3. How can you create a thread in Java?

There are two common traditional ways to create and run a thread.

Method 1: Extending Thread class

```
class MyThread extends Thread {

    public void run() {
        System.out.println("Thread is running");
    }
}

class Main {
    public static void main(String[] args) {

        MyThread t = new MyThread();
        t.start();
    }
}
```

Method 2: Implementing Runnable interface

```
class MyTask implements Runnable {

    public void run() {
        System.out.println("Thread is running");
    }
}

class Main {
    public static void main(String[] args) {

        MyTask task = new MyTask();

        Thread t = new Thread(task);
        t.start();
    }
}
```

Important:

- `start()` creates a new execution thread and invokes `run()` on that thread.
- Calling `run()` directly does not create a new thread.

## 4. Difference between Thread class and Runnable interface?

| Thread                                       | Runnable                   |
| -------------------------------------------- | -------------------------- |
| It is a class                                | It is an interface         |
| We extend Thread                             | We implement Runnable      |
| Cannot extend another class at the same time | Can extend another class   |
| Task and thread are tightly coupled          | Separates task from thread |
| Less flexible                                | More flexible              |

Remember: Runnable is generally preferred because Java supports only single class inheritance.

## 5. What is Synchronization?

Synchronization is a mechanism used to control access to shared resources by multiple threads.

It prevents multiple threads from modifying shared data simultaneously in a way that causes data inconsistency.

Example:

```
class Counter {

    int count = 0;

    synchronized void increment() {
        count++;
    }
}
```

Here, `synchronized` allows only one thread at a time to execute this method on the same Counter object.

Without synchronization: Multiple threads may update shared data incorrectly.

With synchronization: Access to the synchronized method is controlled using the object's lock.

Remember: Synchronization = Controls access to shared resources between threads.

## 6. What is Deadlock?

Deadlock is a situation where two or more threads wait forever for resources locked by each other.

Example:

- Thread 1 locks Resource A and waits for Resource B.
- Thread 2 locks Resource B and waits for Resource A.
- Both threads keep waiting.

Deadlock example

Thread 1

Holds A

Waits for B

Thread 2

Holds B

Waits for A

Both threads are stuck

How to prevent deadlock?

- Acquire locks in a consistent order.
- Avoid unnecessary nested locks.
- Use timeouts with lock operations where appropriate.

Remember: Deadlock = Threads waiting for each other's locks forever.

## 7. What is the volatile keyword?

`volatile` is a keyword used in Java multithreading to ensure visibility of changes made by one thread to other threads.

When one thread updates a volatile variable, other threads can see the updated value.

Example:

```
class MyTask {

    volatile boolean running = true;

    void stop() {
        running = false;
    }
}
```

Here, if one thread changes `running` to false, another thread reading it will see the updated value.

Important:

- Provides visibility.
- Does not provide atomicity for compound operations.
- Does not replace synchronization in every situation.

Remember: Volatile = Visibility of shared variable changes.

## 8. Difference between sleep() and wait()?

| sleep()                                          | wait()                                            |
| ------------------------------------------------ | ------------------------------------------------- |
| Method of Thread class                           | Method of Object class                            |
| Used to pause a thread                           | Used for inter-thread communication               |
| Does not release the held locks                  | Releases the monitor lock on the object           |
| Can be called without owning an object's monitor | Must be called while owning that object's monitor |
| Wakes after the specified time or interruption   | Wakes after notification, interruption or timeout |

Example:

```
Thread.sleep(1000);
```

Pauses the current thread for approximately one second.

```
synchronized (obj) {
    obj.wait();
}
```

Makes the current thread wait and releases that object's monitor lock.

Remember:

- sleep() → Pauses execution.
- wait() → Waits for notification or another permitted wake-up condition and releases the object's monitor.

## 9. Difference between notify() and notifyAll()?

Both methods are used for inter-thread communication.

| notify()                                 | notifyAll()                                                                   |
| ---------------------------------------- | ----------------------------------------------------------------------------- |
| Wakes one waiting thread                 | Wakes all threads waiting on that object's monitor                            |
| JVM chooses which waiting thread to wake | All waiting threads become eligible to compete for the lock                   |
| Other waiting threads remain waiting     | Other threads may proceed after acquiring the lock and checking the condition |

Example:

```
synchronized (obj) {
    obj.notify();
}
```

```
synchronized (obj) {
    obj.notifyAll();
}
```

Remember:

- notify() → One waiting thread.
- notifyAll() → All waiting threads.

Both must be called while holding the object's monitor.

## 10. What is ExecutorService?

ExecutorService is a Java interface used to manage and execute multiple tasks using a thread pool.

Instead of manually creating a new thread for every task, we can submit tasks to ExecutorService.

Example:

```
import java.util.concurrent.*;

class Main {
    public static void main(String[] args) {

        ExecutorService executor =
            Executors.newFixedThreadPool(2);

        executor.submit(() -> {
            System.out.println("Task is running");
        });

        executor.shutdown();
    }
}
```

Advantages:

- Reuses threads.
- Reduces thread creation overhead.
- Manages task execution.
- Makes multithreading easier.

Remember: ExecutorService = Manages a pool of threads and executes tasks.

# Part 2: Exception Handling

## 1. What is Exception Handling?

Exception handling is a mechanism in Java used to handle runtime errors so that the program can continue or terminate gracefully.

It prevents unexpected program termination when an error occurs.

Example:

```
class Main {
    public static void main(String[] args) {

        try {
            int a = 10 / 0;
        }
        catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
    }
}
```

Output:

```
Cannot divide by zero
```

Remember: Exception handling = Handling errors without abnormal program termination.

## 2. Explain the Exception Hierarchy.

In Java, `Throwable` is the parent class of both `Exception` and `Error`.

Throwable

Exception

Checked

IOException, SQLException

Unchecked

RuntimeException, ArithmeticException, NullPointerException

Error

Serious problems

OutOfMemoryError, StackOverflowError

Explanation:

- Throwable → Parent class of exceptions and errors.
- Exception → Problems applications may handle.
- RuntimeException → Parent of unchecked exceptions.
- Error → Serious JVM or system-level problems, generally not handled by application code.

Remember: Throwable → Exception + Error.

## 3. Difference between Checked and Unchecked Exceptions?

| Checked Exception                                                      | Unchecked Exception                     |
| ---------------------------------------------------------------------- | --------------------------------------- |
| Checked at compile time                                                | Occurs at runtime                       |
| Must be handled or declared                                            | Handling or declaring is not compulsory |
| Subclasses of Exception, excluding RuntimeException and its subclasses | RuntimeException and its subclasses     |
| Example: IOException                                                   | Example: NullPointerException           |

Checked exception example:

```
import java.io.*;

class Main {
    public static void main(String[] args) {

        try {
            FileReader f = new FileReader("test.txt");
        }
        catch (IOException e) {
            System.out.println("File not found");
        }
    }
}
```

Unchecked exception example:

```
class Main {
    public static void main(String[] args) {

        int a = 10 / 0;
    }
}
```

This produces `ArithmeticException`.

Remember:

- Checked → Compiler forces handling or declaration.
- Unchecked → Compiler does not force handling.

## 4. What is try-catch-finally?

These are Java keywords used in exception handling.

- `try` → Contains code that may throw an exception.
- `catch` → Handles the exception.
- `finally` → Contains cleanup code that normally executes whether an exception occurs or not.

Example:

```
class Main {
    public static void main(String[] args) {

        try {
            int a = 10 / 0;
        }
        catch (ArithmeticException e) {
            System.out.println("Exception handled");
        }
        finally {
            System.out.println("Finally executed");
        }
    }
}
```

Output:

```
Exception handled
Finally executed
```

Remember:

- try → Risky code.
- catch → Handle exception.
- finally → Cleanup code.

## 5. Can we have multiple catch blocks?

Yes. We can use multiple catch blocks to handle different types of exceptions from a try block.

Example:

```
class Main {
    public static void main(String[] args) {

        try {
            int a = 10 / 0;
        }
        catch (ArithmeticException e) {
            System.out.println("Arithmetic Exception");
        }
        catch (NullPointerException e) {
            System.out.println("Null Pointer Exception");
        }
        catch (Exception e) {
            System.out.println("General Exception");
        }
    }
}
```

Output:

```
Arithmetic Exception
```

Important interview point:

Always write specific exception catch blocks before general exception catch blocks.

Otherwise, Java will show a compile-time error because the general catch block makes the specific one unreachable.

## 6. Can finally execute without catch?

Yes. A `finally` block can be used with a `try` block without a `catch` block.

Example:

```
class Main {
    public static void main(String[] args) {

        try {
            System.out.println("Try block");
        }
        finally {
            System.out.println("Finally block");
        }
    }
}
```

Output:

```
Try block
Finally block
```

Remember: A try block must be followed by at least one catch block or a finally block.

## 7. What is a Custom Exception?

A Custom Exception is a user-defined exception created by the programmer to handle application-specific errors.

We can create:

- Checked custom exceptions by extending `Exception`.
- Unchecked custom exceptions by extending `RuntimeException`.

Example:

```
class InvalidAgeException extends Exception {

    InvalidAgeException(String message) {
        super(message);
    }
}

class Main {
    public static void main(String[] args) {

        int age = 15;

        try {
            if (age < 18) {
                throw new InvalidAgeException(
                    "Age must be 18 or above"
                );
            }
        }
        catch (InvalidAgeException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

Output:

```
Age must be 18 or above
```

Remember: Custom Exception = Exception created by the programmer.

## 8. What happens when an exception occurs inside a finally block?

If an exception occurs inside a finally block, it can propagate to the caller and may replace an exception that was already being thrown from the try or catch block.

Example:

```
class Main {
    public static void main(String[] args) {

        try {
            int a = 10 / 0;
        }
        finally {
            int b = 10 / 0;
        }
    }
}
```

Here:

- The try block throws an ArithmeticException.
- The finally block also throws an ArithmeticException.
- The exception from finally takes precedence over the original exception during propagation.

Important: The original exception can be lost unless it is explicitly preserved or suppressed.

Remember: An exception inside finally can override an exception from try or catch.

# Quick Interview Revision

## Multithreading

| No. | Question            | Important point                       |
| --- | ------------------- | ------------------------------------- |
| 1   | Thread              | Unit of execution                     |
| 2   | Process vs Thread   | Independent process vs execution unit |
| 3   | Creating Thread     | Thread and Runnable                   |
| 4   | Thread vs Runnable  | Class vs Interface                    |
| 5   | Synchronization     | Controls shared resource access       |
| 6   | Deadlock            | Threads wait for each other's locks   |
| 7   | Volatile            | Visibility                            |
| 8   | Sleep vs Wait       | Pause vs release monitor and wait     |
| 9   | Notify vs NotifyAll | One vs all waiting threads            |
| 10  | ExecutorService     | Thread pool management                |

## Exception Handling

| No. | Question                 | Important point                  |
| --- | ------------------------ | -------------------------------- |
| 1   | Exception Handling       | Handles runtime problems         |
| 2   | Exception Hierarchy      | Throwable → Exception / Error    |
| 3   | Checked vs Unchecked     | Compile-time checking vs runtime |
| 4   | Try-Catch-Finally        | Handle and clean up              |
| 5   | Multiple Catch           | Yes                              |
| 6   | Finally without Catch    | Yes                              |
| 7   | Custom Exception         | User-defined exception           |
| 8   | Exception inside Finally | Can replace original exception   |

## Test yourself – Interview Practice

Try answering these five questions without looking at the notes.

Java interview mini-test

0/5 answered

1\. Which method actually starts a new thread?

run()

start()

execute()

sleep()

2\. Does volatile guarantee atomicity for count++?

Yes

No

3\. Which method releases the object's monitor lock?

sleep()

wait()

notify()

run()

4\. Which is an unchecked exception?

IOException

SQLException

NullPointerException

FileNotFoundException

5\. Can we use try with finally without catch?

Yes

No

Submit answers

My suggestion: Give extra attention to synchronization, deadlock, volatile, `wait()` vs `sleep()`, checked vs unchecked exceptions, and custom exceptions. These concepts are frequently used in practical Java and Spring Boot interview scenarios.

# Spring Framework & Spring Boot – 20 Important Interview Questions

These are very important for Java Developer, Java Full Stack Developer, and Spring Boot interviews.

I'll explain each question using:

- Simple English definitions.
- Practical examples.
- Important annotations.
- Short answers you can speak in an interview.

# Part 1: Spring Framework Fundamentals

## 1. What is Spring Framework?

Spring is a Java framework used to develop enterprise applications.

It makes Java application development easier by providing features such as:

- Dependency Injection (DI).
- Inversion of Control (IoC).
- Transaction Management.
- Spring MVC.
- Database Integration.
- Security Integration.

Example: Suppose we are developing an employee management application. Spring helps us manage employee services, repositories, database connections, and business logic.

Interview answer:

Spring Framework is an open-source Java framework used to develop enterprise applications. It provides features like Dependency Injection, Inversion of Control, transaction management, and web development support.

## 2. What is Spring Boot?

Spring Boot is built on top of the Spring Framework. It simplifies Spring application development by providing auto-configuration and starter dependencies.

Main features:

1. Auto-Configuration – Automatically configures components based on dependencies and application settings.
2. Starter Dependencies – Provides ready-made dependency groups.
3. Embedded Server – Supports servers like Tomcat.
4. Production-Ready Features – Provides monitoring and management through Actuator.

Example:

Without Spring Boot, we may need to configure many things manually.

With Spring Boot, we can create an application with minimal configuration.

```
@SpringBootApplication
public class MyApplication {

    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

Interview answer:

Spring Boot is a framework built on top of Spring that simplifies application development through auto-configuration, starter dependencies, and embedded servers.

## 3. Difference between Spring and Spring Boot?

| Spring Framework                                         | Spring Boot                               |
| -------------------------------------------------------- | ----------------------------------------- |
| Provides core application framework features             | Simplifies Spring application development |
| Requires more manual configuration in traditional setups | Provides auto-configuration               |
| Server configuration is often separate                   | Supports embedded servers                 |
| Dependency management requires more setup                | Provides starter dependencies             |
| More initial configuration                               | Minimal initial configuration             |

Remember:

- Spring → Core framework.
- Spring Boot → Makes Spring development easier and faster.

## 4. What is Dependency Injection (DI)?

Dependency Injection is a design technique in which an object receives its required dependencies from an external source instead of creating them itself.

Example without DI:

```
class Service {
    Repository repo = new Repository();
}
```

Here, Service creates its own Repository object.

Example with DI:

```
@Component
class Repository {
}

@Service
class Service {

    private final Repository repo;

    public Service(Repository repo) {
        this.repo = repo;
    }
}
```

Here, Spring provides the Repository object to the Service.

Advantages:

- Reduces tight coupling.
- Improves code reusability.
- Makes unit testing easier.
- Improves maintainability.

Remember: DI = Spring provides the required object instead of the class creating it manually.

## 5. What is Inversion of Control (IoC)?

Inversion of Control is a design principle in which control of object creation and management is transferred from the programmer to the Spring container.

Normally, we create objects using `new`.

With Spring, the Spring IoC container creates, manages, and provides objects called beans.

Example:

```
@Component
class Student {
}
```

Spring creates and manages the Student object as a bean.

Remember:

- IoC → Principle.
- DI → Technique used to implement IoC.

Interview answer: IoC means Spring takes control of creating and managing objects instead of the programmer managing everything manually.

## 6. What is the @Autowired annotation?

`@Autowired` is used to inject dependencies automatically by Spring.

Example:

```
@Component
class Engine {
}

@Component
class Car {

    @Autowired
    Engine engine;
}
```

Spring automatically injects the Engine bean into Car.

Constructor injection example:

```
@Component
class Car {

    private final Engine engine;

    @Autowired
    Car(Engine engine) {
        this.engine = engine;
    }
}
```

In modern Spring, a single constructor does not require `@Autowired`.

Types of dependency injection:

1. Constructor Injection.
2. Setter Injection.
3. Field Injection.

Interview tip: Constructor injection is generally preferred because it supports immutability and easier testing.

## 7. Difference between @Component, @Service, and @Repository?

All three annotations are used to register classes as Spring-managed beans.

| Annotation    | Purpose                     |
| ------------- | --------------------------- |
| `@Component`  | General-purpose Spring bean |
| `@Service`    | Business logic layer        |
| `@Repository` | Database access layer       |

Example:

```
@Component
class EmailUtil {
}
```

```
@Service
class EmployeeService {
}
```

```
@Repository
class EmployeeRepository {
}
```

Important: `@Repository` also supports translation of certain persistence exceptions into Spring's DataAccessException hierarchy.

Remember:

- Component → General class.
- Service → Business logic.
- Repository → Database operations.

## 8. What is @RestController?

`@RestController` is an annotation used to create REST APIs in Spring Boot.

It combines:

- `@Controller`
- `@ResponseBody`

It returns data directly, usually as JSON, instead of returning a view name.

Example:

```
@RestController
public class EmployeeController {

    @GetMapping("/employees")
    public String getEmployee() {
        return "Abirami";
    }
}
```

Response:

```
Abirami
```

For an object response, Spring Boot typically converts it into JSON.

## 9. Difference between @Controller and @RestController?

| @Controller                                       | @RestController                        |
| ------------------------------------------------- | -------------------------------------- |
| Used mainly for MVC web applications              | Used for REST APIs                     |
| Usually returns view names                        | Returns response data directly         |
| Requires `@ResponseBody` for direct response data | Includes `@ResponseBody` automatically |
| Can return HTML views                             | Commonly returns JSON/XML              |

Remember:

- Controller → View-based response by default.
- RestController → Data-based response by default.

## 10. What is @RequestMapping?

`@RequestMapping` is used to map HTTP requests to controller classes or methods.

It can define:

- URL path.
- HTTP method.
- Request parameters.
- Headers.
- Content types.

Example:

```
@RestController
@RequestMapping("/employees")
public class EmployeeController {

    @RequestMapping(value = "/all",
                    method = RequestMethod.GET)
    public String getEmployees() {
        return "Employee List";
    }
}
```

URL:

```
GET /employees/all
```

Remember: `@RequestMapping` maps HTTP requests to controller methods.

## 11. Difference between @GetMapping, @PostMapping, @PutMapping, and @DeleteMapping?

These annotations are used to map HTTP methods to controller methods.

| Annotation       | HTTP Method | Purpose                      |
| ---------------- | ----------- | ---------------------------- |
| `@GetMapping`    | GET         | Retrieve data                |
| `@PostMapping`   | POST        | Create new data              |
| `@PutMapping`    | PUT         | Update or replace a resource |
| `@DeleteMapping` | DELETE      | Delete data                  |

Example:

```
@RestController
@RequestMapping("/employees")
public class EmployeeController {

    @GetMapping
    public String getEmployee() {
        return "Get Employee";
    }

    @PostMapping
    public String addEmployee() {
        return "Employee Added";
    }

    @PutMapping("/{id}")
    public String updateEmployee(@PathVariable int id) {
        return "Employee Updated";
    }

    @DeleteMapping("/{id}")
    public String deleteEmployee(@PathVariable int id) {
        return "Employee Deleted";
    }
}
```

Real-world example:

Suppose we have an Employee Management System:

- GET → View employee details.
- POST → Add a new employee.
- PUT → Update employee details.
- DELETE → Remove an employee.

Remember: GET = Read, POST = Create, PUT = Update, DELETE = Remove.

## 12. What is Spring Data JPA?

Spring Data JPA is a part of the Spring Data project that simplifies database operations using JPA.

It reduces the amount of boilerplate code required to interact with databases.

Instead of writing SQL queries for every operation, we can use repository interfaces.

Example:

```
@Entity
class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```

Repository:

```
@Repository
public interface EmployeeRepository
        extends JpaRepository<Employee, Long> {
}
```

Now we can use built-in methods:

```
employeeRepository.save(employee);

employeeRepository.findById(1L);

employeeRepository.findAll();

employeeRepository.deleteById(1L);
```

Advantages:

- Reduces boilerplate code.
- Provides ready-made CRUD operations.
- Supports pagination and sorting.
- Supports custom query methods.

Remember: Spring Data JPA simplifies database operations using repository interfaces.

## 13. Difference between Hibernate and JPA?

| JPA                                        | Hibernate                      |
| ------------------------------------------ | ------------------------------ |
| Specification                              | ORM framework                  |
| Defines standards for ORM                  | Provides implementation of JPA |
| Cannot work as an implementation by itself | Can work as a JPA provider     |
| Defines annotations and interfaces         | Implements JPA features        |

Example:

JPA annotations:

```
@Entity
@Table(name = "employee")
class Employee {

    @Id
    private Long id;
}
```

Hibernate is commonly used behind the scenes to implement these JPA operations.

Remember:

- JPA → What should be implemented (specification).
- Hibernate → How it is implemented (implementation).

## 14. What is @Entity?

`@Entity` is a JPA annotation used to mark a Java class as an entity that can be mapped to a database table.

Example:

```
@Entity
@Table(name = "employees")
public class Employee {

    @Id
    private Long id;

    private String name;

    private double salary;
}
```

Here:

- Employee is an entity.
- It is mapped to the employees table.
- Its fields are mapped to database columns by default.

Remember: `@Entity` tells JPA that a Java class represents a database entity.

## 15. What is @Id?

`@Id` is a JPA annotation used to identify the primary key of an entity.

A primary key uniquely identifies each record in a database table.

Example:

```
@Entity
class Employee {

    @Id
    private Long id;

    private String name;
}
```

Here, `id` is the primary key.

Remember: `@Id` identifies the primary key.

## 16. What is @GeneratedValue?

`@GeneratedValue` is a JPA annotation used to automatically generate primary key values.

It is generally used along with `@Id`.

Example:

```
@Entity
class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```

Important generation strategies:

| Strategy | Purpose                                                  |
| -------- | -------------------------------------------------------- |
| IDENTITY | Database generates the ID, commonly using auto-increment |
| SEQUENCE | Uses a database sequence                                 |
| TABLE    | Uses a database table to generate IDs                    |
| AUTO     | Provider chooses a suitable strategy                     |

Remember: `@GeneratedValue` automatically generates primary key values.

## 17. What is @Transactional?

`@Transactional` is a Spring annotation used to manage database transactions.

It ensures that a group of database operations is treated as one logical unit of work.

Example:

```
@Service
public class EmployeeService {

    @Autowired
    EmployeeRepository repository;

    @Transactional
    public void saveEmployee() {

        Employee e1 = new Employee();
        e1.setName("Abirami");

        repository.save(e1);

        // If an unchecked exception occurs here,
        // the transaction normally rolls back.
    }
}
```

Important concepts:

- Commit → Permanently saves transaction changes.
- Rollback → Reverses transaction changes.
- By default, Spring rolls back for unchecked exceptions (`RuntimeException` and `Error`).
- Checked exceptions do not trigger rollback by default.

We can configure rollback for checked exceptions:

```
@Transactional(rollbackFor = Exception.class)
```

Remember: `@Transactional` manages transaction boundaries and helps maintain database consistency.

## 18. What is application.properties?

`application.properties` is a configuration file used in Spring Boot applications.

It stores application settings such as:

- Database configuration.
- Server port.
- Database username and password.
- Hibernate configuration.
- Logging configuration.

Example:

```
server.port=8081

spring.datasource.url=jdbc:mysql://localhost:3306/company

spring.datasource.username=root

spring.datasource.password=root

spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true
```

Explanation:

| Property                        | Purpose                    |
| ------------------------------- | -------------------------- |
| `server.port`                   | Changes application port   |
| `spring.datasource.url`         | Database connection URL    |
| `spring.datasource.username`    | Database username          |
| `spring.datasource.password`    | Database password          |
| `spring.jpa.hibernate.ddl-auto` | Controls schema generation |
| `spring.jpa.show-sql`           | Displays SQL queries       |

Remember: `application.properties` stores Spring Boot application configuration.

## 19. What is REST API?

REST stands for Representational State Transfer.

A REST API allows two applications to communicate over HTTP using resources and standard HTTP methods.

For example, a frontend application communicates with a Spring Boot backend to retrieve employee information.

Example:

Suppose we have an Employee Management System.

| HTTP Method | Endpoint       | Operation          |
| ----------- | -------------- | ------------------ |
| GET         | `/employees`   | Get all employees  |
| GET         | `/employees/1` | Get employee by ID |
| POST        | `/employees`   | Create employee    |
| PUT         | `/employees/1` | Update employee    |
| DELETE      | `/employees/1` | Delete employee    |

Example JSON response:

```
{
    "id": 1,
    "name": "Abirami",
    "salary": 30000
}
```

Important REST principles:

1. Client-server architecture.
2. Stateless communication.
3. Resource-based URLs.
4. Standard HTTP methods.
5. Representations such as JSON.

Remember: REST API allows applications to communicate using HTTP methods and resource-based endpoints.

## 20. What are HTTP Status Codes?

HTTP status codes are three-digit numbers returned by the server to indicate the result of an HTTP request.

They are divided into five categories.

| Category | Meaning       |
| -------- | ------------- |
| 1xx      | Informational |
| 2xx      | Success       |
| 3xx      | Redirection   |
| 4xx      | Client Error  |
| 5xx      | Server Error  |

Important status codes for interviews:

| Status Code | Meaning               | Example                                    |
| ----------- | --------------------- | ------------------------------------------ |
| 200         | OK                    | Successfully retrieved data                |
| 201         | Created               | Employee created                           |
| 204         | No Content            | Successfully deleted with no response body |
| 400         | Bad Request           | Invalid request data                       |
| 401         | Unauthorized          | Authentication required or failed          |
| 403         | Forbidden             | User doesn't have permission               |
| 404         | Not Found             | Employee doesn't exist                     |
| 405         | Method Not Allowed    | Unsupported HTTP method                    |
| 409         | Conflict              | Duplicate or conflicting resource          |
| 500         | Internal Server Error | Unexpected server error                    |
| 503         | Service Unavailable   | Server temporarily unavailable             |

Remember:

- 2xx → Success.
- 3xx → Redirection.
- 4xx → Client mistake.
- 5xx → Server problem.

# Quick Revision – All 20 Spring Boot Questions

| No. | Question                           | Important point                   |
| --- | ---------------------------------- | --------------------------------- |
| 1   | Spring Framework                   | Java enterprise framework         |
| 2   | Spring Boot                        | Simplifies Spring development     |
| 3   | Spring vs Spring Boot              | Framework vs simplified setup     |
| 4   | Dependency Injection               | Dependencies provided externally  |
| 5   | IoC                                | Spring controls object management |
| 6   | @Autowired                         | Injects dependencies              |
| 7   | Component vs Service vs Repository | General vs business vs database   |
| 8   | @RestController                    | Creates REST APIs                 |
| 9   | Controller vs RestController       | View vs response data             |
| 10  | @RequestMapping                    | Maps HTTP requests                |
| 11  | Get/Post/Put/Delete                | Read/Create/Update/Delete         |
| 12  | Spring Data JPA                    | Simplifies database operations    |
| 13  | Hibernate vs JPA                   | Implementation vs specification   |
| 14  | @Entity                            | Maps class to database entity     |
| 15  | @Id                                | Primary key                       |
| 16  | @GeneratedValue                    | Generates primary key             |
| 17  | @Transactional                     | Manages database transactions     |
| 18  | application.properties             | Application configuration         |
| 19  | REST API                           | Communication using HTTP          |
| 20  | HTTP Status Codes                  | Request response status           |

## Important practical concepts to prepare

For a Java Developer interview, don't stop with definitions. Practise these scenarios too:

1. How does Spring create and manage beans?
2. What happens if two beans of the same type exist?
3. Why is constructor injection preferred?
4. What happens if `@Autowired` cannot find a matching bean?
5. How does a request travel from Controller → Service → Repository → Database?
6. What happens when an exception occurs inside a `@Transactional` method?
7. Difference between `save()` and `saveAndFlush()`.
8. Difference between `CrudRepository` and `JpaRepository`.

My suggestion: Give special attention to Dependency Injection, IoC, REST APIs, Spring Data JPA, and `@Transactional`. These concepts are particularly important for practical Spring Boot interviews.
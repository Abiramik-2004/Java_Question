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
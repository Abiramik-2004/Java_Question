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

My interview preparation suggestion: First understand questions 2, 3, 4, 5, 9, 12 and 14 deeply. These are especially useful for Core Java interviews.
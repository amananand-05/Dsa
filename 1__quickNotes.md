Absolutely! Here’s a comprehensive overview of essential Java collections, focusing on key methods (15-20 for each collection), time complexity, examples, common use cases, iteration methods, and best practices.

---

### **1. ArrayList**

#### **Key Methods:**
1. **`add(E e)`**  
   Appends the specified element to the end of the list.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   ArrayList<String> list = new ArrayList<>();
   list.add("Hello");
   ```

2. **`add(int index, E element)`**  
   Inserts the specified element at the specified position in the list.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.add(1, "World");
   ```

3. **`get(int index)`**  
   Returns the element at the specified position in the list.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   String value = list.get(0); // "Hello"
   ```

4. **`set(int index, E element)`**  
   Replaces the element at the specified position in the list with the specified element.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   list.set(0, "Hi");
   ```

5. **`remove(int index)`**  
   Removes the element at the specified position in the list.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.remove(1); // Removes "World"
   ```

6. **`remove(Object o)`**  
   Removes the first occurrence of the specified element from the list, if present.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.remove("Hello");
   ```

7. **`contains(Object o)`**  
   Returns `true` if the list contains the specified element.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   boolean hasElement = list.contains("Hi");
   ```

8. **`size()`**  
   Returns the number of elements in the list.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   int size = list.size();
   ```

9. **`isEmpty()`**  
   Returns `true` if the list contains no elements.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   boolean isEmpty = list.isEmpty();
   ```

10. **`clear()`**  
    Removes all elements from the list.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    list.clear();
    ```

11. **`indexOf(Object o)`**  
    Returns the index of the first occurrence of the specified element in the list, or -1 if the list does not contain the element.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    int index = list.indexOf("Hi");
    ```

12. **`lastIndexOf(Object o)`**  
    Returns the index of the last occurrence of the specified element in the list, or -1 if the list does not contain the element.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    int lastIndex = list.lastIndexOf("Hi");
    ```

13. **`toArray()`**  
    Returns an array containing all of the elements in the list in proper sequence.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    Object[] array = list.toArray();
    ```

14. **`subList(int fromIndex, int toIndex)`**  
    Returns a view of the portion of this list between the specified fromIndex, inclusive, and toIndex, exclusive.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    List<String> sublist = list.subList(0, 2);
    ```

15. **`retainAll(Collection<?> c)`**  
    Retains only the elements in this list that are contained in the specified collection.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    List<String> toRetain = Arrays.asList("Hi", "World");
    list.retainAll(toRetain);
    ```

16. **`sort(Comparator<? super E> c)`**  
    Sorts this list according to the order induced by the specified comparator.  
    **Time Complexity**: O(n log n)  
    **Example**:
    ```java
    Collections.sort(list);
    ```

17. **`forEach(Consumer<? super E> action)`**  
    Performs the given action for each element of the list until all elements have been processed.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    list.forEach(System.out::println);
    ```

---

#### **Common Use Cases:**
- Storing a dynamic list of elements where frequent access and iteration are required.
- Maintaining a list of tasks, managing collections of objects, or building stacks and queues.

---

#### **Iteration Methods:**
1. **Using Enhanced For-Loop**:
   ```java
   for (String element : list) {
       System.out.println(element);
   }
   ```

2. **Using Iterator**:
   ```java
   Iterator<String> iterator = list.iterator();
   while (iterator.hasNext()) {
       System.out.println(iterator.next());
   }
   ```

3. **Using Streams (Java 8 and above)**:
   ```java
   list.stream().forEach(System.out::println);
   ```

---

#### **Best Practices:**
- **Initial Capacity**: Specify an initial capacity when creating an `ArrayList` to minimize resizing overhead.
- **Avoid Frequent Random Inserts**: Prefer using `add` only at the end or use `LinkedList` for frequent insertions.
- **Use `Arrays.asList()`**: Create a fixed-size list quickly with `Arrays.asList()` when the size is known upfront.

---

### **2. HashMap**

#### **Key Methods:**
1. **`put(K key, V value)`**  
   Associates the specified value with the specified key in the map.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   HashMap<String, Integer> map = new HashMap<>();
   map.put("Alice", 30);
   ```

2. **`get(Object key)`**  
   Returns the value to which the specified key is mapped, or `null` if the map contains no mapping for the key.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   Integer age = map.get("Alice"); // 30
   ```

3. **`remove(Object key)`**  
   Removes the mapping for the specified key from the map if present.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   map.remove("Alice");
   ```

4. **`containsKey(Object key)`**  
   Returns `true` if the map contains a mapping for the specified key.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   boolean exists = map.containsKey("Alice");
   ```

5. **`containsValue(Object value)`**  
   Returns `true` if the map maps one or more keys to the specified value.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   boolean hasValue = map.containsValue(30);
   ```

6. **`size()`**  
   Returns the number of key-value mappings in the map.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   int size = map.size();
   ```

7. **`isEmpty()`**  
   Returns `true` if the map contains no key-value mappings.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   boolean isEmpty = map.isEmpty();
   ```

8. **`clear()`**  
   Removes all mappings from the map.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   map.clear();
   ```

9. **`keySet()`**  
   Returns a `Set` view of the keys contained in the map.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   Set<String> keys = map.keySet();
   ```

10. **`values()`**  
    Returns a `Collection` view of the values contained in the map.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    Collection<Integer> values = map.values();
    ```

11. **`entrySet()`**  
    Returns a `Set` view of the mappings contained in the map.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    Set<Map.Entry<String, Integer>> entries = map.entrySet();


12. **`putIfAbsent(K key, V value)`**  
    Associates the specified value with the specified key only if the key is not already associated with a value.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    map.putIfAbsent("Bob", 25);
    ```

13. **`replace(K key, V value)`**  
    Replaces the entry for a key only if currently mapped to some value.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    map.replace("Bob", 26);
    ```

14. **`replace(K key, V oldValue, V newValue)`**  
    Replaces the entry for a key only if currently mapped to the specified value.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    map.replace("Bob", 25, 26);
    ```

15. **`forEach(BiConsumer<? super K, ? super V> action)`**  
    Performs the given action for each entry in the map until all entries have been processed.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    map.forEach((key, value) -> System.out.println(key + ": " + value));
    ```

16. **`computeIfAbsent(K key, Function<? super K, ? extends V> mappingFunction)`**  
    Computes a value for the key if absent.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    map.computeIfAbsent("Alice", k -> 35);
    ```

17. **`computeIfPresent(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction)`**  
    Computes a new value for the key if present.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    map.computeIfPresent("Bob", (k, v) -> v + 1);
    ```

18. **`merge(K key, V value, BiFunction<? super V, ? super V, ? extends V> remappingFunction)`**  
    Merges the specified value with the current value.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    map.merge("Alice", 5, Integer::sum);
    ```

19. **`getOrDefault(Object key, V defaultValue)`**  
    Returns the value to which the specified key is mapped, or `defaultValue` if this map contains no mapping for the key.  
    **Time Complexity**: O(1) (amortized)  
    **Example**:
    ```java
    int age = map.getOrDefault("Charlie", 0); // 0 if not found
    ```

---

#### **Common Use Cases:**
- Storing key-value pairs for fast retrieval, such as caching, frequency counting, and lookups.

---

#### **Iteration Methods:**
1. **Using Enhanced For-Loop**:
   ```java
   for (Map.Entry<String, Integer> entry : map.entrySet()) {
       System.out.println(entry.getKey() + ": " + entry.getValue());
   }
   ```

2. **Using Iterator**:
   ```java
   Iterator<Map.Entry<String, Integer>> iterator = map.entrySet().iterator();
   while (iterator.hasNext()) {
       Map.Entry<String, Integer> entry = iterator.next();
       System.out.println(entry.getKey() + ": " + entry.getValue());
   }
   ```

3. **Using Streams (Java 8 and above)**:
   ```java
   map.forEach((key, value) -> System.out.println(key + ": " + value));
   ```

---

#### **Best Practices:**
- **Initial Capacity**: Specify an initial capacity and load factor to minimize rehashing.
- **Avoid Null Keys**: Only one null key is allowed; consider using a wrapper class if necessary.
- **Use Immutable Keys**: Prefer immutable objects as keys to prevent accidental modification.

---

### **3. HashSet**

#### **Key Methods:**
1. **`add(E e)`**  
   Adds the specified element to the set if it is not already present.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   HashSet<String> set = new HashSet<>();
   set.add("Apple");
   ```

2. **`remove(Object o)`**  
   Removes the specified element from the set if it is present.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   set.remove("Apple");
   ```

3. **`contains(Object o)`**  
   Returns `true` if the set contains the specified element.  
   **Time Complexity**: O(1) (amortized)  
   **Example**:
   ```java
   boolean exists = set.contains("Apple"); // true or false
   ```

4. **`size()`**  
   Returns the number of elements in the set.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   int size = set.size(); // Number of elements in the set
   ```

5. **`isEmpty()`**  
   Returns `true` if the set contains no elements.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   boolean isEmpty = set.isEmpty(); // true or false
   ```

6. **`clear()`**  
   Removes all elements from the set.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   set.clear(); // Set will be empty
   ```

7. **`addAll(Collection<? extends E> c)`**  
   Adds all of the elements in the specified collection to the set.  
   **Time Complexity**: O(m) where m is the number of elements added.  
   **Example**:
   ```java
   HashSet<String> anotherSet = new HashSet<>();
   anotherSet.add("Banana");
   set.addAll(anotherSet);
   ```

8. **`removeAll(Collection<?> c)`**  
   Removes all of the elements in this set that are also contained in the specified collection.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   HashSet<String> toRemove = new HashSet<>();
   toRemove.add("Banana");
   set.removeAll(toRemove);
   ```

9. **`retainAll(Collection<?> c)`**  
   Retains only the elements in this set that are contained in the specified collection.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   HashSet<String> toRetain = new HashSet<>();
   toRetain.add("Apple");
   set.retainAll(toRetain);
   ```

10. **`containsAll(Collection<?> c)`**  
    Returns `true` if this set contains all of the elements in the specified collection.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    boolean allContain = set.containsAll(toRetain);
    ```

11. **`forEach(Consumer<? super E> action)`**  
    Performs the given action for each element of the set until all elements have been processed.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    set.forEach(System.out::println);
    ```

12. **`toArray()`**  
    Returns an array containing all of the elements in the set.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    Object[] array = set.toArray();
    ```

13. **`toArray(T[] a)`**  
    Returns an array containing all of the elements in the set; the runtime type of the returned array is that of the specified array.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    String[] array = set.toArray(new String[0]);
    ```

14. **`clone()`**  
    Returns a shallow copy of this `HashSet` instance.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    HashSet<String> clonedSet = (HashSet<String>) set.clone();
    ```

15. **`spliterator()`**  
    Creates a `Spliterator` over the elements in this set.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    Spliterator<String> spliterator = set.spliterator();
    ```

---

#### **Common Use Cases:**
- Storing unique elements without duplicates, such as managing a collection of user IDs, tags, or any unique identifiers.

---

#### **Iteration Methods:**
1. **Using Enhanced For-Loop**:
   ```java
   for (String element : set) {
       System.out.println(element);
   }
   ```

2. **Using Iterator**:
   ```java
   Iterator<String> iterator = set.iterator();
   while (iterator.hasNext()) {
       System.out.println(iterator.next());
   }
   ```



3. **Using Streams (Java 8 and above)**:
   ```java
   set.forEach(System.out::println);
   ```

---

#### **Best Practices:**
- **Initial Capacity**: Set an initial capacity to optimize memory usage.
- **Immutable Elements**: Use immutable objects to ensure consistent state.
- **Check for Duplicates**: Use `contains()` to check for duplicates before adding.

---

### **4. LinkedList**

#### **Key Methods:**
1. **`add(E e)`**  
   Appends the specified element to the end of the list.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   LinkedList<String> list = new LinkedList<>();
   list.add("Apple");
   ```

2. **`add(int index, E element)`**  
   Inserts the specified element at the specified position in the list.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.add(0, "Banana");
   ```

3. **`addFirst(E e)`**  
   Inserts the specified element at the beginning of the list.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   list.addFirst("Cherry");
   ```

4. **`addLast(E e)`**  
   Appends the specified element to the end of the list.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   list.addLast("Date");
   ```

5. **`remove(int index)`**  
   Removes the element at the specified position in the list.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.remove(1); // Removes the element at index 1
   ```

6. **`remove(Object o)`**  
   Removes the first occurrence of the specified element from the list, if it is present.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.remove("Apple");
   ```

7. **`get(int index)`**  
   Returns the element at the specified position in the list.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   String element = list.get(0); // First element
   ```

8. **`set(int index, E element)`**  
   Replaces the element at the specified position in the list with the specified element.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   list.set(0, "Grape");
   ```

9. **`size()`**  
   Returns the number of elements in the list.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   int size = list.size();
   ```

10. **`isEmpty()`**  
    Returns `true` if this list contains no elements.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    boolean isEmpty = list.isEmpty(); // true or false
    ```

11. **`clear()`**  
    Removes all elements from the list.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    list.clear();
    ```

12. **`forEach(Consumer<? super E> action)`**  
    Performs the given action for each element of the list until all elements have been processed.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    list.forEach(System.out::println);
    ```

13. **`toArray()`**  
    Returns an array containing all of the elements in the list in proper sequence.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    Object[] array = list.toArray();
    ```

14. **`toArray(T[] a)`**  
    Returns an array containing all of the elements in the list; the runtime type of the returned array is that of the specified array.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    String[] array = list.toArray(new String[0]);
    ```

15. **`clone()`**  
    Returns a shallow copy of this `LinkedList` instance.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    LinkedList<String> clonedList = (LinkedList<String>) list.clone();
    ```

16. **`peek()`**  
    Retrieves, but does not remove, the head (first element) of the list, or returns `null` if this list is empty.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    String first = list.peek();
    ```

17. **`poll()`**  
    Retrieves and removes the head (first element) of the list, or returns `null` if this list is empty.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    String first = list.poll();
    ```

18. **`offer(E e)`**  
    Adds the specified element as the tail (last element) of the list.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    list.offer("Fig");
    ```

19. **`descendingIterator()`**  
    Returns an iterator over the elements in this list in reverse order.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    Iterator<String> descendingIterator = list.descendingIterator();
    ```

20. **`spliterator()`**  
    Creates a `Spliterator` over the elements in this list.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    Spliterator<String> spliterator = list.spliterator();
    ```

---

#### **Common Use Cases:**
- Storing elements in a sequential order with frequent insertions and deletions, such as in queues and stacks.

---

#### **Iteration Methods:**
1. **Using Enhanced For-Loop**:
   ```java
   for (String element : list) {
       System.out.println(element);
   }
   ```

2. **Using Iterator**:
   ```java
   Iterator<String> iterator = list.iterator();
   while (iterator.hasNext()) {
       System.out.println(iterator.next());
   }
   ```

3. **Using Streams (Java 8 and above)**:
   ```java
   list.forEach(System.out::println);
   ```

---

#### **Best Practices:**
- **Use for Queues**: Prefer `LinkedList` for queue implementations due to efficient insertions and deletions.
- **Avoid Random Access**: Avoid accessing elements by index for better performance.
- **Use Immutable Objects**: Use immutable objects to prevent accidental modification.

---

### **5. TreeSet**

#### **Key Methods:**
1. **`add(E e)`**  
   Adds the specified element to the set if it is not already present.  
   **Time Complexity**: O(log n)  
   **Example**:
   ```java
   TreeSet<String> set = new TreeSet<>();
   set.add("Apple");
   ```

2. **`remove(Object o)`**  
   Removes the specified element from the set if it is present.  
   **Time Complexity**: O(log n)  
   **Example**:
   ```java
   set.remove("Apple");
   ```

3. **`contains(Object o)`**  
   Returns `true` if the set contains the specified element.  
   **Time Complexity**: O(log n)  
   **Example**:
   ```java
   boolean exists = set.contains("Apple");
   ```

4. **`size()`**  
   Returns the number of elements in the set.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   int size = set.size();
   ```

5. **`isEmpty()`**  
   Returns `true` if this set contains no elements.  
   **Time Complexity**: O(1)  
   **Example**:
   ```java
   boolean isEmpty = set.isEmpty(); // true or false
   ```

6. **`clear()`**  
   Removes all elements from the set.  
   **Time Complexity**: O(n)  
   **Example**:
   ```java
   set.clear(); // Set will be empty
   ```

7. **`first()`**  
   Returns the first (lowest) element currently in this set.  
   **Time Complexity**: O(log n)  
   **Example**:
   ```java
   String firstElement = set.first();
   ```

8. **`last()`**  
   Returns the last (highest) element currently in this set.  
   **Time Complexity**: O(log n)  
   **Example**:
   ```java
   String lastElement = set.last();
   ```

9. **`ceiling(E e)`**  
   Returns the least element in this set greater than or equal to the given element, or `null` if there is no such element.  
   **Time Complexity**: O(log n)  
   **Example**:
   ```java
   String ceiling = set.ceiling("Banana");
   ```

10. **`

floor(E e)`**  
Returns the greatest element in this set less than or equal to the given element, or `null` if there is no such element.  
**Time Complexity**: O(log n)  
**Example**:
```java
String floor = set.floor("Banana");
```

11. **`higher(E e)`**  
    Returns the least element in this set strictly greater than the given element, or `null` if there is no such element.  
    **Time Complexity**: O(log n)  
    **Example**:
    ```java
    String higher = set.higher("Banana");
    ```

12. **`lower(E e)`**  
    Returns the greatest element in this set strictly less than the given element, or `null` if there is no such element.  
    **Time Complexity**: O(log n)  
    **Example**:
    ```java
    String lower = set.lower("Banana");
    ```

13. **`iterator()`**  
    Returns an iterator over the elements in this set.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    Iterator<String> iterator = set.iterator();
    ```

14. **`forEach(Consumer<? super E> action)`**  
    Performs the given action for each element of the set until all elements have been processed.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    set.forEach(System.out::println);
    ```

15. **`toArray()`**  
    Returns an array containing all of the elements in the set in proper sequence.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    Object[] array = set.toArray();
    ```

16. **`toArray(T[] a)`**  
    Returns an array containing all of the elements in the set; the runtime type of the returned array is that of the specified array.  
    **Time Complexity**: O(n)  
    **Example**:
    ```java
    String[] array = set.toArray(new String[0]);
    ```

17. **`spliterator()`**  
    Creates a `Spliterator` over the elements in this set.  
    **Time Complexity**: O(1)  
    **Example**:
    ```java
    Spliterator<String> spliterator = set.spliterator();
    ```

---

#### **Common Use Cases:**
- Storing unique elements in a sorted order, such as when maintaining a leaderboard or a collection of unique tags.

---

#### **Iteration Methods:**
1. **Using Enhanced For-Loop**:
   ```java
   for (String element : set) {
       System.out.println(element);
   }
   ```

2. **Using Iterator**:
   ```java
   Iterator<String> iterator = set.iterator();
   while (iterator.hasNext()) {
       System.out.println(iterator.next());
   }
   ```

3. **Using Streams (Java 8 and above)**:
   ```java
   set.forEach(System.out::println);
   ```

---

#### **Best Practices:**
- **Use for Sorted Data**: Use `TreeSet` for sorted data requirements.
- **Avoid Null Elements**: `TreeSet` does not permit null elements.
- **Custom Comparators**: Use custom comparators for defining order when necessary.

---

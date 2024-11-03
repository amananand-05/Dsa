# 1. HashMap

Here’s a concise cheat sheet for all the key functions of `HashMap` in Java, along with iteration methods, designed for quick memorization:

### **HashMap Methods Cheat Sheet**

1. **`put(K key, V value)`**  
   Adds or updates a key-value pair in the map.  
   Example: `map.put(1, "One");`

2. **`get(Object key)`**  
   Retrieves the value associated with the specified key.  
   Example: `map.get(1);`

3. **`remove(Object key)`**  
   Removes the key-value pair for the specified key.  
   Example: `map.remove(1);`

4. **`containsKey(Object key)`**  
   Checks if the map contains the specified key.  
   Example: `map.containsKey(1);`

5. **`containsValue(Object value)`**  
   Checks if the map contains the specified value.  
   Example: `map.containsValue("One");`

6. **`isEmpty()`**  
   Returns `true` if the map is empty.  
   Example: `map.isEmpty();`

7. **`size()`**  
   Returns the number of key-value pairs in the map.  
   Example: `map.size();`

8. **`clear()`**  
   Removes all key-value pairs from the map.  
   Example: `map.clear();`

9. **`replace(K key, V newValue)`**  
   Replaces the value for the specified key if it exists.  
   Example: `map.replace(1, "Uno");`

10. **`getOrDefault(Object key, V defaultValue)`**  
    Returns the value for the key, or a default value if the key does not exist.  
    Example: `map.getOrDefault(2, "Default");`

11. **`putIfAbsent(K key, V value)`**  
    Adds the key-value pair only if the key is not already present.  
    Example: `map.putIfAbsent(3, "Three");`

12. **`merge(K key, V value, BiFunction)`**  
    Merges a new value with the existing one for a given key, or inserts it if absent.  
    Example: `map.merge(1, "New", (oldVal, newVal) -> oldVal + " & " + newVal);`

13. **`replaceAll(BiFunction)`**  
    Replaces each value by applying a given function to each entry.  
    Example: `map.replaceAll((k, v) -> v.toUpperCase());`

---

### **Iterating over a HashMap**

1. **Iterating over keys**:
   ```java
   for (Integer key : map.keySet()) {
       System.out.println(key);
   }
   ```

2. **Iterating over values**:
   ```java
   for (String value : map.values()) {
       System.out.println(value);
   }
   ```

3. **Iterating over key-value pairs (entries)**:
   ```java
   for (Map.Entry<Integer, String> entry : map.entrySet()) {
       System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
   }
   ```

---

### **Quick Notes for Memorization:**

- **Insert/Update**: `put(K, V)`
- **Retrieve**: `get(Object)`
- **Remove**: `remove(Object)`
- **Contains Key/Value**: `containsKey()`, `containsValue()`
- **Empty/Size**: `isEmpty()`, `size()`
- **Replace**: `replace()`, `replaceAll()`
- **Default value if absent**: `getOrDefault()`
- **Conditional put**: `putIfAbsent()`
- **Merge values**: `merge()`
- **Clear map**: `clear()`

---

# 2. HashSet

Here's a concise cheat sheet for the key functions of `HashSet` in Java, along with iteration methods, designed for quick memorization:

### **HashSet Methods Cheat Sheet**

1. **`add(E e)`**  
   Adds the specified element to the set.  
   Example: `set.add("Element");`

2. **`remove(Object o)`**  
   Removes the specified element from the set.  
   Example: `set.remove("Element");`

3. **`contains(Object o)`**  
   Checks if the set contains the specified element.  
   Example: `set.contains("Element");`

4. **`isEmpty()`**  
   Returns `true` if the set is empty.  
   Example: `set.isEmpty();`

5. **`size()`**  
   Returns the number of elements in the set.  
   Example: `set.size();`

6. **`clear()`**  
   Removes all elements from the set.  
   Example: `set.clear();`

7. **`addAll(Collection<? extends E> c)`**  
   Adds all elements from the specified collection to the set.  
   Example: `set.addAll(anotherSet);`

8. **`retainAll(Collection<?> c)`**  
   Retains only the elements in the set that are contained in the specified collection.  
   Example: `set.retainAll(anotherSet);`

9. **`removeAll(Collection<?> c)`**  
   Removes all elements in the set that are also contained in the specified collection.  
   Example: `set.removeAll(anotherSet);`

10. **`toArray()`**  
    Returns an array containing all elements in the set.  
    Example: `Object[] array = set.toArray();`

---

### **Iterating over a HashSet**

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
   set.stream().forEach(System.out::println);
   ```

---

### **Quick Notes for Memorization:**

- **Insert**: `add(E)`
- **Remove**: `remove(Object)`
- **Contains**: `contains(Object)`
- **Empty/Size**: `isEmpty()`, `size()`
- **Clear**: `clear()`
- **Bulk Operations**: `addAll(Collection)`, `removeAll(Collection)`, `retainAll(Collection)`
- **Convert to Array**: `toArray()`

---

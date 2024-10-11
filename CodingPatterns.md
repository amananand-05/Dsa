# Coding patterns in DSA

---
### 1. **Sliding Window**
- **Description**: Involves maintaining a window that either grows or shrinks to solve problems involving subarrays or substrings.
- **Use Cases**: Maximum or minimum subarray sum, longest substring with specific properties.
- **Example Problems**:
    - Longest Substring Without Repeating Characters (LeetCode #3)
    - Maximum Sum Subarray of Size K

### 2. **Two Pointers**
- **Description**: Uses two pointers that move towards each other or in the same direction to process data more efficiently, often with sorted arrays or strings.
- **Use Cases**: Finding pairs in an array, solving palindrome problems, removing duplicates.
- **Example Problems**:
    - Two Sum (Sorted Array, LeetCode #167)
    - Container With Most Water (LeetCode #11)

### 3. **Fast and Slow Pointers (Tortoise and Hare)**
- **Description**: Involves using two pointers moving at different speeds to detect cycles in linked lists or arrays.
- **Use Cases**: Cycle detection, middle of a linked list.
- **Example Problems**:
    - Linked List Cycle (LeetCode #141)
    - Find the Duplicate Number (LeetCode #287)

### 4. **Merge Intervals**
- **Description**: Used when dealing with overlapping intervals and merging them.
- **Use Cases**: Scheduling problems, interval merging, finding gaps.
- **Example Problems**:
    - Merge Intervals (LeetCode #56)
    - Insert Interval (LeetCode #57)

### 5. **Cyclic Sort**
- **Description**: Sorting problems where numbers are within a known range (e.g., 1 to n).
- **Use Cases**: Finding missing or duplicate numbers in a range.
- **Example Problems**:
    - Find All Duplicates in an Array (LeetCode #442)
    - Find the Missing Number (LeetCode #268)

### 6. **In-place Reversal of a Linked List**
- **Description**: Reversing parts of a linked list in place.
- **Use Cases**: Reversing a sub-list, k-group reversal, palindrome checks.
- **Example Problems**:
    - Reverse Linked List (LeetCode #206)
    - Reverse Nodes in k-Group (LeetCode #25)

### 7. **Topological Sort (Graph)**
- **Description**: Sorting nodes in a Directed Acyclic Graph (DAG) based on dependencies.
- **Use Cases**: Task scheduling, dependency resolution.
- **Example Problems**:
    - Course Schedule (LeetCode #207)
    - Alien Dictionary (LeetCode #269)

### 8. **Binary Search**
- **Description**: Efficient search algorithm that works on sorted arrays, reducing the search space by half in each step.
- **Use Cases**: Searching in a sorted array, searching in rotated arrays.
- **Example Problems**:
    - Binary Search (LeetCode #704)
    - Search in Rotated Sorted Array (LeetCode #33)

### 9. **DFS (Depth First Search)**
- **Description**: Explores as far as possible along a branch before backtracking. Often used in recursive problems.
- **Use Cases**: Graph traversal, backtracking, tree problems.
- **Example Problems**:
    - Number of Islands (LeetCode #200)
    - Path Sum (LeetCode #112)

### 10. **BFS (Breadth First Search)**
- **Description**: Explores all the nodes at the present depth before moving on to the nodes at the next depth level.
- **Use Cases**: Shortest path, level-order traversal.
- **Example Problems**:
    - Binary Tree Level Order Traversal (LeetCode #102)
    - Word Ladder (LeetCode #127)

### 11. **Dynamic Programming (DP)**
- **Description**: Breaking down problems into overlapping subproblems, storing their results to avoid redundant calculations.
- **Use Cases**: Knapsack problem, Fibonacci sequence, pathfinding.
- **Example Problems**:
    - Longest Increasing Subsequence (LeetCode #300)
    - House Robber (LeetCode #198)

### 12. **Greedy Algorithm**
- **Description**: Makes the locally optimal choice at each stage with the hope of finding a global optimum.
- **Use Cases**: Interval scheduling, coin change problems.
- **Example Problems**:
    - Jump Game (LeetCode #55)
    - Gas Station (LeetCode #134)

### 13. **Backtracking**
- **Description**: Systematically searches for a solution to a problem by trying multiple possibilities and abandoning paths that don't lead to a valid solution.
- **Use Cases**: Solving puzzles, generating combinations or permutations.
- **Example Problems**:
    - N-Queens (LeetCode #51)
    - Sudoku Solver (LeetCode #37)

### 14. **Union-Find (Disjoint Set Union)**
- **Description**: A data structure to keep track of a set of elements partitioned into disjoint (non-overlapping) subsets.
- **Use Cases**: Finding connected components in graphs, cycle detection.
- **Example Problems**:
    - Number of Connected Components in an Undirected Graph (LeetCode #323)
    - Redundant Connection (LeetCode #684)

### 15. **Trie (Prefix Tree)**
- **Description**: A tree-like data structure that stores strings in a way that allows for fast search and retrieval.
- **Use Cases**: Autocomplete systems, prefix-based searches.
- **Example Problems**:
    - Implement Trie (LeetCode #208)
    - Word Search II (LeetCode #212)

### 16. **Kadane’s Algorithm**
- **Description**: Used to find the maximum sum subarray in a given array.
- **Use Cases**: Maximum subarray sum, variations of subarray problems.
- **Example Problems**:
    - Maximum Subarray (LeetCode #53)

### 17. **Matrix Traversal**
- **Description**: Techniques to traverse 2D grids/matrices.
- **Use Cases**: Pathfinding, flood fill algorithms.
- **Example Problems**:
    - Spiral Matrix (LeetCode #54)
    - Word Search (LeetCode #79)

### 18. **Bit Manipulation**
- **Description**: Solving problems by directly manipulating bits.
- **Use Cases**: XOR, AND, OR operations on bits, finding missing numbers.
- **Example Problems**:
    - Single Number (LeetCode #136)
    - Counting Bits (LeetCode #338)


# Sample questions

---

### 1. **Sliding Window**

1. [LeetCode #3] - Longest Substring Without Repeating Characters
2. [LeetCode #76] - Minimum Window Substring
3. [LeetCode #209] - Minimum Size Subarray Sum
4. [LeetCode #239] - Sliding Window Maximum
5. [LeetCode #567] - Permutation in String
6. [LeetCode #438] - Find All Anagrams in a String

---

### 2. **Two Pointers**

1. [LeetCode #167] - Two Sum II - Input Array Is Sorted
2. [LeetCode #11] - Container With Most Water
3. [LeetCode #15] - 3Sum
4. [LeetCode #19] - Remove Nth Node From End of List
5. [LeetCode #283] - Move Zeroes
6. [LeetCode #876] - Middle of the Linked List

---

### 3. **Fast and Slow Pointers**

1. [LeetCode #141] - Linked List Cycle
2. [LeetCode #142] - Linked List Cycle II
3. [LeetCode #287] - Find the Duplicate Number
4. [LeetCode #876] - Middle of the Linked List
5. [LeetCode #202] - Happy Number
6. [LeetCode #234] - Palindrome Linked List

---

### 4. **Merge Intervals**

1. [LeetCode #56] - Merge Intervals
2. [LeetCode #57] - Insert Interval
3. [LeetCode #252] - Meeting Rooms
4. [LeetCode #253] - Meeting Rooms II
5. [LeetCode #759] - Employee Free Time
6. [LeetCode #986] - Interval List Intersections

---

### 5. **Cyclic Sort**

1. [LeetCode #268] - Missing Number
2. [LeetCode #287] - Find the Duplicate Number
3. [LeetCode #448] - Find All Numbers Disappeared in an Array
4. [LeetCode #645] - Set Mismatch
5. [LeetCode #442] - Find All Duplicates in an Array
6. [LeetCode #41] - First Missing Positive

---

### 6. **In-place Reversal of a Linked List**

1. [LeetCode #206] - Reverse Linked List
2. [LeetCode #92] - Reverse Linked List II
3. [LeetCode #25] - Reverse Nodes in k-Group
4. [LeetCode #143] - Reorder List
5. [LeetCode #234] - Palindrome Linked List
6. [LeetCode #328] - Odd Even Linked List

---

### 7. **Topological Sort (Graph)**

1. [LeetCode #207] - Course Schedule
2. [LeetCode #210] - Course Schedule II
3. [LeetCode #444] - Sequence Reconstruction
4. [LeetCode #1203] - Sort Items by Groups Respecting Dependencies
5. [LeetCode #269] - Alien Dictionary
6. [LeetCode #802] - Find Eventual Safe States

---

### 8. **Binary Search**

1. [LeetCode #704] - Binary Search
2. [LeetCode #33] - Search in Rotated Sorted Array
3. [LeetCode #81] - Search in Rotated Sorted Array II
4. [LeetCode #74] - Search a 2D Matrix
5. [LeetCode #153] - Find Minimum in Rotated Sorted Array
6. [LeetCode #34] - Find First and Last Position of Element in Sorted Array

---

### 9. **DFS (Depth First Search)**

1. [LeetCode #200] - Number of Islands
2. [LeetCode #112] - Path Sum
3. [LeetCode #113] - Path Sum II
4. [LeetCode #130] - Surrounded Regions
5. [LeetCode #694] - Number of Distinct Islands
6. [LeetCode #124] - Binary Tree Maximum Path Sum

---

### 10. **BFS (Breadth First Search)**

1. [LeetCode #102] - Binary Tree Level Order Traversal
2. [LeetCode #127] - Word Ladder
3. [LeetCode #752] - Open the Lock
4. [LeetCode #994] - Rotting Oranges
5. [LeetCode #103] - Binary Tree Zigzag Level Order Traversal
6. [LeetCode #107] - Binary Tree Level Order Traversal II

---

### 11. **Dynamic Programming (DP)**

1. [LeetCode #53] - Maximum Subarray
2. [LeetCode #152] - Maximum Product Subarray
3. [LeetCode #300] - Longest Increasing Subsequence
4. [LeetCode #198] - House Robber
5. [LeetCode #1143] - Longest Common Subsequence
6. [LeetCode #70] - Climbing Stairs

---

### 12. **Greedy Algorithm**

1. [LeetCode #55] - Jump Game
2. [LeetCode #45] - Jump Game II
3. [LeetCode #134] - Gas Station
4. [LeetCode #435] - Non-overlapping Intervals
5. [LeetCode #406] - Queue Reconstruction by Height
6. [LeetCode #763] - Partition Labels

---

### 13. **Backtracking**

1. [LeetCode #51] - N-Queens
2. [LeetCode #37] - Sudoku Solver
3. [LeetCode #46] - Permutations
4. [LeetCode #39] - Combination Sum
5. [LeetCode #47] - Permutations II
6. [LeetCode #22] - Generate Parentheses

---

### 14. **Union-Find (Disjoint Set Union)**

1. [LeetCode #200] - Number of Islands
2. [LeetCode #547] - Number of Provinces
3. [LeetCode #684] - Redundant Connection
4. [LeetCode #323] - Number of Connected Components in an Undirected Graph
5. [LeetCode #721] - Accounts Merge
6. [LeetCode #959] - Regions Cut by Slashes

---

### 15. **Trie (Prefix Tree)**

1. [LeetCode #208] - Implement Trie (Prefix Tree)
2. [LeetCode #211] - Add and Search Word - Data Structure Design
3. [LeetCode #212] - Word Search II
4. [LeetCode #648] - Replace Words
5. [LeetCode #677] - Map Sum Pairs
6. [LeetCode #720] - Longest Word in Dictionary

---

### 16. **Kadane’s Algorithm**

1. [LeetCode #53] - Maximum Subarray
2. [LeetCode #152] - Maximum Product Subarray
3. [LeetCode #918] - Maximum Sum Circular Subarray
4. [LeetCode #363] - Max Sum of Rectangle No Larger Than K
5. [LeetCode #121] - Best Time to Buy and Sell Stock
6. [LeetCode #42] - Trapping Rain Water

---

### 17. **Matrix Traversal**

1. [LeetCode #54] - Spiral Matrix
2. [LeetCode #59] - Spiral Matrix II
3. [LeetCode #79] - Word Search
4. [LeetCode #200] - Number of Islands
5. [LeetCode #542] - 01 Matrix
6. [LeetCode #733] - Flood Fill

---

### 18. **Bit Manipulation**

1. [LeetCode #136] - Single Number
2. [LeetCode #190] - Reverse Bits
3. [LeetCode #191] - Number of 1 Bits
4. [LeetCode #338] - Counting Bits
5. [LeetCode #389] - Find the Difference
6. [LeetCode #268] - Missing Number

---




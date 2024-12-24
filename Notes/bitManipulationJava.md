### Bit Manipulation Techniques in Java

Bit manipulation is a technique that allows you to perform operations directly on binary representations of numbers. It's commonly used in low-level programming, competitive programming, and optimizing algorithms.

---

### **Key Operations**
1. **Bitwise AND (`&`)**
    - **Use**: Sets a bit to `1` if both corresponding bits are `1`.
    - **Example**:
      ```java
      int a = 5; // 0101
      int b = 3; // 0011
      int result = a & b; // 0001 (1 in decimal)
      ```

2. **Bitwise OR (`|`)**
    - **Use**: Sets a bit to `1` if either of the corresponding bits is `1`.
    - **Example**:
      ```java
      int a = 5; // 0101
      int b = 3; // 0011
      int result = a | b; // 0111 (7 in decimal)
      ```

3. **Bitwise XOR (`^`)**
    - **Use**: Sets a bit to `1` if the corresponding bits are different.
    - **Example**:
      ```java
      int a = 5; // 0101
      int b = 3; // 0011
      int result = a ^ b; // 0110 (6 in decimal)
      ```

4. **Bitwise NOT (`~`)**
    - **Use**: Inverts all bits.
    - **Example**:
      ```java
      int a = 5; // 0101
      int result = ~a; // 1010 (in 2's complement form, -6 in decimal)
      ```

5. **Left Shift (`<<`)**
    - **Use**: Shifts bits to the left, adding zeros from the right. Equivalent to multiplying by `2^n`.
    - **Example**:
      ```java
      int a = 5; // 0101
      int result = a << 1; // 1010 (10 in decimal)
      ```

6. **Right Shift (`>>`)**
    - **Use**: Shifts bits to the right, preserving the sign bit (arithmetic shift). Equivalent to dividing by `2^n`.
    - **Example**:
      ```java
      int a = 5; // 0101
      int result = a >> 1; // 0010 (2 in decimal)
      ```

7. **Unsigned Right Shift (`>>>`)**
    - **Use**: Shifts bits to the right, filling with zeros irrespective of the sign bit.
    - **Example**:
      ```java
      int a = -5; // 111...111011 (in 2's complement form)
      int result = a >>> 1; // 011...111101 (large positive number)
      ```

---

### **Common Techniques**

1. **Check if a Number is Odd or Even**
    - **Odd**: `num & 1 == 1`
    - **Even**: `num & 1 == 0`
    - Example:
      ```java
      int num = 5;
      if ((num & 1) == 1) {
          System.out.println("Odd");
      } else {
          System.out.println("Even");
      }
      ```

2. **Check if `k`-th Bit is Set**
    - Formula: `(num & (1 << k)) != 0`
    - Example:
      ```java
      int num = 5; // 0101
      int k = 2;
      boolean isSet = (num & (1 << k)) != 0; // true
      ```

3. **Set the `k`-th Bit**
    - Formula: `num | (1 << k)`
    - Example:
      ```java
      int num = 5; // 0101
      int k = 1;
      int result = num | (1 << k); // 0111 (7 in decimal)
      ```

4. **Clear the `k`-th Bit**
    - Formula: `num & ~(1 << k)`
    - Example:
      ```java
      int num = 5; // 0101
      int k = 2;
      int result = num & ~(1 << k); // 0001 (1 in decimal)
      ```

5. **Toggle the `k`-th Bit**
    - Formula: `num ^ (1 << k)`
    - Example:
      ```java
      int num = 5; // 0101
      int k = 1;
      int result = num ^ (1 << k); // 0100 (4 in decimal)
      ```

6. **Count Set Bits (Hamming Weight)**
    - **Example**:
      ```java
      int num = 5; // 0101
      int count = 0;
      while (num > 0) {
          count += (num & 1);
          num >>= 1;
      }
      System.out.println(count); // 2
      ```

7. **Find the Only Non-Duplicate Number in an Array**
    - XOR all numbers: `result = a ^ b ^ c ^ a ^ c` (duplicates cancel out).
    - Example:
      ```java
      int[] arr = {4, 1, 2, 1, 2};
      int result = 0;
      for (int num : arr) {
          result ^= num;
      }
      System.out.println(result); // 4
      ```
8. **Load binary string and toBinaryString**
```java
        System.out.println(Integer.parseUnsignedInt("100",2));  // 4
        System.out.println(Integer.toBinaryString(4));          //100
```

---

### **Applications**
- **Subset Generation**:
    - Use binary representation to represent subsets.
- **Bit Masking**:
    - Represent states in dynamic programming.
- **Power of Two Check**:
    - Formula: `(num & (num - 1)) == 0`
- **Swapping Without Temp Variable**:
    - Formula: `a ^= b; b ^= a; a ^= b;`

---

## Signed values can be represented in binary using **two's complement representation**, which is the most common method in modern computing.

---

### **Two's Complement Representation**

1. **For Positive Numbers**:
   - The binary representation is the same as the unsigned value.
   - The **most significant bit (MSB)** is `0`, indicating a positive number.

2. **For Negative Numbers**:
   - Take the binary representation of the absolute value.
   - Invert all the bits (**1's complement**).
   - Add `1` to the inverted binary (**2's complement**).
   - The MSB is `1`, indicating a negative number.

---

### **Steps to Represent a Signed Integer**

#### Example: Representing `-5` in an 8-bit binary number
1. Start with the binary representation of `5`:
   ```
   00000101
   ```

2. Invert all bits (1's complement):
   ```
   11111010
   ```

3. Add `1` to the result (2's complement):
   ```
   11111010 + 1 = 11111011
   ```

Thus, `-5` in 8-bit two's complement form is:
```
11111011
```

---

### **Verifying Two's Complement**
To verify, convert the binary representation of `11111011` back to decimal:
1. The MSB is `1`, so it's negative.
2. Invert the bits:
   ```
   11111011 → 00000100
   ```

3. Add `1`:
   ```
   00000100 + 1 = 00000101 (5 in decimal)
   ```

4. Add the negative sign:
   ```
   -5
   ```

---

### **Range of Signed Integers**
For an **n-bit signed integer**, the range is:
```
-(2^(n-1)) to (2^(n-1) - 1)
```

#### Example:
For an 8-bit integer:
- Minimum: `-128` (`10000000` in binary)
- Maximum: `127` (`01111111` in binary)

---

### **Sign Extension**
When extending a signed binary number to a larger size, the sign bit is propagated (preserved). For example:
- Extending `-5` (`11111011` in 8 bits) to 16 bits:
  ```
  11111111 11111011
  ```

---

### **Applications**
- Efficient arithmetic operations, especially subtraction and comparisons.
- Negative number representation simplifies hardware design.

Would you like more examples or details on operations using signed binary numbers?
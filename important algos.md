### 1. [Binary search]
```java
class Solution {
    public int search(int[] nums, int target) {
        return binarySearch(nums, target, 0, nums.length - 1);
    }

    public int binarySearch(int[] nums, int target, int l, int r) {
        if (l > r)
            return -1;

        int mid = l + (r - l) / 2;

        if (nums[mid] == target)
            return mid;
        else if (nums[mid] < target)
            return binarySearch(nums, target, mid + 1, r);
        else
            return binarySearch(nums, target, l, mid - 1);
    }
}
```
### 2. [Methods to Compute GCD]
```java
//Euclidean Algorithm
public int gcd(int a, int b) {
    if (b == 0)
        return a;
    return gcd(b, a % b);
}
//or 
public int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}
```
### 3. []
```java

```
### 4. []
```java

```
### 5. []
```java

```
### 6. []
```java

```
### 7. []
```java

```
### 8. []
```java

```
### 9. []
```java

```
### 10. []
```java

```
### 11. []
```java

```
### 12. []
```java

```
### 13. []
```java

```
### 14. []
```java

```
### 15. []
```java

```
### 16. []
```java

```
### 17. []
```java

```

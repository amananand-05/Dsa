# Top Interview 150 LC


## Part A. Array / String
### 1. [88. Merge Sorted Array] https://leetcode.com/problems/merge-sorted-array/description/
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        // Merge from the end of both arrays
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }

        // Copy remaining elements from nums2 (if any)
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
}
//time: O(m+n)
//space: O(0)
```
```java
 class Solution {
     public void merge(int[] nums1, int m, int[] nums2, int n) {
         int k = 0;
         int[] temp = new int[m];
         for (int i = 0; i < m; i++)
             temp[i] = nums1[i];
         int i = 0, j = 0;
         while (i < m && j < n) {
             if (temp[i] < nums2[j])
                 nums1[k] = temp[i++];
             else
                 nums1[k] = nums2[j++];
             k++;
         }
         while (i < m) {
             nums1[k] = temp[i++];
             k++;
         }
         while (j < n) {
             nums1[k] = nums2[j++];
             k++;
         }
     }
 }
 // time: O(m+n)
 // space: O(m)
```
### 2. []
```java

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

### 18. []
```java

```

### 19. []
```java

```

### 20. []
```java

```

### 21. []
```java

```

### 22. []
```java

```

### 23. []
```java

```

### 24. []
```java

```

### 25. []
```java

```

### 26. []
```java

```

### 27. []
```java

```

### 28. []
```java

```

### 29. []
```java

```

### 30. []
```java

```

### 31. []
```java

```

### 32. []
```java

```

### 33. []
```java

```

### 34. []
```java

```

### 35. []
```java

```

### 36. []
```java

```

### 37. []
```java

```

### 38. []
```java

```

### 39. []
```java

```

### 40. []
```java

```

### 41. []
```java

```

### 42. []
```java

```

### 43. []
```java

```

### 44. []
```java

```

### 45. []
```java

```

### 46. []
```java

```

### 47. []
```java

```

### 48. []
```java

```

### 49. []
```java

```

### 50. []
```java

```

### 51. []
```java

```

### 52. []
```java

```

### 53. []
```java

```

### 54. []
```java

```

### 55. []
```java

```

### 56. []
```java

```

### 57. []
```java

```

### 58. []
```java

```

### 59. []
```java

```

### 60. []
```java

```

### 61. []
```java

```

### 62. []
```java

```

### 63. []
```java

```

### 64. []
```java

```

### 65. []
```java

```

### 66. []
```java

```

### 67. []
```java

```

### 68. []
```java

```

### 69. []
```java

```

### 70. []
```java

```

### 71. []
```java

```

### 72. []
```java

```

### 73. []
```java

```

### 74. []
```java

```

### 75. []
```java

```

### 76. []
```java

```

### 77. []
```java

```

### 78. []
```java

```

### 79. []
```java

```

### 80. []
```java

```

### 81. []
```java

```

### 82. []
```java

```

### 83. []
```java

```

### 84. []
```java

```

### 85. []
```java

```

### 86. []
```java

```

### 87. []
```java

```

### 88. []
```java

```

### 89. []
```java

```

### 90. []
```java

```

### 91. []
```java

```

### 92. []
```java

```

### 93. []
```java

```

### 94. []
```java

```

### 95. []
```java

```

### 96. []
```java

```

### 97. []
```java

```

### 98. []
```java

```

### 99. []
```java

```

### 100. []
```java

```

### 101. []
```java

```

### 102. []
```java

```

### 103. []
```java

```

### 104. []
```java

```

### 105. []
```java

```

### 106. []
```java

```

### 107. []
```java

```

### 108. []
```java

```

### 109. []
```java

```

### 110. []
```java

```

### 111. []
```java

```

### 112. []
```java

```

### 113. []
```java

```

### 114. []
```java

```

### 115. []
```java

```

### 116. []
```java

```

### 117. []
```java

```

### 118. []
```java

```

### 119. []
```java

```

### 120. []
```java

```

### 121. []
```java

```

### 122. []
```java

```

### 123. []
```java

```

### 124. []
```java

```

### 125. []
```java

```

### 126. []
```java

```

### 127. []
```java

```

### 128. []
```java

```

### 129. []
```java

```

### 130. []
```java

```

### 131. []
```java

```

### 132. []
```java

```

### 133. []
```java

```

### 134. []
```java

```

### 135. []
```java

```

### 136. []
```java

```

### 137. []
```java

```

### 138. []
```java

```

### 139. []
```java

```

### 140. []
```java

```

### 141. []
```java

```

### 142. []
```java

```

### 143. []
```java

```

### 144. []
```java

```

### 145. []
```java

```

### 146. []
```java

```

### 147. []
```java

```

### 148. []
```java

```

### 149. []
```java

```

### 150. []
```java

```




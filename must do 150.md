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
### 2. [27. Remove Element] https://leetcode.com/problems/remove-element/description
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                // Only copy when i and k are different to avoid unnecessary assignment
                if (i != k)
                    nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
}
```
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;
        for(int i=0; i<nums.length; i++){
            if(nums[i]!=val){
                if(i != k){
                    nums[i] = nums[i] + nums[k];
                    nums[k] = nums[i] - nums[k];
                    nums[i] = nums[i] - nums[k];
                }
                k++;
            }
        }
        return k;
    }
}
```

### 3. [26. Remove Duplicates from Sorted Array] https://leetcode.com/problems/remove-duplicates-from-sorted-array/description
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int k = 0;
        int n = nums.length;
        if (n < 2)
            return n;
        for (int i = 1; i < n; i++) {
            if (nums[i] != nums[i - 1]) {
                k++;
                nums[k] = nums[i];
            }
        }
        return k + 1;
    }
}

```

### 4. [80. Remove Duplicates from Sorted Array II] https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int k = 2;
        int n = nums.length;
        if (n < 3)
            return n;
        for (int i = 2; i < n; i++)
            if (nums[i] != nums[k - 2])
                nums[k++] = nums[i];
        return k;
    }
}
```
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int k = -1;
        int n = nums.length;
        int[] temp = new int[nums.length];
        if (n < 3)
            return n;
        for (int i = 2; i < nums.length; i++) {
            if (!(nums[i] != nums[i - 1]) &&
                    !(nums[i] == nums[i - 1] && nums[i - 1] != nums[i - 2]))
                temp[i] = -1;
        }
        for (int i = 0; i < nums.length; i++) {
            if (temp[i] != -1)
                nums[++k] = nums[i];
        }
        return k + 1;
    }
}

```

### 5. [169. Majority Element] https://leetcode.com/problems/majority-element/description
```java
// Boyer-Moore Voting Algorithm:
class Solution {
    public int majorityElement(int[] nums) {
        int majorityElement = nums[0], count  = 0;
        for(int num : nums){
            if(count == 0)
               majorityElement = num; 
            count += num == majorityElement ? 1 : -1;
        }
        return majorityElement;
    }
}
// The algorithm states: If the same value keeps coming, the count will increase. Different values will decrease the accumulated count, effectively neutralizing it. When the count reaches zero, we select a new majority element from that point onwards.
```

### 6. [189. Rotate Array] https://leetcode.com/problems/rotate-array/description
```java
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n; // it will calculate the actual shift
        reverse(nums, 0, n - 1); // it will move k element from right end to left
        reverse(nums, 0, k - 1); // fix the order for first k element
        reverse(nums, k, n - 1); // fix the order for last l-k element
    }

    public void reverse(int[] nums, int l, int r) {
        while (l < r) {
            nums[r] += nums[l];
            nums[l] = nums[r] - nums[l];
            nums[r] -= nums[l];
            l++;
            r--;
        }
    }
}
```

### 7. [121. Best Time to Buy and Sell Stock] https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description
```java
class Solution {
    public int maxProfit(int[] prices) {
        int min = Integer.MAX_VALUE, res = 0;
        for (int price : prices) {
            min = Math.min(min, price);
            res = Math.max(res, price - min);
        }
        return res;
    }
}
// at any moment keep track of min form left to present index
// and result will be max of all (present value - min)
```

### 8. [122. Best Time to Buy and Sell Stock II] https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description
```java
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1])
                profit += prices[i] - prices[i - 1];
        }
        return profit;
    }
}
```

### 9. [55. Jump Game] https://leetcode.com/problems/jump-game/description
```java
class Solution {
    public boolean canJump(int[] nums) {
        int maxReachIndex = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            if ((maxReachIndex == i && nums[i] == 0) && i != n - 1)
                return false;
            maxReachIndex = Math.max(maxReachIndex, i + nums[i]);
        }
        return true;
    }
}
```

### 10. [45. Jump Game II] https://leetcode.com/problems/jump-game-ii/description
```java
class Solution {
    public int jump(int[] nums) {
        int maxReachIndex = 0;
        int n = nums.length;
        int currEndIndex = 0;
        int jumps = 0;
        for(int i=0;i<n-1;i++){
            maxReachIndex = Math.max(maxReachIndex, i+nums[i]);
            if(i == currEndIndex){
                jumps++; // it doesnot mean jump is made exactly at currEndIndex
                // but jump is made in between range of the last jump index and currEndIndex
                currEndIndex = maxReachIndex;
                if(currEndIndex >= n-1)
                    break;
            }
        }
        return jumps;
    }
}
```

### 11. [274. H-Index] https://leetcode.com/problems/h-index/description
```java
class Solution {
    public int hIndex(int[] citations) {
        int n = citations.length;
        int[] count = new int[n + 1];

        // Step 1: Fill the count array
        for (int citation : citations) {
            if (citation >= n) {
                count[n]++;
            } else {
                count[citation]++;
            }
        }

        // example: 
        // [3,0,6,1,5]      -> citations
        // [1,1,0,1,0,2]    -> count array values
        // [0,1,2,3,4,5]    -> count array indexes

        // Step 2: Find the H-Index
        int cumulative = 0;
        for (int i = n; i >= 0; i--) {
            cumulative += count[i];
            if (cumulative >= i) {
                return i;
            }
        }
        return 0;
    }
}
```
```java
class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);
        int n = citations.length;
        for(int i=0;i<n;i++){
            int remaining = n-i;
            if(citations[i] >= remaining)
                return remaining;
        }
        return 0;
    }
}
```

### 12. [380. Insert Delete GetRandom O(1)] https://leetcode.com/problems/insert-delete-getrandom-o1/description
```java
class RandomizedSet {
    private Map<Integer,Integer> hm;
    private List<Integer> list;
    private Random rand;

    public RandomizedSet() {
        this.hm= new HashMap<>();
        this.list= new ArrayList<>();
        this.rand = new Random();
    }

    public boolean insert(int val) {
        if(!this.hm.containsKey(val)){
            this.hm.put(val,list.size());
            this.list.add(val);
            return true;
        }
        return false;
    }

    public boolean remove(int val) {
        if(this.hm.containsKey(val)){
            int n = this.list.size();
            int removeIndexInList = hm.get(val);
            int lastElementInList = this.list.get(n-1);
            this.list.set(removeIndexInList, lastElementInList);
            this.list.remove(n-1); // removing last element as it is set  
            // to the val's remove index
            this.hm.put(lastElementInList, removeIndexInList);
            this.hm.remove(val);
            return true;
        }
        return false;
    }

    public int getRandom() {
        return this.list.get(this.rand.nextInt(this.hm.size()));
    }
}

/**
 * Your RandomizedSet object will be instantiated and called as such:
 * RandomizedSet obj = new RandomizedSet();
 * boolean param_1 = obj.insert(val);
 * boolean param_2 = obj.remove(val);
 * int param_3 = obj.getRandom();
 */
```

### 13. [238. Product of Array Except Self] https://leetcode.com/problems/product-of-array-except-self/description
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];
        res[0] = 1;
        for (int i = 1; i < n; i++)
            res[i] = res[i - 1] * nums[i - 1]; // prepare an array with prefix product
        int suffixProduct = 1;
        for (int i = n - 1; i >= 0; i--) { // multiply suffix product on the fly
            res[i] *= suffixProduct;
            suffixProduct *= nums[i];
        }
        return res;
    }
}

```
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int productNonZero = 1;
        int productAll = 1;
        int multiZero = 0;
        for(int num:nums){
            if(num == 0) multiZero++;
            productNonZero *= num != 0 ? num: 1;
            productAll *= num;
        }
        int n = nums.length;
        int[] res = new int[n];
        if(multiZero>1) return res;
        for(int i=0;i<n;i++){
            res[i] = nums[i] == 0 ? productNonZero: productAll/nums[i];
        }
        return res;
    }
}
```

### 14. [134. Gas Station] https://leetcode.com/problems/gas-station/description
```java
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int n = gas.length;
        int sumGas = 0;
        int sumCost = 0;
        for(int i=0;i<n;i++){
            sumGas+=gas[i];
            sumCost+=cost[i];
        }
        if(sumGas<sumCost) return -1;
        int currGas = 0;
        int startIndex = 0;
        for(int i=0;i<n;i++){
            currGas += gas[i] - cost[i];
            if(currGas<0){
                currGas = 0;
                startIndex = i+1;
            }
        }
        return startIndex;
    }
}
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




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
        if(sumGas<sumCost) return -1; //means solution does not exist, circle cannot be covered.
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

### 15. [135. Candy] https://leetcode.com/problems/candy/description
```java
class Solution {
    public int candy(int[] ratings) {
        int n = ratings.length;
        int result = n;
        int[] candies = new int[n];
        for (int i = 1; i < n; i++)
            if (ratings[i - 1] < ratings[i])
                candies[i] = candies[i - 1]+1;
        for (int i = n-2; i >= 0; i--)
            if (ratings[i] > ratings[i + 1])
                candies[i] = Math.max(candies[i + 1] + 1, candies[i]);
        for (int i : candies)
            result += i;
        return result;
    }
}
```
```java
class Solution {
    public int candy(int[] ratings) {
        int n = ratings.length;
        int result = n;
        int up = 0, down = 0, peak = 0;

        for (int i = 1; i < n; i++) {
            if (ratings[i] > ratings[i - 1]) {
                up++;
                peak = up;
                down = 0;
                result += up;
            } else if (ratings[i] < ratings[i - 1]) {
                down++;
                up = 0;
                result += down;
                if (down > peak) result++;
            } else {
                up = down = peak = 0;
            }
        }
        return result;
    }
}

```

### 16. [42. Trapping Rain Water] https://leetcode.com/problems/trapping-rain-water/description
```java
class Solution {
    public int trap(int[] height) {
        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0;
        int result = 0;

        while (left <= right) {
            if (height[left] <= height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    result += leftMax - height[left];
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    result += rightMax - height[right];
                }
                right--;
            }
        }
        return result;
    }
}

```
```java
class Solution {
    public int trap(int[] height) {
        int n = height.length;
        int[][] dbref = new int[n][2];
        for(int i = 0;i<n;i++)
            if(i==0)
                dbref[i][0] = height[i];
            else
                dbref[i][0] = Math.max(dbref[i-1][0],height[i]);

        for(int i = n-1; i>=0; i--)
            if(i==n-1)
                dbref[i][1] = height[i];
            else
                dbref[i][1] = Math.max(dbref[i+1][1],height[i]);
                
        int result = 0;
        for(int i = n-1; i>=0; i--)
            result += Math.min(dbref[i][1],dbref[i][0])-height[i];
        return result;
        
    }
}
```

### 17. [13. Roman to Integer] https://leetcode.com/problems/roman-to-integer/description
```java
class Solution {
    public int romanToInt(String s) {
        int result = 0;
        int n = s.length();
        for(int i=n-1;i>=0;i--){
            if(i<n-1 && getValue(s.charAt(i)) < getValue(s.charAt(i+1)))
                result -= getValue(s.charAt(i));
            else 
                result += getValue(s.charAt(i));
        }
        return result;
        
    }
    private int getValue(char ch){
        switch(ch){
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            case 'M': return 1000;
            default: return 0;
        }
    }
}
```

### 18. [12. Integer to Roman] https://leetcode.com/problems/integer-to-roman/description
```java
class Solution {
    public String intToRoman(int num) {
        String[] symbols = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        int[] values = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
        StringBuilder sb = new StringBuilder();
        for(int i =0; i<13; i++){
            while(values[i] <= num){
                sb.append(symbols[i]);
                num -= values[i];
            }
        }
        return sb.toString();
    }
}
```

### 19. [58. Length of Last Word] https://leetcode.com/problems/length-of-last-word/description
```java
class Solution {
    public int lengthOfLastWord(String s) {
        boolean alphabetAnCountered = false;
        int n = s.length();
        int result = 0;
        for (int i = n - 1; i >= 0; i--) {
            char ch = s.charAt(i);
            if (ch != ' ') {
                alphabetAnCountered = true;
                result++;
            } else if (alphabetAnCountered)
                return result;
        }
        return result;
    }
}
```

### 20. [14. Longest Common Prefix] https://leetcode.com/problems/longest-common-prefix/description
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0)
            return "";
        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++) {
            while (strs[i].indexOf(prefix) != 0) {
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix == "")
                    return "";
            }
        }
        return prefix;
    }
}
```

### 21. [151. Reverse Words in a String] https://leetcode.com/problems/reverse-words-in-a-string/description
```java
class Solution {
    public String reverseWords(String input_s) {
        StringBuilder s = new StringBuilder(input_s);
        int n = s.length();
        int dataIndex = 0;
        for (int i = 0; i < n; i++) {
            char ch = s.charAt(i);
            if (ch != ' ')
                s.setCharAt(dataIndex++, ch);
            else if (ch == ' ' && (i > 0 && s.charAt(i - 1) != ' '))
                s.setCharAt(dataIndex++, ch);
        }
        if (s.charAt(dataIndex - 1) == ' ')
            dataIndex--;
        int left = 0, r = dataIndex - 1;
        reverse(s, left, dataIndex - 1);
        left = 0;
        for (int i = 0; i < dataIndex; i++) {
            if (s.charAt(i) == ' ') {
                s = reverse(s, left, i - 1);
                left = i + 1;
            }
        }
        s = reverse(s, left, dataIndex - 1);
        return s.substring(0, dataIndex).toString();
    }

    public StringBuilder reverse(StringBuilder s, int l, int r) {
        while (l < r) {
            char ch = s.charAt(l);
            s.setCharAt(l, s.charAt(r));
            s.setCharAt(r, ch);
            l++;
            r--;
        }
        return s;
    }
}

// trim spaces
// reverse full string
// reverse the words string
// (words were in the reversed state due to the previous reverse)
// return :)
```

### 22. [6. Zigzag Conversion] https://leetcode.com/problems/zigzag-conversion/description
```java
class Solution {
    public String convert(String s, int numRows) {
        if (numRows == 1 || numRows >= s.length()) {
            return s;
        }

        // Initialize StringBuilder array
        StringBuilder[] sbArr = new StringBuilder[numRows];
        for (int i = 0; i < numRows; i++) {
            sbArr[i] = new StringBuilder();
        }

        int index = 0;
        boolean increase = true;

        // Traverse the string
        for (char c : s.toCharArray()) {
            sbArr[index].append(c);

            // Change direction when reaching top or bottom
            if (index == 0) {
                increase = true;
            } else if (index == numRows - 1) {
                increase = false;
            }

            // Update index based on direction
            index += increase ? 1 : -1;
        }

        // Concatenate all rows
        StringBuilder res = new StringBuilder();
        for (StringBuilder sb : sbArr) {
            res.append(sb);
        }

        return res.toString();
    }
}

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




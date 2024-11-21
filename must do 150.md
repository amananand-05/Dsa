# Top Interview 150 LC


## Part A. Array / String

---
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

### 23. [28. Find the Index of the First Occurrence in a String] https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description
```java
// real solution will go here
// ...
```
```java
class Solution {
    public int strStr(String haystack, String needle) {
        return haystack.indexOf(needle);
    }
}
```

### 24. [68. Text Justification] https://leetcode.com/problems/text-justification/description
```java
class Solution {
    public List<String> fullJustify(String[] words, int maxWidth) {
        int startI = 0,lastI = 0;
        int dataLength = 0; 
        List<String> result = new ArrayList<>();
        for(int i=0;i<words.length;i++){
            dataLength += words[i].length()+1;
            if(dataLength - 1 <= maxWidth)
                lastI = i;
            else{
                result.add(getLineString(words,startI,lastI,maxWidth));
                dataLength = words[i].length()+1;
                startI = lastI = i;
            }
        }
        result.add(getLineString(words,startI,lastI,maxWidth));
        return result;
        
    }
    public String getLineString(String[] words,int startI, int lastI, int maxWidth){
        StringBuilder sb = new StringBuilder();
        int spaces = maxWidth;
        int spacesIntervalCount = lastI-startI;
        for(int i=startI; i<=lastI; i++)
            spaces-=words[i].length();

        if(words.length-1 == lastI){
            for(int i=startI; i<=lastI; i++){
                sb.append(words[i]+(i != lastI ? " " : " ".repeat(spaces)));
                spaces--;
            }
            return sb.toString().substring(0,sb.length());
        }

        if(startI - lastI == 0)
            return words[startI]+" ".repeat(spaces);

        
        for(int i=startI; i<=lastI; i++){
            int temp = spacesIntervalCount > 0 ? (int)Math.ceil((double)spaces/spacesIntervalCount) : 0;
            sb.append(words[i]+" ".repeat(temp));
            spaces -= temp;
            spacesIntervalCount--;
        }
        return sb.toString();
    }
}
```

## Part B. Two Pointers

---
### 25. [125. Valid Palindrome] https://leetcode.com/problems/valid-palindrome/description
```java
class Solution {
    public boolean isPalindrome(String s) {
        int l=0,r=s.length()-1;
        while(l<r){
            if( legit(s.charAt(l)) > 0 && 
                legit(s.charAt(r)) > 0 &&
                legit(s.charAt(l)) != legit(s.charAt(r))
                ) return false;
            else if(legit(s.charAt(l)) < 0) l++;
            else if(legit(s.charAt(r)) < 0) r--;
            else{
                l++;
                r--;
            }
        }
        return true;
        
    }
    public int legit(char ch){
        if ((97 <= ch && ch <= 97 + 25) ||
                (65 <= ch && ch <= 65 + 25) ||
                (48 <= ch && ch <= 48 + 9)) {
                return (65 <= ch && ch <= 65 + 25) ? (int) (ch + 32) : (int)ch;
            }
        return -1;

    }
}
```
```java
class Solution {
    public boolean isPalindrome(String s) {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if ((97 <= ch && ch <= 97 + 25) ||
                    (65 <= ch && ch <= 65 + 25) ||
                    (48 <= ch && ch <= 48 + 9)) {
                sb.append((65 <= ch && ch <= 65 + 25) ? (char) (ch + 32) : ch);
            }
        }
        int l = 0, r = sb.length() - 1;
        while (l < r) {
            if (sb.charAt(l) != sb.charAt(r))
                return false;
            l++;
            r--;
        }
        return true;
    }
}
```

### 26. [392. Is Subsequence] https://leetcode.com/problems/is-subsequence/description
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int pointer1 = 0;
        int pointer2 = 0;
        while (pointer1 < s.length() && pointer2 < t.length()) {
            if (s.charAt(pointer1) == t.charAt(pointer2))
                pointer1++;
            pointer2++;
        }
        return pointer1 == s.length();
    }
}
```

### 27. [167. Two Sum II - Input Array Is Sorted] https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int l = 0, r = numbers.length - 1;
        int[] res = new int[2];
        while (l < r) {
            if (numbers[l] + numbers[r] == target) {
                res[0] = l + 1;
                res[1] = r + 1;
                return res;
            } else if (numbers[l] + numbers[r] > target)
                r--;
            else
                l++;
        }
        return res;

    }
}
```

### 28. [11. Container With Most Water] https://leetcode.com/problems/container-with-most-water/description
```java
class Solution {
    public int maxArea(int[] height) {
        int l = 0, r=height.length-1;
        int maxWater = 0;
        while(l<r){
            maxWater = Math.max(maxWater, water(height,l,r));
            if(height[l] <= height[r])
                l++;
            else
                r--;
        }
        return maxWater;
    }
    public int water(int[] height, int l, int r){
        return (r-l)*Math.min(height[l],height[r]);
    }
}
```

### 29. [15. 3Sum] https://leetcode.com/problems/3sum/description
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        int n = nums.length, l, r;
        for(int i=0;i<nums.length-2;i++){
            if(i>0 && nums[i] == nums[i-1]) continue;

            l = i+1;
            r = n-1;
            int target = 0 - nums[i];
            while(l<r){
                int sum = nums[l]+nums[r];
                if(sum == target){
                    result.add(Arrays.asList(nums[i],nums[l],nums[r]));
                    while(l<r && nums[l] == nums[l+1]) l++;
                    while(l<r && nums[r] == nums[r-1]) r--;
                    l++;
                    r--;
                }else if(sum < target)
                    l++;
                else
                    r--; 
            }
        }
        return result;
    }
}
```

## Part C. Sliding Window

---
### 30. [209. Minimum Size Subarray Sum] https://leetcode.com/problems/minimum-size-subarray-sum/description
```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        
        int l=0;
        int sum=0;
        int minInterval = Integer.MAX_VALUE;
        for(int r=0;r<nums.length;r++){
            sum += nums[r];
            while(sum>=target){
                minInterval = Math.min(minInterval, r-l+1);
                sum -= nums[l];
                l++;
            }
        }
        return Integer.MAX_VALUE != minInterval ? minInterval : 0;
    }
}
```
```java
// --- wrong solution [Time Limit Exceeded] [brute force]
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int minLength = 1;
        int n = nums.length;
        while (minLength <= n) {
            int temp = 0;
            int sum = 0;
            while (temp < minLength) {
                sum += nums[temp];
                temp++;
            }
            if (sum >= target)
                return minLength;
            System.out.println(minLength + " " + sum);
            while (temp < n) {
                sum = sum + nums[temp] - nums[temp - minLength];
                if (sum >= target)
                    return minLength;
                System.out.println(minLength + " " + sum);
                temp++;
            }
            minLength++;
        }
        return 0;
    }
}
```

### 31. [3. Longest Substring Without Repeating Characters] https://leetcode.com/problems/longest-substring-without-repeating-characters/description
```java
class Solution { // didn't understand
    public int lengthOfLongestSubstring(String s) {
        int longSubStrLen = 0;
        int[] lastSeen = new int[128];
        int l = 0;
        for (int r = 0; r < s.length(); r++) {
            char currentChar = s.charAt(r);
            if (lastSeen[currentChar] > 0) 
                l = Math.max(l, lastSeen[currentChar]);
            lastSeen[currentChar] = r + 1;

            longSubStrLen = Math.max(longSubStrLen, r - l + 1);
        }

        return longSubStrLen;
    }
}
```
```java
class Solution1 { // my sol
    public int lengthOfLongestSubstring(String s) {
        int longSubStrLen = 0;
        int[] chRef = new int[128];
        int l = 0;
        for (int r = 0; r < s.length(); r++) {
            if (chRef[s.charAt(r)] == 0) {
                chRef[s.charAt(r)] += 1;
                System.out.println(s.substring(l, r + 1));
                longSubStrLen = Math.max(longSubStrLen, r - l + 1);
            } else {
                chRef[s.charAt(l)] = 0;
                l++;
                r--;
            }
        }
        return longSubStrLen;

    }
}
```

### 32. [30. Substring with Concatenation of All Words] https://leetcode.com/problems/substring-with-concatenation-of-all-words/description
- hard
```java
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        List<Integer> result = new ArrayList<>();
        if (s == null || s.length() == 0 || words == null || words.length == 0) {
            return result;
        }

        // Create a frequency map for the words
        HashMap<String, Integer> wordFreqMap = new HashMap<>();
        for (String word : words) {
            wordFreqMap.put(word, wordFreqMap.getOrDefault(word, 0) + 1);
        }

        int wordLen = words[0].length();
        int wordCount = words.length;
        int totalLen = wordLen * wordCount;
        int n = s.length();

        // Iterate over the first `wordLen` characters to cover all starting points
        for (int i = 0; i < wordLen; i++) {
            int left = i, right = i, count = 0;
            HashMap<String, Integer> tempMap = new HashMap<>();

            while (right + wordLen <= n) {
                String word = s.substring(right, right + wordLen);
                right += wordLen;

                if (wordFreqMap.containsKey(word)) {
                    tempMap.put(word, tempMap.getOrDefault(word, 0) + 1);
                    count++;

                    while (tempMap.get(word) > wordFreqMap.get(word)) {
                        String leftWord = s.substring(left, left + wordLen);
                        tempMap.put(leftWord, tempMap.get(leftWord) - 1);
                        count--;
                        left += wordLen;
                    }

                    if (count == wordCount) {
                        result.add(left);
                    }
                } else {
                    tempMap.clear();
                    count = 0;
                    left = right;
                }
            }
        }

        return result;
    }
}

```

### 33. [76. Minimum Window Substring] https://leetcode.com/problems/minimum-window-substring/description
- hard
```java

```

## Part D. Matrix

### 34. [36. Valid Sudoku] https://leetcode.com/problems/valid-sudoku/description
- medium
```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        int[] nums;

        // (x,y)
        // x-> row
        // y-> col

        // for rows
        for (int i = 0; i < 9; i++) {
            nums = new int[9];
            for (int j = 0; j < 9; j++) {
                if (board[i][j] == '.')
                    continue;
                if (board[i][j] < 49 || 57 < board[i][j])
                    return false;
                nums[board[i][j] - 49] += 1;
                if (nums[board[i][j] - 49] > 1)
                    return false;
            }
        }
        // for cols
        // col and row can be done in the same array using two nums array and exchanging
        // i and j
        for (int i = 0; i < 9; i++) {
            nums = new int[9];
            for (int j = 0; j < 9; j++) {
                if (board[j][i] == '.')
                    continue;
                nums[board[j][i] - 49] += 1;
                if (nums[board[j][i] - 49] > 1)
                    return false;
            }
        }
        // for boxes
        for (int i = 0; i < 9; i += 3) {
            for (int j = 0; j < 9; j += 3) {
                nums = new int[9];
                for (int k = i; k < i + 3; k++) {
                    for (int l = j; l < j + 3; l++) {
                        if (board[k][l] == '.')
                            continue;
                        nums[board[k][l] - 49] += 1;
                        if (nums[board[k][l] - 49] > 1)
                            return false;
                    }
                }
            }
        }
        return true;
    }
}
```

### 35. [54. Spiral Matrix] https://leetcode.com/problems/spiral-matrix/description
- medium
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<>();
        if (matrix == null || matrix.length == 0) {
            return result;
        }
        int rows = matrix.length;
        int cols = matrix[0].length;
        int top = 0, bottom = rows - 1, left = 0, right = cols - 1;
        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) {
                result.add(matrix[top][i]);
            }
            top++;
            for (int i = top; i <= bottom; i++) {
                result.add(matrix[i][right]);
            }
            right--;
            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    result.add(matrix[bottom][i]);
                }
                bottom--;
            }
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    result.add(matrix[i][left]);
                }
                left++;
            }
        }       
        return result;
    }
}
```
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> li = new ArrayList<>();
        int rows = matrix.length; // row 
        int cols = matrix[0].length; // col 

        int offSet = 0;
        while(li.size() < rows*cols){
            for(int i=0+offSet;i<cols-offSet && li.size() < rows*cols;i++)
                li.add(matrix[0+offSet][i]);

            for(int i=1+offSet;i<matrix.length-offSet && li.size() < rows*cols;i++)
                li.add(matrix[i][cols-1-offSet]);

            for(int i=cols-2-offSet;i>=0+offSet && li.size() < rows*cols;i--)
                li.add(matrix[rows-1-offSet][i]);

            for(int i=rows-2-offSet;i>=1+offSet && li.size() < rows*cols;i--)
                li.add(matrix[i][0+offSet]);
            offSet++;
        }
        return li;
    }
}
```

### 36. [48. Rotate Image] https://leetcode.com/problems/rotate-image/description
```java
class Solution {
    public void rotate(int[][] matrix) {
        // tranpose table and reverse row values
        int n = matrix.length;
        for (int i = 0; i < n; i++)
            for (int j = i; j < n; j++) {
                System.out.print(matrix[i][j]);
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        for (int i = 0; i < n; i++) {
            int l = 0;
            int r = n - 1;
            while (l < r) {
                int temp = matrix[i][l];
                matrix[i][l] = matrix[i][r];
                matrix[i][r] = temp;
                l++;
                r--;
            }
        }
    }
}
```

### 37. [73. Set Matrix Zeroes] https://leetcode.com/problems/set-matrix-zeroes/description
- medium
```java
// O(m + n) space --------
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length; // rows
        int n = matrix[0].length; // cols 
        int rowZero[] = new int[m];
        int colZero[] = new int[n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j] == 0){
                    rowZero[i] = 1;
                    colZero[j] = 1;
                }
            }
        }
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(rowZero[i]==1 || colZero[j]==1){
                    matrix[i][j]=0;
                }
            }
        }
    }
}
```
```java
// O(1) space --------
// considering 1000 any number x will never be in data
class Solution {
    public void setZeroes(int[][] m) {
        int rows = m.length;
        int cols = m[0].length;
        boolean headRow = false;
        boolean headCol = false;

        for(int i=0;i<rows;i++){
            if(m[i][0] == 0){
                headCol = true;
                break;
            }
        }
        for(int i=0;i<cols;i++){
            if(m[0][i] == 0){
                headRow = true;
                break;
            }
        }

        for(int i=0;i<rows;i++){
            for(int j=0;j<cols;j++){
                if(m[i][j] == 0){
                    m[i][0] = 1000;
                    m[0][j] = 1000;
                }
            }
        }
        for(int i=1;i<rows;i++){
            for(int j=1;j<cols;j++){
                if(m[i][0] == 1000 || m[0][j] == 1000){
                    m[i][j] = 0;
                }
            }
        }

        for(int i=0;i<rows;i++){
            if(m[i][0] == 1000 || headCol){
                m[i][0] = 0;
            }
        }
        for(int i=0;i<cols;i++){
            if(m[0][i] == 1000 || headRow){
                m[0][i] = 0;
            }
        }
    }
}
```

### 38. [289. Game of Life] https://leetcode.com/problems/game-of-life/description
- medium
```java
class Solution {
    public void gameOfLife(int[][] board) {
        int[][] boardRef = new int[board.length][board[0].length];
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                boardRef[i][j] = board[i][j]; // Deep copy
            }
        }
        for(int i = 0;i<boardRef.length;i++){
            for(int j = 0; j<boardRef[0].length;j++){
                boardRef[i][j] = getNeighborsCount(board,i,j);
            }
        }
        for(int i = 0;i<boardRef.length;i++){
            for(int j = 0; j<boardRef[0].length;j++){
                if(boardRef[i][j] < 2)
                    board[i][j] = 0;
                else if(board[i][j] == 0 && boardRef[i][j] == 3)
                    board[i][j] = 1;
                else if(boardRef[i][j] > 3)
                    board[i][j] = 0;
            }
        }
    }
    public int getNeighborsCount(int[][] board, int i,int j){
        return 
        getVal(board, i+1,j) +      //bottom
        getVal(board, i-1,j-1) +    //topleft
        getVal(board, i-1,j) +      //top
        getVal(board, i-1,j+1) +    //topright
        getVal(board, i,j-1) +      //left
        getVal(board, i+1,j-1) +    //bottomleft
        getVal(board, i,j+1) +      //right
        getVal(board, i+1,j+1);     //bottomright
    }
    public int getVal(int[][] board, int i,int j){
        try{
            return board[i][j];
        }catch(Exception e){
            return 0;
        }
    }
}
```
```java
class Solution {
    public void gameOfLife(int[][] board) {
        int rows = board.length, cols = board[0].length;

        // Traverse each cell in the board
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                int neighbors = getNeighborsCount(board, i, j);

                // Encode the next state:
                // - 01 (binary) represents the cell is currently dead and will stay dead.
                // - 10 (binary) represents the cell is alive but will die.
                // - 11 (binary) represents the cell is alive and will stay alive.
                // - 00 (binary) represents the cell is dead and will stay dead.

                // Rule 1 or Rule 3: Cell dies due to underpopulation or overpopulation
                if (board[i][j] == 1 && (neighbors < 2 || neighbors > 3)) {
                    board[i][j] = 1; // Encode 01 (binary), current 1 -> next 0
                }
                // Rule 4: Dead cell becomes alive by reproduction
                else if (board[i][j] == 0 && neighbors == 3) {
                    board[i][j] = 2; // Encode 10 (binary), current 0 -> next 1
                }
                // Rule 2: Cell stays alive with 2 or 3 neighbors
                else if (board[i][j] == 1) {
                    board[i][j] = 3; // Encode 11 (binary), current 1 -> next 1
                }
            }
        }

        // Finalize the board by extracting the next state
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                board[i][j] >>= 1; // Right shift to get the next state
            }
        }
    }

    private int getNeighborsCount(int[][] board, int row, int col) {
        int rows = board.length, cols = board[0].length;
        int count = 0;

        // Directions for the 8 neighbors
        int[][] directions = {
            {-1, -1}, {-1, 0}, {-1, 1},
            {0, -1},          {0, 1},
            {1, -1}, {1, 0}, {1, 1}
        };

        for (int[] dir : directions) {
            int newRow = row + dir[0], newCol = col + dir[1];
            if (newRow >= 0 && newRow < rows && newCol >= 0 && newCol < cols) {
                // Check the least significant bit (current state)
                count += board[newRow][newCol] & 1;
            }
        }

        return count;
    }
}

```
## Part E. Hashmap

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




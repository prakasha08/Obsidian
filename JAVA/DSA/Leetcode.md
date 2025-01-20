# list
## [136. Single Number](https://leetcode.com/problems/single-number/)
```java
class Solution {
    public int singleNumber(int[] nums) {
        List<Integer> n = new ArrayList<>();
        for(int i=0;i<nums.length;i++){
            if(!n.contains(nums[i]))
                n.add(nums[i]);
            else
                n.remove(Integer.valueOf(nums[i]));
        }
        return n.get(0);
    }
}
```
## [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int[][] d = {{0,1},{1,0},{0,-1},{-1,0}};
        int row = matrix.length;
        int col = matrix[0].length;
        boolean[][] visited = new boolean[row][col];
        int k = 0;
        int r = 0,c = 0;
        int dr = d[0][0];
        int dc = d[0][1];
        List<Integer> result = new ArrayList<>();
        while(result.size()!=row*col){
            result.add(matrix[r][c]);
            visited[r][c] = true;
            int nr = r + d[k][0];
            int nc = c + d[k][1];
            if (nr < 0 || nr >= row || nc < 0 || nc >= col || visited[nr][nc]) {
                k = (k + 1) % 4; 
                nr = r + d[k][0];
                nc = c + d[k][1];
            }
            r = nr;
            c = nc;
        }
        return result;
    }
}
```
## [59. Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)
```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] d = {{0,1},{1,0},{0,-1},{-1,0}};
        int[][] matrix = new int[n][n];
        boolean[][] visited = new boolean[n][n];
        int k = 0;
        int r = 0,c = 0;
        int dr = d[0][0];
        int dc = d[0][1];
        int i = 1;
        while( i <= n*n){
           matrix[r][c] = i++;
            visited[r][c] = true;
            int nr = r + d[k][0];
            int nc = c + d[k][1];
            if (nr < 0 || nr >= n || nc < 0 || nc >= n || visited[nr][nc]) {
                k = (k + 1) % 4; 
                nr = r + d[k][0];
                nc = c + d[k][1];
            }
            r = nr;
            c = nc;
        }
        return matrix;
    }
}
```
## [885. Spiral Matrix III](https://leetcode.com/problems/spiral-matrix-iii/)
```java
class Solution {
    public int[][] spiralMatrixIII(int rows, int cols, int rStart, int cStart) {
        int step = 1;
        int k = 0;
        int[][] direction = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
        int r = rStart, c = cStart;
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        while (result.size() < (rows * cols)) {
            for (int i = 0; i < 2; i++) {
                int dR = direction[k][0];
                int dC = direction[k][1];
                for (int j = 0; j < step; j++) {
                    if (0 <= r && r < rows && 0 <= c && c < cols) {
                        ArrayList<Integer> row = new ArrayList<>();
                        row.add(r);
                        row.add(c);
                        result.add(row);
                    }
                    r = r + dR;
                    c = c + dC;
                }
                k = (k + 1) % 4;
            }
            step += 1;
        }
        int[][] array = new int[result.size()][];
        for (int i = 0; i < result.size(); i++) {
            ArrayList<Integer> row = result.get(i);
            array[i] = new int[row.size()];
            for (int j = 0; j < row.size(); j++) {
                array[i][j] = row.get(j);
            }
        }
        return array;
    }
}
```
## [442. Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)
```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        int[] count = new int[nums.length + 1];
        List<Integer> res = new ArrayList<>();
        for(int num : nums){
            if(count[num] == 1){
                res.add(num);
            }
            count[num]++;
        }
        return res;
    }
}
```
# HashMap && HashSet
## [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<>();
        for (int num : nums1) {
            set1.add(num);
        }
        HashSet<Integer> resultSet = new HashSet<>();
        for (int num : nums2) {
            if (set1.contains(num)) {
                resultSet.add(num);
            }
        }
        int[] resultArray = new int[resultSet.size()];
        int i = 0;
        for (int num : resultSet) {
            resultArray[i++] = num;
        }
        return resultArray;
    }
}
```
## [350. Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)
```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for (int num : nums1) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        ArrayList<Integer> resultSet = new ArrayList<>();
        for (int num : nums2) {
            if (map.containsKey(num) && map.get(num)>0) {
                resultSet.add(num);
                 map.put(num, map.get(num) - 1);
            }
        }
        int[] resultArray = new int[resultSet.size()];
        int i = 0;
        for (int num : resultSet) {
            resultArray[i++] = num;
        }
        return resultArray;
    }
}
```
## [2215. Find the Difference of Two Arrays](https://leetcode.com/problems/find-the-difference-of-two-arrays/)
```java
class Solution {
    public List<List<Integer>> findDifference(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<>();
        List<List<Integer>> result = new ArrayList<>();
        for (int num : nums1) {
            set1.add(num);
        }
        HashSet<Integer> set2 = new HashSet<>();
        for (int num : nums2) {
            set2.add(num);
        } 
        List<Integer> temp = new ArrayList<>();
        for (int num : nums1) {
            if(!set2.contains(num) && !temp.contains(num)){
                temp.add(num);
            }
        }
        result.add(temp);
         temp = new ArrayList<>();
        for (int num : nums2) {
            if(!set1.contains(num) && !temp.contains(num)){
                temp.add(num);
            }
        }
        result.add(temp);
        return result;
    }
}
```

```java
import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;

class Solution {
    public List<List<Integer>> findDifference(int[] nums1, int[] nums2) {
        // Use HashSet to store unique elements from nums1 and nums2
        HashSet<Integer> set1 = new HashSet<>();
        HashSet<Integer> set2 = new HashSet<>();
        
        for (int num : nums1) {
            set1.add(num);
        }
        for (int num : nums2) {
            set2.add(num);
        }
        
        // Lists to store the result
        List<Integer> uniqueToNums1 = new ArrayList<>();
        List<Integer> uniqueToNums2 = new ArrayList<>();
        
        // Find elements in nums1 that are not in nums2
        for (int num : set1) {
            if (!set2.contains(num)) {
                uniqueToNums1.add(num);
            }
        }
        
        // Find elements in nums2 that are not in nums1
        for (int num : set2) {
            if (!set1.contains(num)) {
                uniqueToNums2.add(num);
            }
        }
        
        // Add the results to the final list
        List<List<Integer>> result = new ArrayList<>();
        result.add(uniqueToNums1);
        result.add(uniqueToNums2);
        
        return result;
    }
}
```
## [2540. Minimum Common Value](https://leetcode.com/problems/minimum-common-value/)
```java
class Solution {
    public int getCommon(int[] nums1, int[] nums2) {
      HashSet<Integer> set1 = new HashSet<>();
        for (int num : nums1) {
            set1.add(num);
        }
        for (int num : nums2) {
            if (set1.contains(num)) {
                return num;
            }
        }
        return -1;  
    }
}
```
Optimal way     ||
            V 
```java
import java.util.Arrays;

class Solution {
    public int getCommon(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);

        int i = 0, j = 0;
        while (i < nums1.length && j < nums2.length) {
            if (nums1[i] == nums2[j]) {
                return nums1[i];
            } else if (nums1[i] < nums2[j]) {
                i++;
            } else {
                j++;
            }
        }
        return -1;
    }
}
```

## [599. Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)
```java
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
        HashMap<String, Integer> map = new HashMap<>();
        for (int i = 0; i < list1.length; i++) {
            map.put(list1[i], i);
        }
        ArrayList<String> result = new ArrayList<>();
        int minIndexSum = Integer.MAX_VALUE;
        for (int i = 0; i < list2.length; i++) {
            if (map.containsKey(list2[i])) {
                int indexSum = i + map.get(list2[i]);
                if (indexSum < minIndexSum) {
                    result.clear();
                    result.add(list2[i]);
                    minIndexSum = indexSum;
                } 
                else if (indexSum == minIndexSum) {
                    result.add(list2[i]);
                }
            }
        }
        return result.toArray(new String[0]);
    }
}
```
## [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/)
```java
class Solution {
    public int romanToInt(String s) {
        int res=0;
        HashMap<Character,Integer> roman = new HashMap<>();
        roman.put('I',1);
        roman.put('V',5);
        roman.put('X',10);
        roman.put('L',50);
        roman.put('C',100);
        roman.put('D',500);
        roman.put('M',1000);
        for(int i=0;i<s.length();i++){
            if(i<s.length()-1 && roman.get(s.charAt(i))<roman.get(s.charAt(i+1))){
                res-=roman.get(s.charAt(i));
                continue;
            }
            res+=roman.get(s.charAt(i));
        }
        return res;
    }
}
```
## [961. N-Repeated Element in Size 2N Array](https://leetcode.com/problems/n-repeated-element-in-size-2n-array/)
```java
class Solution {
    public int repeatedNTimes(int[] nums) {
        HashSet s=new HashSet<>();
        for(int i=0;i<nums.length;i++){
            if(!s.contains(nums[i]))
                s.add(nums[i]);
            else 
                return nums[i];
        }
        return -1;
    }
}
```
Using HashMap
```java
class Solution {
    public int repeatedNTimes(int[] nums) {
        int n = nums.length/2;
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int num : nums){
            map.put(num,map.getOrDefault(num,0)+1);
        }
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if(entry.getValue()==n)
                return entry.getKey();
        }
        return 0;
    }
}
```
## [819. Most Common Word](https://leetcode.com/problems/most-common-word/)
```java
import java.util.HashMap;
import java.util.HashSet;
import java.util.Map;

class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        // Step 1: Convert banned words to a HashSet for O(1) lookup
        HashSet<String> ban = new HashSet<>();
        for (String banWord : banned) {
            ban.add(banWord.toLowerCase());
        }

        // Step 2: Process the paragraph and count word occurrences
        HashMap<String, Integer> para = new HashMap<>();
        paragraph = paragraph.toLowerCase();
        StringBuilder word = new StringBuilder();

        for (int i = 0; i < paragraph.length(); i++) {
            char c = paragraph.charAt(i);

            // If the character is a letter, build the word
            if (Character.isLetter(c)) {
                word.append(c);
            } else if (word.length() > 0) {
                // Non-letter found, process the word
                String finalWord = word.toString();
                if (!ban.contains(finalWord)) {
                    para.put(finalWord, para.getOrDefault(finalWord, 0) + 1);
                }
                word = new StringBuilder(); // Reset for the next word
            }
        }

        // Step 3: Handle the last word if the paragraph ends without punctuation
        if (word.length() > 0) {
            String finalWord = word.toString();
            if (!ban.contains(finalWord)) {
                para.put(finalWord, para.getOrDefault(finalWord, 0) + 1);
            }
        }

        // Step 4: Find the most common word
        String mostCommon = "";
        int maxCount = 0;
        for (Map.Entry<String, Integer> entry : para.entrySet()) {
            if (entry.getValue() > maxCount) {
                mostCommon = entry.getKey();
                maxCount = entry.getValue();
            }
        }

        return mostCommon;
    }
}
```
## [2399. Check Distances Between Same Letters](https://leetcode.com/problems/check-distances-between-same-letters/)
```java
class Solution {
    public boolean checkDistances(String s, int[] distance) {
        HashMap<Character, Integer> Distance = new HashMap<>();
        
        // Loop through the string to populate the Distance map
        for (int i = 0; i < s.length(); i++) {
            char currChar = s.charAt(i);
            
            // If it's the first time encountering the character, store its index
            if (!Distance.containsKey(currChar)) {
                Distance.put(currChar, i);
            } 
            // Else calculate the distance between occurrences
            else {
                // Update the map with the distance between the two occurrences of the character
                Distance.put(currChar, i - Distance.get(currChar) - 1);
            }
        }
        
        // Now compare distances with the provided distance array
        for (int i = 0; i < distance.length; i++) {
            char expectedChar = (char) (i + 'a');  // Convert index to corresponding character
            
            // If the character appears in the string, compare the distances
            if (Distance.containsKey(expectedChar)) {
                int currDistance = Distance.get(expectedChar);
                if (distance[i] != currDistance) {
                    return false;  // If the distance doesn't match, return false
                }
            }
        }
        
        return true;  // If all distances match, return true
    }
}
```
## [136. Single Number](https://leetcode.com/problems/single-number/)

```java
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        for(int i=0;i<nums.length-1;i+=2){
            if(nums[i]!=nums[i+1])
                return nums[i];
        }
        return nums[nums.length-1];
    }
}
```

```java
class Solution {
    public int singleNumber(int[] nums) {
        int k=0;
        for(int i=0;i<nums.length;i++){
           k^=nums[i];
        }
       return k;
    }
}
```

```java
//using HashMap//TC:O(n),SC:O(n)
class Solution {
    public int singleNumber(int[] nums) {
      HashMap<Integer,Integer> n = new HashMap<>();
        for(int i =0 ;i<nums.length;i++){
        n.put(nums[i],n.getOrDefault(nums[i],0)+1);
        }
        for(int i=0;i<nums.length;i++){
            if(n.get(nums[i])==1)
                return nums[i];
        }
        return 0;
    }
}
```

```java
///TC:O(n^2)
class Solution {
    public int singleNumber(int[] nums) {
        HashSet<Integer> n = new HashSet<>();
        int arraySum=0,setSum=0;
        for(int i =0 ;i<nums.length;i++){
           if(n.contains(nums[i]) == false){
                n.add(nums[i]);
                setSum+=nums[i];
           }
           arraySum+=nums[i];
        }
        return 2*setSum-arraySum;
    }
}
```

## [137. Single Number II](https://leetcode.com/problems/single-number-ii/)
```java
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        for(int i=0;i<nums.length-1;i+=3){
            if(nums[i]!=nums[i+1])
                return nums[i];
        }
        return nums[nums.length-1];
    }
}
```

```java
```java
class Solution {
    public int singleNumber(int[] nums) {
        HashMap<Integer,Integer> n = new HashMap<>();
        for(int i =0 ;i<nums.length;i++){
            n.put(nums[i],n.getOrDefault(nums[i],0)+1);
        }
        for(int i=0;i<nums.length;i++){
            if(n.get(nums[i])==1)
                return nums[i];
        }
        return 0;
    }
}
```
## [137. Single Number II](https://leetcode.com/problems/single-number-ii/)
```java
class Solution {
    public int[] singleNumber(int[] nums) {
        HashMap<Integer,Integer> n = new HashMap<>();
        int[] result = new int[2];
        int k=0;
        for(int i =0 ;i<nums.length;i++){
            n.put(nums[i],n.getOrDefault(nums[i],0)+1);
        }
        for(int i=0;i<nums.length;i++){
            if(n.get(nums[i])==1)
                result[k++] = nums[i];
        }
        return result;
    }
}
```

```java
class Solution {
    public int[] singleNumber(int[] nums) {
        HashSet<Integer> n = new HashSet<>();
        int[] result = new int[2];
        int k=0;
        for(int i =0 ;i<nums.length;i++){
           if(!n.contains(nums[i]))
                n.add(nums[i]);
           else
                n.remove(nums[i]);
        }
        for(int N:n){
           result[k++]=N;
        }
        return result;
    }
}
```
## [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
```java 
///using Stack And HashMap
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int n1=nums1.length;
        int n2 =  nums2.length;
        int[] res = new int[n1];
        HashMap<Integer,Integer> map = new HashMap<>();
        Stack<Integer> stack = new Stack();
        for(int i=0;i<n2;i++){
            while(!stack.empty()&&nums2[i]>stack.peek()){
                map.put(stack.pop(),nums2[i]);
            stack.push(nums2[i]);
        }
        for(int i=0;i<n1;i++){
            res[i]=map.getOrDefault(nums1[i],-1);
        }
        return res;
    }
}
```

```java 
//using Dequeu(Interface) and HashMap
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int n1=nums1.length;
        int n2 =  nums2.length;
        int[] res = new int[n1];
        HashMap<Integer,Integer> map = new HashMap<>();
        Deque<Integer> stack = new ArrayDeque<>();
        for(int i=0;i<n2;i++){
            while(!stack.isEmpty()&&nums2[i]>stack.peek()){
                map.put(stack.pop(),nums2[i]);
            }
            stack.push(nums2[i]);
        }
        for(int i=0;i<n1;i++){
            res[i]=map.getOrDefault(nums1[i],-1);
        }
        return res;
    }
}
```
## [503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)
```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int n=nums.length;
        int[] res = new int[n];
        Arrays.fill(res,-1);
        Stack<Integer> stack = new Stack();
        for(int i=0;i<2*n;i++){
            while(!stack.empty()&&nums[i%n]>nums[stack.peek()]){
                res[stack.pop()]=nums[i%n];
            }
            stack.push(i%n);
        }
        return res;
    }
}
```
## [128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> N=new HashSet<>();
        int max=0;
        for(int num:nums){
            N.add(num);
        }
        for(int num:N){
            if(!N.contains(num-1)){
                int count=1;
                while(N.contains(num+count)){
                    count++;
                }
                if(count>max)max=count;
            }
        }
         return max;
    }
}
```
## [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
```java
import java.util.HashSet;

  

class Solution {

    public int lengthOfLongestSubstring(String s) {

        int count = 0;

        for (int i = 0; i < s.length(); i++) {

            HashSet<Character> lS = new HashSet<>();

            for (int j = i; j < s.length(); j++) {

                if (!lS.contains(s.charAt(j))) {

                    lS.add(s.charAt(j));

                } else {

                    break;

                }

            }

            if (lS.size() > count) {

                count = lS.size();

            }

        }

        return count;

    }

}
```

```java
import java.util.HashSet;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        int count = 0;
        HashSet<Character> set = new HashSet<>();
        int i = 0, j = 0;

        while (i < n && j < n) {
            if (!set.contains(s.charAt(j))) {
                set.add(s.charAt(j++));
                count = Math.max(count, j - i);
            } else {
                set.remove(s.charAt(i++));
            }
        }

        return count;
    }
}

```
## [2260. Minimum Consecutive Cards to Pick Up](https://leetcode.com/problems/minimum-consecutive-cards-to-pick-up/)
Below will give correct answer but result in time exceed
```java
import java.util.HashSet;
class Solution {
    public int minimumCardPickup(int[] cards) {
        int count = 0;
        int min=100000;
        HashSet<Integer> N = new HashSet<>();
        int i = 0;
        while (i < cards.length) {
            int  j = cards.length-1;
            while(i<j){
                if(cards[i]==cards[j]&&j-i+1<min){
                    min=j-i+1;
                    count=min;
                }
                j--;
            }
            i++;
        }
        return (count > 0) ? count : -1;  // Return the count or -1 if no valid pickup
    }
}
```

```java

```
## [1695. Maximum Erasure Value](https://leetcode.com/problems/maximum-erasure-value/)
```java
 public int maximumUniqueSubarray(int[] nums) {
        int max = Integer.MIN_VALUE, l = 0, curSum = 0;
        int memo[] = new int[10001];
        for(int n: nums){
            while(memo[n] == 1){
                memo[nums[l]]--;
                curSum -= nums[l];
                l++;
            }
            curSum += n;
            memo[n]++;
            max = Math.max(max, curSum);
        }
        return max;
    }
```

```java
class Solution {

    public int maximumUniqueSubarray(int[] nums) {

        HashSet<Integer> N=new HashSet<>();

        int i = 0, j = 0;

        int count = 0;

        while (i < nums.length) {

            if (!N.contains(nums[i])) {

                N.add(nums[i]);

                count += nums[i++];

                continue;

            }

            i++;

        }

        return count;

    }

}
```
## [697. Degree of an Array](https://leetcode.com/problems/degree-of-an-array/)
 Optimized Code
 ```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int findShortestSubArray(int[] nums) {
        HashMap<Integer, Integer> frequencyMap = new HashMap<>();
        HashMap<Integer, Integer> firstIndexMap = new HashMap<>();
        HashMap<Integer, Integer> lastIndexMap = new HashMap<>();
        int degree = 0;
        for (int i = 0; i < nums.length; i++) {
            int num = nums[i];
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
            degree = Math.max(degree, frequencyMap.get(num));
            if (!firstIndexMap.containsKey(num)) {
                firstIndexMap.put(num, i);
            }
            lastIndexMap.put(num, i);
        }
        int minLength = nums.length;
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            int num = entry.getKey();
            if (entry.getValue() == degree) {
                int length = lastIndexMap.get(num) - firstIndexMap.get(num) + 1;
                minLength = Math.min(minLength, length);
            }
        }
        return minLength;
    }
}
```
Own Approach
```java
class Solution {
    public int findShortestSubArray(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        int degree = 0;
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if (entry.getValue() > degree) {
                degree = entry.getValue();
            }
        }
        int result = Integer.MAX_VALUE;
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if (entry.getValue() == degree) {
                int n = entry.getKey();
                int k = 0, m = 0;
                for (int i = 0; i < nums.length; i++) {
                    if (nums[i] == n) {
                        k = i;
                        break;
                    }
                }
                for (int i = nums.length - 1; i >= 0; i--) {
                    if (nums[i] == n) {
                        m = i;
                        break;
                    }
                }        System.out.println(n);
                result = Math.min(result,Math.abs(m - k) + 1);
            }
        }
        return result;
    }
}
```
## [884. Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/)
```java
class Solution {
    public String[] uncommonFromSentences(String s1, String s2) {
        HashMap<String, Integer> wordCount = new HashMap<>();
                String combined = s1 + " " + s2;
        String[] words = combined.split(" ");
        for (String word : words) {
            wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
        }
        ArrayList<String> uncommonWords = new ArrayList<>();
        for (Map.Entry<String, Integer> entry : wordCount.entrySet()) {
            if (entry.getValue() == 1) {
                uncommonWords.add(entry.getKey());
            }
        }
        return uncommonWords.toArray(new String[0]);
    }
}
```
## [2094. Finding 3-Digit Even Numbers](https://leetcode.com/problems/finding-3-digit-even-numbers/)
```java
class Solution {
    public int[] findEvenNumbers(int[] digits) {
        HashSet<Integer> resultSet = new HashSet<>(); // To avoid duplicates

        int n = digits.length;
        for (int i = 0; i < n; i++) {
            if (digits[i] == 0) continue; // Skip leading zeros
            for (int j = 0; j < n; j++) {
                if (i == j) continue; // Avoid duplicate indices
                for (int k = 0; k < n; k++) {
                    if (i == k || j == k) continue; // Avoid duplicate indices
                    if (digits[k] % 2 == 0) { // Last digit must be even
                        int num = digits[i] * 100 + digits[j] * 10 + digits[k];
                        resultSet.add(num); // Add unique number
                    }
                }
            }
        }

        ArrayList<Integer> result = new ArrayList<>(resultSet);
        Collections.sort(result);

        int[] Result = new int[result.size()];
        for(int i = 0 ; i<result.size();i++)
            Result[i] = result.get(i);
        return Result;
    }
}
```
## [1189. Maximum Number of Balloons](https://leetcode.com/problems/maximum-number-of-balloons/)
```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int maxNumberOfBalloons(String text) {
        int N = 0;
        HashMap<String, Integer> m = new HashMap<>();
        m.put("a", 1);
        m.put("b", 1);
        m.put("l", 2);
        m.put("o", 2);
        m.put("n", 1);
        HashMap<String, Integer> n = new HashMap<>();
        for (char c : text.toCharArray()) {
            String key = String.valueOf(c);
            n.put(key, n.getOrDefault(key, 0) + 1);
        }
        boolean flag = true;
        while (flag) {
            for (Map.Entry<String, Integer> entry : m.entrySet()) {
                String key = entry.getKey();
                int required = entry.getValue();
                if (n.getOrDefault(key, 0) < required) {
                    flag = false;
                    break;
                }
                n.put(key, n.get(key) - required);
            }
            if (flag) {
                N++;
            }
        }
        return N;
    }
}
```
## [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
```java
class Solution {
    private boolean isAnagram(String s1,String s2,int len){
        int[] arr =  new int [26];
        for(int i = 0;i<len;i++){
            arr[s1.charAt(i)-'a']++;
            arr[s2.charAt(i)-'a']--;
        }
        for(int i = 0;i<26;i++){
            if(arr[i] >0)
                return false;
        }
        return true;
    }
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> index =  new ArrayList<>();
        int len = s.length();
        int pLen = p.length();
        for(int i = 0;i<=len-pLen;i++){
            String temp = s.substring(i,i+pLen);
            if(isAnagram(temp, p,pLen)){
                index.add(i);
            }
        }
        return index;
        }
    }
```
## [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)
```java
class Solution {

    public List<List<String>> groupAnagrams(String[] strs) {

        HashMap<String,List<String>> S = new HashMap<>();

        for(String s:strs){

            char[] charArray=s.toCharArray();

            Arrays.sort(charArray);

            String key = new String(charArray);

            if(!S.containsKey(key)){

                S.put(key,new ArrayList<>());

            }

            S.get(key).add(s);

        }

        return new ArrayList<>(S.values());

    }

}
```
## [1282. Group the People Given the Group Size They Belong To](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/)

```java
class Solution {
    public List<List<Integer>> groupThePeople(int[] groupSizes) {
        List<List<Integer>> result = new ArrayList<>();
        HashSet<Integer> Duplicate = new HashSet<>();
         for(int i = 0; i < groupSizes.length; i++) {
            if(!Duplicate.contains(groupSizes[i])){
                Duplicate.add(groupSizes[i]);
                List<Integer> freq= new ArrayList<>();
                for(int j=0;j<groupSizes.length;j++){
                    if((groupSizes[i]==groupSizes[j])&&(freq.size()<=groupSizes[i])){
                        freq.add(j);
                    }
                    if (freq.size() == groupSizes[i]) {
                        result.add(new ArrayList<>(freq));
                        freq.clear();
                    }
                }
            }
        }
        return result;
    }
}
```
## [229. Majority Element II](https://leetcode.com/problems/majority-element-ii/)
```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> numbers=new ArrayList<>();
        int n=nums.length/3;
        HashMap<Integer,Integer> num=new HashMap<>();
        for(int N:nums){
            num.put(N,num.getOrDefault(N,0)+1);
        }
        int c=0;
        for(int N:nums){
            if(num.get(N)>n&&!numbers.contains(N)){
                numbers.add(N);
            }
        }
        return numbers;
    }
}
```
## [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
    int count=0,sum=0;
    HashMap<Integer,Integer> num= new HashMap<>();
    num.put(0,1);
    for(int n:nums){
        sum+=n;
        int diff=sum-k;
        if(num.containsKey(diff)){
            count+=num.get(diff);
        }
        num.put(sum,num.getOrDefault(sum,0)+1);
    }
    return count;
    }
}
```

## [2442. Count Number of Distinct Integers After Reverse Operations](https://leetcode.com/problems/count-number-of-distinct-integers-after-reverse-operations/)
```java
class Solution {
    public int countDistinctIntegers(int[] nums) {
        Set<Integer> distinctIntegers = new HashSet<>();
        for (int num : nums) {
            distinctIntegers.add(num);
            int reverseNum = Integer.parseInt(new StringBuilder().append(num).reverse().toString());
            distinctIntegers.add(reverseNum);
        }
        return distinctIntegers.size();
    }
}
```

```java
class Solution {
    public int countDistinctIntegers(int[] nums) {
        List<Integer> result = new ArrayList<>();
        int count=0;
        for(int i=0;i<nums.length;i++){
            result.add(nums[i]);
        }
         for(int i=0;i<nums.length;i++){
            result.add(reverse(nums[i]));
        }
        Set<Integer> r = new HashSet<>();
        for(int n:result){
                r.add(n);
                count++;
            }
        return count;
    }
    int reverse(int num){
        int i=0;
        while(num>0){
            int temp=num%10;
            i=i*10+temp;
            num/=10;
        }
        return i;
    }
}
```
## [974. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
```java
  class Solution {
    public int subarraysDivByK(int[] nums, int k) {
    int count=0,sum=0;
    HashMap<Integer,Integer> num= new HashMap<>();
    num.put(0,1);
    for(int n:nums){
        sum+=n;
        int rem=(sum % k + k) % k;
        if(num.containsKey(rem)){
            count+=num.get(rem);
        }
        num.put(rem,num.getOrDefault(rem,0)+1);
    }
    return count;
    }
}
```

## [2001. Number of Pairs of Interchangeable Rectangles](https://leetcode.com/problems/number-of-pairs-of-interchangeable-rectangles/)
```java
class Solution {
    public long interchangeableRectangles(int[][] rectangles) {
        long res=0;
        HashMap<Double,Integer> map= new HashMap<>();
        for(int i=0;i<rectangles.length;i++){
            double ratio = (double)rectangles[i][0]/rectangles[i][1];
            res+=map.getOrDefault(ratio,0);
            map.put(ratio,map.getOrDefault(ratio,0)+1);
        }
        return res;
    }
}
```
## [791. Custom Sort String](https://leetcode.com/problems/custom-sort-string/)
```java
class Solution {
    public String customSortString(String order, String s) {
        HashMap<Character,Integer> Freq = new HashMap<>();
        for(char c:s.toCharArray()){
            Freq.put(c,Freq.getOrDefault(c,0)+1);
        }
        StringBuilder S = new StringBuilder();
        for(char c:order.toCharArray()){
            if(Freq.containsKey(c)){
                int count=Freq.get(c);
                for(int i=0;i<count;i++){
                     S.append(c);
                }
                Freq.remove(c);
            }
        }
       for (Map.Entry<Character, Integer> entry : Freq.entrySet()) {
            char c = entry.getKey();
            int count = entry.getValue();
            for (int i = 0; i < count; i++) {
                S.append(c);
            }
        }
        return S.toString();
    }
}
```
## [273. Integer to English Words](https://leetcode.com/problems/integer-to-english-words/)
```java
class Solution {
           static HashMap<Integer, String> Ones = new HashMap<>() {
        {
            put(1, "One");
            put(2, "Two");
            put(3, "Three");
            put(4, "Four");
            put(5, "Five");
            put(6, "Six");
            put(7, "Seven");
            put(8, "Eight");
            put(9, "Nine");
            put(12, "Twelve");
            put(13, "Thirteen");
            put(14, "Fourteen");
            put(15, "Fifteen");
            put(16, "Sixteen");
            put(17, "Seventeen");
            put(18, "Eighteen");
            put(19, "Nineteen");
            put(11, "Eleven");
            put(10, "Ten");
        }
    };
  
    static HashMap<Integer, String> Tens = new HashMap<>() {
        {
            put(20, "Twenty");
            put(30, "Thirty");
            put(40, "Forty");
            put(50, "Fifty");
            put(60, "Sixty");
            put(70, "Seventy");
            put(80, "Eighty");
            put(90, "Ninety");
        }
    };
    
     public String numberToWords(int num) {
        StringBuilder s = new StringBuilder();
        if (num == 0) {
            return "Zero";
        }

        String Part="";
        String[] post = {"", " Thousand", " Million", " Billion"};
        int i=0;
        while (num != 0) {
            int N = num % 1000;
            String s1 = getstring(N);
            if(N!=0){
                if (!s1.isEmpty()) {
                  s.append(s1).append(post[i]).append(" ").append(Part);
                }else{
                    s.append(s1).append(post[i]);
                }
                Part=s.toString().trim();
                s.delete(0,s.length());
            }
            num /= 1000;
            i++;
        }
        return Part;
    }

    private static String getstring(int num) {
        StringBuilder s = new StringBuilder();
        int last_2=num%100;
        int hundren=num/100;
        if(hundren>0){
            s.append(Ones.get(hundren)).append(" Hundred");
        }
        if(last_2<20 && last_2>0){
            if(hundren>0) s.append(" ");
            s.append(Ones.get(last_2));
        }
        if(last_2>=20){
            int l=last_2/10;
            if(hundren>0) s.append(" ");
            s.append(Tens.get(l*10));
            if(last_2%10!=0) {
                if(l!=0) s.append(" ");
                s.append(Ones.get(last_2 % 10));
            }
        }
        return s.toString();
    }
}
```
# Stack
## [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
```java 
///using Stack And HashMap
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int n1=nums1.length;
        int n2 =  nums2.length;
        int[] res = new int[n1];
        HashMap<Integer,Integer> map = new HashMap<>();
        Stack<Integer> stack = new Stack();
        for(int i=0;i<n2;i++){
            while(!stack.empty()&&nums2[i]>stack.peek()){
                map.put(stack.pop(),nums2[i]);
            stack.push(nums2[i]);
        }
        for(int i=0;i<n1;i++){
            res[i]=map.getOrDefault(nums1[i],-1);
        }
        return res;
    }
}
```

```java 
//using Dequeu(Interface) and HashMap
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int n1=nums1.length;
        int n2 =  nums2.length;
        int[] res = new int[n1];
        HashMap<Integer,Integer> map = new HashMap<>();
        Deque<Integer> stack = new ArrayDeque<>();
        for(int i=0;i<n2;i++){
            while(!stack.isEmpty()&&nums2[i]>stack.peek()){
                map.put(stack.pop(),nums2[i]);
            }
            stack.push(nums2[i]);
        }
        for(int i=0;i<n1;i++){
            res[i]=map.getOrDefault(nums1[i],-1);
        }
        return res;
    }
}
```
## [503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)
```java
class Solution {
        public int[] nextGreaterElements(int[] nums) {
            int n=nums.length;
            int[] res = new int[n];
            Arrays.fill(res,-1);
            Stack<Integer> stack = new Stack();
            for(int i=0;i<2*n;i++){
                while(!stack.empty()&&nums[i%n]>nums[stack.peek()]){
                    res[stack.pop()]=nums[i%n];
                }
                stack.push(i%n);
            }
            return res;
        }
    }
```
## [739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int n=temperatures.length;
            int[] res = new int[n];
            Arrays.fill(res,0);
            Stack<Integer> stack = new Stack();
            for(int i=0;i<n;i++){
                while(!stack.empty()&&temperatures[i]>temperatures[stack.peek()]){
                    int index = stack.pop();
                    res[index]=i-index;
                }
                stack.push(i);
            }
            return res;
    }
}
```

## [1673. Find the Most Competitive Subsequence](https://leetcode.com/problems/find-the-most-competitive-subsequence/)
```java
class Solution {
    public int[] mostCompetitive(int[] nums, int k) {
        Stack<Integer> stack = new Stack<>();
        for (int i = 0; i < nums.length; i++) {
            int n = nums[i];
            while (!stack.isEmpty() && stack.peek() > n && stack.size() + (nums.length - i) > k) {
                stack.pop();
            }
            if (stack.size() < k) {
                stack.push(n);
            }
        }
        int[] result = new int[k];
        for (int i = k - 1; i >= 0; i--) {
            result[i] = stack.pop();
        }
        return result;
    }
}
```
## [227. Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/)
```java
import java.util.Stack;

class Solution {
    public int calculate(String s) {
        s = s.replaceAll("\\s+", "");  // Remove all spaces
        Stack<Integer> s1 = new Stack<>();  // Stack for numbers
        Stack<Character> s2 = new Stack<>();  // Stack for operators
        int num = 0;  // To handle multi-digit numbers
        char sign = '+';  // Track current operator, initialize with '+'

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            // Build the number if it's a digit
            if (Character.isDigit(ch)) {
                num = num * 10 + (ch - '0');  // For multi-digit numbers
            }

            // If it's an operator or we're at the last character, calculate based on current operator
            if (!Character.isDigit(ch) || i == s.length() - 1) {
                switch (sign) {
                    case '+':
                        s1.push(num);  // Add the current number to the stack
                        break;
                    case '-':
                        s1.push(-num);  // Subtract the current number by pushing its negative
                        break;
                    case '*':
                        s1.push(s1.pop() * num);  // Multiply the top of the stack
                        break;
                    case '/':
                        s1.push(s1.pop() / num);  // Divide the top of the stack
                        break;
                }
                sign = ch;  // Update the current operator
                num = 0;  // Reset number
            }
        }

        // Sum up all the numbers in the stack
        int result = 0;
        while (!s1.isEmpty()) {
            result += s1.pop();
        }

        return result;
    }
}
```
## [402. Remove K Digits](https://leetcode.com/problems/remove-k-digits/)

**Here StringBuilder is Act as Stack** 
```java
class Solution {
    public String removeKdigits(String num, int k) {
        int n = num.length();
        if (k == n) {
            return "0"; 
        }
        StringBuilder stack = new StringBuilder();
        for (int i = 0; i < n; i++) {
            char currentDigit = num.charAt(i);
            while (k > 0 && stack.length() > 0 && stack.charAt(stack.length() - 1) > currentDigit) {
                stack.deleteCharAt(stack.length() - 1); 
                k--;
            }
            stack.append(currentDigit);
        }
        while (k > 0) {
            stack.deleteCharAt(stack.length() - 1);
            k--;
        }
        while (stack.length() > 0 && stack.charAt(0) == '0') {
            stack.deleteCharAt(0);
        }
        return stack.length() == 0 ? "0" : stack.toString();
    }
}
```
## [84. Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
```java
class Solution {
    public int largestRectangleArea(int[] heights) {
        int maxArea = 0;
        Stack<Integer> stack = new Stack();
        for (int i = 0; i <= heights.length; i++) {
            int height = (i == heights.length) ? 0 : heights[i];
            while(!stack.isEmpty() && height<heights[stack.peek()]){
                int h = heights[stack.pop()];
                int w = stack.isEmpty()?i:i-stack.peek()-1;
                maxArea = Math.max(maxArea, h * w);
            }
            stack.push(i);
        }  
        return maxArea;
    }
}
```
# Sorting
## [912. Sort an Array](https://leetcode.com/problems/sort-an-array/)
```java
class Solution {
    public int[] sortArray(int[] nums) {
        mergeSort(nums, 0, nums.length-1);
        return nums;
    }
    public void mergeSort(int []arr, int low, int high){
        if(low >= high) return;

        int mid = (low+high)/2;
        mergeSort(arr, low, mid);
        mergeSort(arr, mid+1, high);
        merge(arr, low, high, mid);
    }
    public void merge(int []arr, int low, int high, int mid){
        ArrayList<Integer> temp = new ArrayList<>();
        int left = low;
        int right = mid+1;

        while(left <= mid && right <= high){
            if(arr[left] <= arr[right]){
                temp.add(arr[left]);
                left++;
            }else{
                temp.add(arr[right]);
                right++;
            }
        }
        while(left <= mid){
            temp.add(arr[left]);
            left++;
        }
        while(right <= high){
            temp.add(arr[right]);
            right++;
        }
        for(int i=low; i<= high; i++){
            arr[i] = temp.get(i-low);
        }
    }
}

```

# Merge Sort
## ** [493. Reverse Pairs](https://leetcode.com/problems/reverse-pairs/)
```java
public class Solution {

    // Main function to find the total number of reverse pairs in the array
    public int reversePairs(int[] nums) {
        int n = nums.length; // Get the length of the array
        // Start the merge sort process which will sort the array and count reverse pairs
        return mergeSort(nums, 0, n - 1);
    }

    // Recursive merge sort function to split the array and count reverse pairs
    private int mergeSort(int nums[], int left, int right) {
        // Base case: when left index is not less than right, no further splitting is needed
        if (left >= right) {
            return 0; // No pairs to count
        }

        int count = 0; // Initialize reverse pair count
        int mid = (left + right) / 2; // Find the middle index

        // Recursively split the left half of the array
        count += mergeSort(nums, left, mid);
        // Recursively split the right half of the array
        count += mergeSort(nums, mid + 1, right);
        // Count and merge the split arrays
        count += merger(nums, left, mid, right);

        return count; // Return the total count of reverse pairs
    }

    // Function to merge two sorted halves and count reverse pairs
    private int merger(int nums[], int left, int mid, int right) {
        int j = mid + 1; // Start index for the right half
        int pc = 0; // Pair count

        // Count reverse pairs where nums[i] > 2 * nums[j]
        for (int i = left; i <= mid; i++) { // Traverse the left subarray
            // Move j while the reverse pair condition is met
            while (j <= right && nums[i] > (long) 2 * nums[j]) j++;
            pc += j - (mid + 1); // Count valid j values for each i
        }

        // Merge the two sorted halves into a temporary list
        List<Integer> ans = new ArrayList<>();
        int l = left, r = mid + 1; // l is the start of the left half, r is the start of the right half

        // Merge process: Compare elements from left and right subarrays and add them to the list
        while (l <= mid && r <= right) {
            if (nums[l] <= nums[r]) {
                ans.add(nums[l++]); // Add the smaller element from the left half
            } else {
                ans.add(nums[r++]); // Add the smaller element from the right half
            }
        }

        // Add remaining elements from the left subarray, if any
        while (l <= mid) {
            ans.add(nums[l++]);
        }

        // Add remaining elements from the right subarray, if any
        while (r <= right) {
            ans.add(nums[r++]);
        }

        // Copy the merged sorted elements back to the original array
        for (int i = left; i <= right; i++) {
            nums[i] = ans.get(i - left);
        }

        return pc; // Return the count of reverse pairs found in this merge
    }

}
```
# Two-Pointer Approach
## [15. 3Sum](https://leetcode.com/problems/3sum/)
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result =  new ArrayList<>();
        for(int i = 0;i<nums.length-2;i++){
            int left = i+1;
            int right = nums.length-1;
            if(i>0 && nums[i] == nums[i-1])
                continue;
            while(left<right){
                int n = nums[left] + nums[right] + nums[i];
                if(n<0)
                    left++;
                else if(n>0)
                    right--;
                else{
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    while(left<right && nums[left] == nums[left+1])
                        left++;
                    while(left<right && nums[right] == nums[right-1])
                        right--;
                    left++;
                    right--;
                }
            }
        }
        return result;
    }
}
```**
## ** [75. Sort Colors](https://leetcode.com/problems/sort-colors/)
```java
class Solution {
    public void sortColors(int[] nums) {
        int c1=0,c2=0,c3=0,n=nums.length;
        for(int i=0;i<n;i++){
            c1=nums[i]==0?c1+1:c1;
            c2=nums[i]==1?c2+1:c2;
        }
        int k=0;
       while(k<c1){
            nums[k++]=0;
        }
       while(k<c1+c2){
            nums[k++]=1;
        }
       while(k<n){
            nums[k++]=2;
        }
    }
}
```

```java
//two Pointer Approach
class Solution {
    public void sortColors(int[] nums) {
        int n=nums.length;
       int l=0,r=n-1,i=0;
       while(i<=r){
            if(nums[i]==0){
                int temp = nums[i];
                nums[i]=nums[l];
                nums[l] = temp;
                l++;
                i++;
            }
            else if(nums[i]==1)
                i++;
            else{
                 int temp = nums[i];
                nums[i]=nums[r];
                nums[r] = temp;
                r--;
            }
       }
    }
}
```
## [11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
```java
class Solution {
    public int maxArea(int[] height) {
        int n =  height.length,ans=0;
        int l = 0, r = n-1;
        while(l<r){
            if(height[l]<height[r]){
                ans = Math.max((r-l)*height[l],ans);
                l++;
            }
            else{
                ans = Math.max((r-l)*height[r],ans);
                r--;
            }
        }
        return ans;
    }
}
```
## [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
## [2149. Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/)
```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int[] result = new int[nums.length];
        int l = 0,r=1;
        for(int num : nums){
            if(num>0 && l < result.length-1){
                result[l] = num;
                l+=2;
            }
            if(num<0 && r < result.length){
                result[r] = num;
                r+=2;
            }
        }
        return result;
    }
}
```
## [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)
	
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int m = s.length();
        int n = t.length();
        int i=0,j=0;
        for(i=0,j=0;i<n;i++){
            if(j<m && s.charAt(j)==t.charAt(i))
                j++;
        }
        return j==m;
    }
}
```
# Sliding Window
```java
class Solution {
    private boolean isPermutation(char[] s1Freq, char[] windowFreq) {
        for (int i = 0; i < 26; i++) {
            if (s1Freq[i] != windowFreq[i]) {
                return false;
            }
        }
        return true;
    }

    public boolean checkInclusion(String s1, String s2) {
        if (s1.length() > s2.length()) {
            return false;
        }

        // Frequency arrays for s1 and the sliding window of s2
        char[] s1Freq = new char[26];  // Frequency array for s1
        char[] windowFreq = new char[26];  // Frequency array for current window in s2

        // Fill the frequency array for s1 and the first window in s2
        for (int i = 0; i < s1.length(); i++) {
            s1Freq[s1.charAt(i) - 'a']++;
            windowFreq[s2.charAt(i) - 'a']++;
        }

        // Slide the window over s2
        for (int i = s1.length(); i < s2.length(); i++) {
            if (isPermutation(s1Freq, windowFreq)) {
                return true;  // Return true if the frequencies match
            }
            // Add the next character to the window and remove the first character
            windowFreq[s2.charAt(i) - 'a']++;
            windowFreq[s2.charAt(i - s1.length()) - 'a']--;
        }

        // Check the last window
        return isPermutation(s1Freq, windowFreq);
    }
}
```
# Dynamic Programming

**Memoization +(Recursion (Or) Iteration) = DP**\
## [1137. N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)
```java
class Solution {
    public int tribonacci(int n) {
        if(n == 0)
            return 0;
        if(n == 1 || n == 2)
            return 1;
        int[] dp = new int[n+1];
        dp[0] = 0;
        dp[1] = 1;
        dp[2] = 1;
        for(int i = 3 ; i<=n;i++){
            dp[i] = dp[i-1] + dp[i-2] + dp[i-3];
        }
        return dp[n];
    }
}
```
## [338. Counting Bits](https://leetcode.com/problems/counting-bits/)
```java
class Solution {
    public int[] countBits(int n) {
        int[] ans = new int[n+1];
        ans[0] = 0;
        for(int i = 1; i<=n;i++){
            ans[i] = ans[i/2] + (i & 1);
        }
        return ans;
    }
}
```
## [509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)
```java
//Normal Method,its performance is low and leads to overlapping so we go for DP.but it also give o/p
class Solution {
    public int fib(int n) {
        if(n<=1)
            return n;
        return fib(n-1)+fib(n-2);
    }
}
```

```java
//using Dynamic Programming
//TC:O(n)
//SC:O(n)
class Solution {
    int[] dp = new int[31];
    public int fib(int n) {
        if(n<=1)
            return n;
        if(dp[n]!=0)
            return dp[n];
        return dp[n]=fib(n-1)+fib(n-2);
    }
}
```

```java
//TC:O(n)
//SC:O(1)
class Solution {
    public int fib(int n) {
        if(n<=1)
            return n;
        int prev=0,curr=1,next=0,i=1;
        while(i<n){
            next=prev+curr;
            prev=curr;
            curr=next;
            i++;
        }
        return next;
    }
}
```
## [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
```java
class Solution {
    int[] dp =  new int[46];
    public int climbStairs(int n) {
         if(n==1||n==2)
            return n;
        if(dp[n]!=0)
            return dp[n];
        return dp[n]=climbStairs(n-1)+climbStairs(n-2);
    }
}
```
## [198. House Robber](https://leetcode.com/problems/house-robber/)
DP by Iteration
```java
//Memoization + iteration = DP
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if(n == 1) return nums[0];
        int[] dp = new int[n];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);

        for(int i=2; i<n; i++){
            dp[i] = Math.max(dp[i-1] , nums[i] + dp[i-2]);
        }

        return dp[n-1];
    }
}
```
### Explanation
Let's go through the given example `[100, 3, 5, 200, 6, 300]` step-by-step, explaining each decision during the dynamic programming (DP) iteration process. The goal is to determine the maximum amount of money that can be robbed without robbing two consecutive houses.

#### Problem Understanding:
Given the array `[100, 3, 5, 200, 6, 300]`, each element represents the amount of money in each house. You cannot rob two adjacent houses because of the security system, so we need to find a strategy to maximize the total amount robbed.

#### Step-by-Step Code Explanation:

1. **Initialization:**
   ```java
   int n = nums.length;
   if (n == 1) return nums[0];
   ```
   - `n` is the number of houses, which is `6` in this example.
   - If there was only one house, you would simply rob that house. But since `n > 1`, we proceed to the next steps.

2. **Dynamic Programming Array Setup:**
   ```java
   int[] dp = new int[n];
   dp[0] = nums[0];
   dp[1] = Math.max(nums[0], nums[1]);
   ```
   - Create an array `dp` of size `n` to store the maximum amount of money that can be robbed up to each house.
   - `dp[0] = nums[0] = 100`: If you rob only the first house, the maximum money you get is `100`.
   - `dp[1] = Math.max(nums[0], nums[1]) = Math.max(100, 3) = 100`: Between the first and the second house, you can only rob one, so you choose the first house which has more money (`100`).

   Initial `dp` array: `[100, 100, 0, 0, 0, 0]`.

3. **Iterate through the rest of the houses:**
   ```java
   for (int i = 2; i < n; i++) {
       dp[i] = Math.max(dp[i - 1], nums[i] + dp[i - 2]);
   }
   ```
   - Starting from the third house, you decide whether to rob it or skip it based on the previous decisions stored in the `dp` array.

4. **Detailed Iteration and Decisions:**

   - **For `i = 2` (House 3 with `5`):**
     ```java
     dp[2] = Math.max(dp[1], nums[2] + dp[0]);
     dp[2] = Math.max(100, 5 + 100) = Math.max(100, 105) = 105;
     ```
     - **Explanation**:
       - **Option 1**: Skip House 3 and take the maximum money robbed up to House 2 (`dp[1] = 100`).
       - **Option 2**: Rob House 3 (`5`) and add it to the maximum money robbed up to House 1 (`dp[0] = 100`), giving a total of `105`.
       - **Decision**: Robbing House 3 and adding to House 1 yields a higher total (`105`), so we update `dp[2] = 105`.

     Updated `dp` array: `[100, 100, 105, 0, 0, 0]`.

   - **For `i = 3` (House 4 with `200`):**
     ```java
     dp[3] = Math.max(dp[2], nums[3] + dp[1]);
     dp[3] = Math.max(105, 200 + 100) = Math.max(105, 300) = 300;
     ```
     - **Explanation**:
       - **Option 1**: Skip House 4 and take the maximum money robbed up to House 3 (`dp[2] = 105`).
       - **Option 2**: Rob House 4 (`200`) and add it to the maximum money robbed up to House 2 (`dp[1] = 100`), giving a total of `300`.
       - **Decision**: Robbing House 4 and adding to House 2 yields a higher total (`300`), so we update `dp[3] = 300`.

     Updated `dp` array: `[100, 100, 105, 300, 0, 0]`.

   - **For `i = 4` (House 5 with `6`):**
     ```java
     dp[4] = Math.max(dp[3], nums[4] + dp[2]);
     dp[4] = Math.max(300, 6 + 105) = Math.max(300, 111) = 300;
     ```
     - **Explanation**:
       - **Option 1**: Skip House 5 and take the maximum money robbed up to House 4 (`dp[3] = 300`).
       - **Option 2**: Rob House 5 (`6`) and add it to the maximum money robbed up to House 3 (`dp[2] = 105`), giving a total of `111`.
       - **Decision**: Robbing House 5 does not provide a better outcome compared to just keeping the total from House 4 (`300`), so we keep `dp[4] = 300`.

     Updated `dp` array: `[100, 100, 105, 300, 300, 0]`.

   - **For `i = 5` (House 6 with `300`):**
     ```java
     dp[5] = Math.max(dp[4], nums[5] + dp[3]);
     dp[5] = Math.max(300, 300 + 300) = Math.max(300, 600) = 600;
     ```
     - **Explanation**:
       - **Option 1**: Skip House 6 and take the maximum money robbed up to House 5 (`dp[4] = 300`).
       - **Option 2**: Rob House 6 (`300`) and add it to the maximum money robbed up to House 4 (`dp[3] = 300`), giving a total of `600`.
       - **Decision**: Robbing House 6 and adding to House 4 yields a higher total (`600`), so we update `dp[5] = 600`.

     Final `dp` array: `[100, 100, 105, 300, 300, 600]`.

5. **Return the Result:**
   ```java
   return dp[n - 1];
   ```
   - The maximum amount of money that can be robbed is `dp[5] = 600`.

#### Conclusion:
- The optimal strategy for the given array `[100, 3, 5, 200, 6, 300]` involves robbing the houses with values `100, 200, and 300`, skipping adjacent ones where necessary.
- The total money robbed is `100 + 200 + 300 = 600`. 

This approach carefully balances the decision to rob or skip each house to maximize the total amount stolen while adhering to the constraint of not robbing two consecutive houses.
 DP by Recursion
 ```java
 //Memoization + Recursion = DP
class Solution {
    int[] dp;
    public int rob(int[] nums) {
        int n = nums.length;
        dp = new int[n];
        Arrays.fill(dp,-1);
        return robb(nums,0,n);
    }
    private int robb(int[] nums,int i,int n){
        if(i>=n)
            return 0;
        if(dp[i]!=-1)
            return dp[i];
        return dp[i]=Math.max(robb(nums,i+1,n),(robb(nums,i+2,n)+nums[i]));
    }
}
```
## [213. House Robber II](https://leetcode.com/problems/house-robber-ii/)

DP by Iteration same as in HR1 I
```java
   class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if(n == 1) return nums[0];
        if(n == 2) return Math.max(nums[0],nums[1]);
        int[] dp = new int[n-1];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        for(int i=2; i<n-1; i++){
            dp[i] = Math.max(dp[i-1] , dp[i-2]+nums[i]);
        }
        int ans1=  dp[n-2];

       int[] dp1 = new int[n-1];
        dp1[0] = nums[1];
        dp1[1] = Math.max(nums[1], nums[2]);

        for(int i=2; i<n-1; i++){
            dp1[i] = Math.max(dp1[i-1] , dp1[i-2]+nums[i+1]);
        }
        int ans2=  dp1[n-2];
        return Math.max(ans1,ans2);
    }
}
```
## [62. Unique Paths](https://leetcode.com/problems/unique-paths/)

```java
class Solution {
    int dp[][];
    public int uniquePaths(int m, int n) {
        dp = new int[m][n];
        for(int i[]:dp)
            Arrays.fill(i,-1);
        return up(m,n,0,0);
    }
    private int up(int m,int n,int i,int j){
        if(i >= m || j >= n)
            return 0;
        if(i == m-1 && j == n-1)
            return 1;
        if(dp[i][j] != -1)
            return dp[i][j];
        return dp[i][j] = up(m,n,i+1,j)+up(m,n,i,j+1);
    }
}
```

```java
class Solution {
    int dp[][];
    public int uniquePaths(int m, int n) {
        dp = new int[m][n];
        for(int i[]:dp)
            Arrays.fill(i,1);
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j] = dp[i][j-1] + dp[i-1][j];
            }
        }
        return dp[m-1][n-1];
}
}
```
## [63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)
```java
class Solution {
    int dp[][];
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length,n = obstacleGrid[0].length;
         dp = new int[m][n];
        for(int i[]:dp)
            Arrays.fill(i,-1);
        return up(obstacleGrid,m,n,0,0);
    }
    private int up(int[][] obstacleGrid ,int m,int n,int i,int j){
        if(i >= m || j >= n)
            return 0;
        if(obstacleGrid[i][j]==1)
            return 0;
        if(i == m-1 && j == n-1)
            return 1;
        if(dp[i][j] != -1)
            return dp[i][j];
        return dp[i][j] = up(obstacleGrid ,m,n,i+1,j)+up(obstacleGrid ,m,n,i,j+1);
    }

}
```
## [1025. Divisor Game](https://leetcode.com/problems/divisor-game/)

```java
class Solution {
    public boolean divisorGame(int n) {
        int turn = 0; 
        int x;
        while (n > 1) {
            x = 1;
            while (n % x != 0 && x < n) {
                x++;
            }
            n -= x;
            turn = 1 - turn;
        }
        return turn == 1; 
    }
}
```

```java
class Solution {
    public boolean divisorGame(int n) {
        boolean[] dp = new boolean[n+1];
        for(int i = 2 ; i<=n;i++){
            for(int x = 1 ;x<i;x++){
                if(i%x==0 && !dp[i-x]){
                    dp[i]=true;
                    break;
                }
            }
        }
        return dp[n];
    }
}
```

```java
class Solution {
    public boolean divisorGame(int n) {
        return n%2==0;
    }
}
```
## [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)
```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int n = cost.length;
        int[] dp = new int[n];
        dp[0] = cost[0];
        dp[1] = cost[1];
        for (int i = 2; i < n; i++) {
            dp[i] = Math.min(dp[i - 1], dp[i - 2]) + cost[i];
        }
        return Math.min(dp[n - 1], dp[n - 2]);
    }
}
```
## [494. Target Sum](https://leetcode.com/problems/target-sum/)
```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        int sum = 0;
        for (int num : nums) {
            sum += num;
        }
        if (sum < Math.abs(target) || (sum + target) % 2 != 0) retur
        int[] dp = new int[subsetSum + 1];
        dp[0] = 1;
        for (int num : nums) {
            for (int j = subsetSum; j >= num; j--) {
                dp[j] += dp[j - num];
            }
        }
        return dp[subsetSum];
    }
}
```
## [416. Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)
```java
class Solution {
    public boolean canPartition(int[] nums) {
       int sum = 0;
       for (int num : nums) {
           sum += num;
       }
       if (sum % 2 != 0) {
           return false;
       }
       int target = sum / 2;
       boolean[] dp = new boolean[target + 1];
       dp[0] = true;
       for (int num : nums) {
           for (int j = target; j >= num; j--) {
               dp[j] = dp[j] || dp[j - num];
           }
       }
       return dp[target];
    }
}
```
## [647. Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)
```java
class Solution {
    public int countSubstrings(String s) {
        int n = s.length();
        boolean[][] dp = new boolean[n][n];
        int count = 0;
        for (int len = 1; len <= n; len++) {
            for (int i = 0; i <= n - len; i++) {
                int j = i + len - 1; 
                if (len == 1) {
                    dp[i][j] = true;
                } else if (len == 2) {
                    dp[i][j] = (s.charAt(i) == s.charAt(j));
                } else {
                    dp[i][j] = (s.charAt(i) == s.charAt(j)) && dp[i+1][j-1];
                }
                if (dp[i][j]) {
                    count++;
                }
            }
        }
        return count;
    }
}
```
## [474. Ones and Zeroes](https://leetcode.com/problems/ones-and-zeroes/)
**Below is a own approach .It will give Pass max testcase **
```java
class Solution {
    public static int countZeros(String str) {
        return str.length() - str.replace("0", "").length();
    }

    public int findMaxForm(String[] strs, int m, int n) {
        int max = 0;
        for (int i = 0; i < strs.length; i++) {
            int count = 1; 
            int M = m; 
            int N = n;
            int t = countZeros(strs[i]);
            int onesInCurrentString = strs[i].length() - t;
            M -= t;
            N -= onesInCurrentString;
            if (M < 0 || N < 0) {
                count = 0;
                continue;
            }
            for (int j = 0; j < strs.length; j++) {
                if (j == i) continue;
                int z = countZeros(strs[j]);
                int onesInNextString = strs[j].length() - z;
                if (M >= z && N >= onesInNextString) {
                    M -= z; 
                    N -= onesInNextString;
                    count++;
                }
            }
            max = Math.max(max, count); 
            if (max == strs.length) {
                return max;
            }
        }
        return max;
    }
}
```

```java
public class Solution {
    public int findMaxForm(String[] strs, int m, int n) {
        int[][] dp = new int[m + 1][n + 1];
        for (String s : strs) {
            int count0 = 0, count1 = 0;
            for (char c : s.toCharArray()) {
                if (c == '0') count0++;
                else count1++;
            }
            for (int i = m; i >= count0; i--) {
                for (int j = n; j >= count1; j--) {
                    dp[i][j] = Math.max(dp[i][j], 1 + dp[i - count0][j - count1]);
                }
            }
        }
        return dp[m][n];
    }
}
```
## [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
Without DP
```java
class Solution {
    public int maxSubArray(int[] nums) {
        // int[] dp = new int[nums.length];
        // dp[0] = nums[0];
        int currSum = nums[0];
        int maxSum = nums[0];
        for (int i = 1; i < nums.length; i++) {
            currSum = Math.max(nums[i], currSum + nums[i]);
            maxSum = Math.max(maxSum, currSum);
        }
        return maxSum;
    }
}
```

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        int maxSum = dp[0];
        for (int i = 1; i < nums.length; i++) {
            dp[i] = Math.max(nums[i], dp[i - 1] + nums[i]);
            maxSum = Math.max(maxSum, dp[i]);
        }
        return maxSum;
    }
}
```
## [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
without DP
```java
class Solution {
    public int maxProduct(int[] nums) {
        int currMax = nums[0];
        int currMin = nums[0];
        int maxProduct = nums[0];

        for (int i = 1; i < nums.length; i++) {
            int tempMax = currMax;  // store currMax before updating
            
            currMax = Math.max(nums[i], Math.max(currMax * nums[i], currMin * nums[i]));
            currMin = Math.min(nums[i], Math.min(tempMax * nums[i], currMin * nums[i]));
            
            maxProduct = Math.max(currMax, maxProduct);
        }
        return maxProduct;
    }
}
```

```java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        int[] dpMax = new int[n];
        int[] dpMin = new int[n];

        dpMax[0] = nums[0];
        dpMin[0] = nums[0];
        int maxProduct = nums[0];

        for (int i = 1; i < n; i++) {
            dpMax[i] = Math.max(nums[i], Math.max(dpMax[i - 1] * nums[i], dpMin[i - 1] * nums[i]));
            dpMin[i] = Math.min(nums[i], Math.min(dpMax[i - 1] * nums[i], dpMin[i - 1] * nums[i]));
            maxProduct = Math.max(maxProduct, dpMax[i]);
        }
        return maxProduct;
    }
}
```
## [1749. Maximum Absolute Sum of Any Subarray](https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/)


```java
class Solution {
    public int maxAbsoluteSum(int[] nums) {
        int maxSumEndingHere = nums[0];
        int minSumEndingHere = nums[0];
        int maxAbsoluteSum = Math.abs(nums[0]);
        for (int i = 1; i < nums.length; i++) {
            maxSumEndingHere = Math.max(nums[i], maxSumEndingHere + nums[i]);
            minSumEndingHere = Math.min(nums[i], minSumEndingHere + nums[i]);

            maxAbsoluteSum = Math.max(maxAbsoluteSum, Math.max(Math.abs(maxSumEndingHere), Math.abs(minSumEndingHere)));
        }

        return maxAbsoluteSum;
    }
}
```

```java
class Solution {
    public int maxAbsoluteSum(int[] nums) {
        int n = nums.length;
        int[] maxDp = new int[n];
        int[] minDp = new int[n];

        // Initialize with the first element
        maxDp[0] = nums[0];
        minDp[0] = nums[0];
        
        // Initialize the result with the absolute of the first element
        int maxAbsoluteSum = Math.abs(nums[0]);

        // Fill in the DP arrays
        for (int i = 1; i < n; i++) {
            maxDp[i] = Math.max(nums[i], maxDp[i - 1] + nums[i]);
            minDp[i] = Math.min(nums[i], minDp[i - 1] + nums[i]);
            
            // Update the maximum absolute sum by taking absolute values of both maxDp[i] and minDp[i]
            maxAbsoluteSum = Math.max(maxAbsoluteSum, Math.abs(maxDp[i]));
            maxAbsoluteSum = Math.max(maxAbsoluteSum, Math.abs(minDp[i]));
        }

        return maxAbsoluteSum;
    }
}
```
```java
class Solution {
    public int maxAbsoluteSum(int[] nums) {
        int sum = 0, min = 0, max = 0;

        for (int num : nums) {
            sum += num;
            min = Math.min(min, sum);
            max = Math.max(max, sum);
        }

        return max - min;        // min always <= 0, so 'max + Math.abs(min)' is the same        
    }
}
```
## [64. Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/)
```java
Tabulation
class Solution {
    public int minPathSum(int[][] grid) {
        int m = grid.length,n=grid[0].length;
        int[][] dp = new int[m][n];
        dp[0][0] = grid[0][0];
        for(int i = 0;i<m;i++){
            for(int j = 0;j<n;j++){
                if(i==0&&j==0)
                    continue;
                int temp = 0;
                if(i-1>=0 && j-1>=0){
                   temp = Math.min(dp[i-1][j],dp[i][j-1]);
                }
                else if(i-1>=0)
                    temp = dp[i-1][j];
                else if(j-1>=0)
                    temp = dp[i][j-1];
                dp[i][j] = grid[i][j]+temp;
            }
        }
        return dp[m-1][n-1];
    }
}
```

```java
Memoization
class Solution {
    public int minPathSum(int[][] grid) {
        int m = grid.length,n=grid[0].length;
        int[][] dp = new int[m][n];
        for (int[] row : dp) {
            Arrays.fill(row, -1);
        }
        return path(grid,dp,0,0,m,n);
    }
    private int path(int[][] grid,int[][] dp,int i,int j,int m,int n){
       if(i>=m || j>=n)
            return Integer.MAX_VALUE;
       if(dp[i][j] != -1)
            return dp[i][j];
       if(i==m-1 && j == n-1)
            return grid[i][j];
        
        return dp[i][j] = grid[i][j] + Math.min(path(grid,dp,i,j+1,m,n),path(grid,dp,i+1,j,m,n));
    }
}
```
## [55. Jump Game](https://leetcode.com/problems/jump-game/)
```java
class Solution {
    public boolean canJump(int[] nums) {
        if (nums.length == 1) 
            return true;
        boolean[] dp = new boolean[nums.length];
        dp[0] = true;
        for (int i = 0; i < nums.length; i++) {
            if (!dp[i]) 
                continue;
            int maxJump = nums[i] + i;
            for (int j = i + 1; j <= maxJump && j < nums.length; j++) {
                dp[j] = true;
                if (j == nums.length - 1) 
                    return true;
            }
        }
        return false;
    }
}
```
## [45. Jump Game II](https://leetcode.com/problems/jump-game-ii/)
```java
class Solution {
    public int jump(int[] nums) {
        if (nums.length == 1) 
            return 0;
        int[] dp = new int[nums.length];
        Arrays.fill(dp,Integer.MAX_VALUE);
        dp[0]=0;
        for (int i = 0; i < nums.length; i++) {
            if (dp[i]==Integer.MAX_VALUE) 
                continue;
            int maxJump = nums[i] + i;
            for (int j = i + 1; j <= maxJump && j < nums.length; j++) {
                dp[j] = Math.min(dp[i]+1,dp[j]);
            }
        }
        return dp[nums.length-1];
    }
}
```
## [1871. Jump Game VII](https://leetcode.com/problems/jump-game-vii/)(Using BFS Not DP)
```java
class Solution {
    public boolean canReach(String s, int minJump, int maxJump) {
        int n = s.length();
        if (s.charAt(n - 1) != '0') {
            return false;
        }
        boolean[] visited = new boolean[n]; 
        visited[0] = true;
        int farthest = 0;
        for (int i = 0; i < n; i++) {
            if (visited[i] && s.charAt(i) == '0') {
                for (int j = Math.max(i + minJump, farthest + 1); j <= Math.min(i + maxJump, n - 1); j++) {
                    if (s.charAt(j) == '0' && !visited[j]) {
                        visited[j] = true;
                        if (j == n - 1) 
                            return true;
                    }
                }
                farthest = i + maxJump;
            }
        }

        return false;  // If we exit the loop without reaching the end, return false
    }
}
```
## [1937. Maximum Number of Points with Cost](https://leetcode.com/problems/maximum-number-of-points-with-cost/)
Own Approach 
```java
class Solution {
    public long maxPoints(int[][] points) {
        int m = points.length, n = points[0].length;
        long[][] dp = new long[m][n];
        for (int c = 0; c < n; c++) {
            dp[0][c] = points[0][c];
        }
        for (int r = 1; r < m; r++) {
            for (int c = 0; c < n; c++) {
                long penalty = Long.MIN_VALUE; 
                for (int j = 0; j < n; j++) {
                    penalty = Math.max(penalty, dp[r - 1][j] - Math.abs(j - c));
                }
                dp[r][c] = points[r][c] + penalty;
            }
        }

        long result = 0;
        for (int j = 0; j < n; j++) {
            result = Math.max(result, dp[m - 1][j]);
        }
        return result;
    }
}
```
Below is an Efficient Way by Using Two-way Approach
```java
class Solution {
    public long maxPoints(int[][] points) {
        int m = points.length, n = points[0].length;
        long[][] dp = new long[m][n];
        for (int c = 0; c < n; c++) {
            dp[0][c] = points[0][c];
        }
        for (int r = 1; r < m; r++) {
            long[] left = new long[n];
            long[] right = new long[n];
            left[0] = dp[r - 1][0];
            for (int c = 1; c < n; c++) {
                left[c] = Math.max(left[c - 1] - 1, dp[r - 1][c]);
            }
            right[n - 1] = dp[r - 1][n - 1];
            for (int c = n - 2; c >= 0; c--) {
                right[c] = Math.max(right[c + 1] - 1, dp[r - 1][c]);
            }
            for (int c = 0; c < n; c++) {
                dp[r][c] = points[r][c] + Math.max(left[c], right[c]);
            }
        }
        long result = 0;
        for (int c = 0; c < n; c++) {
            result = Math.max(result, dp[m - 1][c]);
        }

        return result;
    }
}
	```
## [322. Coin Change](https://leetcode.com/problems/coin-change/)
```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, Integer.MAX_VALUE - 1);
        dp[0] = 0; 
        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
        return dp[amount] == Integer.MAX_VALUE - 1 ? -1 : dp[amount];
    }
}
```
## [1981. Minimize the Difference Between Target and Chosen Elements](https://leetcode.com/problems/minimize-the-difference-between-target-and-chosen-elements/)
```java
class Solution {
    public int minimizeTheDifference(int[][] mat, int target) {
        int m = mat.length, n = mat[0].length;
        boolean[] dp = new boolean[80001];
        dp[0] = true;
        for (int r = 0; r < m; r++) {
            boolean[] newDp = new boolean[80001];
            for (int sum = 0; sum <= 80000; sum++) {
                if (dp[sum]) {
                    for (int val : mat[r]) {
                        int newSum = sum + val;
                        if (newSum <= 80000) {
                            newDp[newSum] = true;
                        }
                    }
                }
            }
            dp = newDp;
        }
        int result = Integer.MAX_VALUE;
        for (int sum = 0; sum <= 80000; sum++) {
            if (dp[sum]) {
                result = Math.min(result, Math.abs(target - sum));
            }
        }
        return result;
    }
}
```

## [313. Super Ugly Number](https://leetcode.com/problems/super-ugly-number/)(DP & TreeSet)

**TreeSet Code lead toTLE so We go for Dp**

```java
class Solution {
    public int nthSuperUglyNumber(int n, int[] primes) {
         PriorityQueue<Long> uglynos = new PriorityQueue<>();
        HashSet<Long> seen =  new HashSet<>();
        seen.add(1L);
        uglynos.add(1L);
        long Ugly = 0;
        for(int i = 0 ; i< n;i++){
            Ugly = uglynos.poll();
            for(int prime : primes){
                long newUgly = prime * Ugly;
                if(!seen.contains(newUgly)){
                    uglynos.add(newUgly);
                    seen.add(newUgly);
                }
            }
        }
        return (int)Ugly;
    }
}
```

```java
class Solution {
    public int nthSuperUglyNumber(int n, int[] primes) {
        long[] dp = new long[n + 1];
        dp[1] = 1; 
        int numPrimes = primes.length;
        int[] indices = new int[numPrimes];
        long[] values = new long[numPrimes];

        for (int i = 0; i < numPrimes; i++) {
            indices[i] = 1;
            values[i] = primes[i];
        }

        for (int i = 2; i <= n; i++) {
            long minUgly = values[0];
            for (int j = 1; j < numPrimes; j++) {
                minUgly = Math.min(minUgly, values[j]);
            }
            dp[i] = minUgly;

            for (int j = 0; j < numPrimes; j++) {
                if (values[j] == minUgly) {
                    indices[j]++;
                    values[j] = dp[indices[j]] * primes[j];
                }
            }
        }

        return (int) dp[n];
    }
}
```

# Binary Search

## [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            // Check if mid is the target
            if (nums[mid] == target) {
                return mid;
            }

            // Determine which half is sorted
            if (nums[left] <= nums[mid]) { // Left half is sorted
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;  // Target is in the left half
                } else {
                    left = mid + 1;   // Target is in the right half
                }
            } else {  // Right half is sorted
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;   // Target is in the right half
                } else {
                    right = mid - 1;  // Target is in the left half
                }
            }
        }

        return -1;  // Target not found
    }
}
```
## [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length,n = matrix[0].length;
        int left = 0, right = m * n - 1;
        while(left <= right){
            int mid = (left+right)/2;
            int r = mid / n;//to find mid element row 
            int c = mid % n;//to find mid element column
            if(target == matrix[r][c])
                return true;
            else if(target>matrix[r][c])
                left = mid + 1;
            else
                right = mid - 1;
        }
        return false;
    }
}
```

## [240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int r = matrix.length-1;
        int c = 0;
        int cM = matrix[0].length;
        while(r>=0 && c<cM){
            if(target == matrix[r][c])
                return true;
            else if(target>matrix[r][c])
                c++;
            else
                r--;
        }
        return false;
    }
}
```
## [162. Find Peak Element](https://leetcode.com/problems/find-peak-element/)
```java
//normal
class Solution {
    public int findPeakElement(int[] nums) {
        int n=nums.length;
        for(int i=0;i<n-1;i++){
            if(nums[i]>nums[i+1])
                return i;
        }
        return n-1;
    }
}
```

```java
//using Binary search
class Solution {
    public int findPeakElement(int[] nums) {
       int l=0,r=nums.length-1;
       while(l<r){
        int mid = (l+r)/2;
        if(nums[mid]>nums[mid+1])
            r=mid;
        else
            l=mid+1;
       }
        return l;
    }
}
```
## [875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)
```java
//TLE (Own Method) another tye of brute force in notes

class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        Arrays.sort(piles);
        int n = piles.length, b = 0;
        int max = piles[n - 1];
        for (int i = max; i > 0; i--) {
            int h1 = 0;
            for (int j = 0; j < n; j++) {
                int temp = piles[j];
                // Correct calculation for hours needed at speed 'i'
                h1 += (int) Math.ceil((double) temp/i);// Ceiling division to count the full hours needed
            }
            if (h1 <= h) {
                b = i;
            }
        }
        return b;
    }

}
```

```java
//binary Search
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        Arrays.sort(piles);
        int n = piles.length;
        int r = piles[n - 1],l=0;
       while(l<r){
            int mid =  (l+r)/2;
            int h1=0;
            for (int i = 0; i < n; i++) {
                h1 += (int) Math.ceil((double) piles[i]/mid);
                if(h<h1)
                    break;
            }
            if (h1 <= h)
                r=mid;
            else
                l=mid+1;
       }
        return l;
    }
}
```
## [1482. Minimum Number of Days to Make m Bouquets](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/)
```java
//normal bruete force method
class Solution (
public int minDays(int[] bloomDay, int m, int k) (
	int n  = bloomDay.length;
	if(n <m*k) 
		return -1;
	for(int day = 1; day <= 1000000000; day++){
			int nfb, bc = 0;
		for(int 1 = 0; i < n; i++){
			if(bloomDay[1] <= day)
				nfb++;
			else 
				nfb = 0;
			if(nfb == k){
				++bc;
				nfb = 0;
			}
		}
		if(bc >= m) 
			return day;	
	}
	return -1;
	}
}
```

```java
//Using Binary Search
class Solution {
public int minDays(int[] bloomDay, int m, int k) {
    int n  = bloomDay.length;
    if(n <m*k)
        return -1;
    int left = 0 , right = bloomDay[0],minDays=-1
    for(int i : bloomDay){
        right = Math.max(i,right);
    }
    while(left<=right){
        int mid = (left+right)/2;
        if(bC(bloomDay,mid,k)>=m){
            minDays = mid;
            right=mid-1;
        }
        else
            left = mid+1;
    }
    return minDays;
    }
    int bC(int[] bloomDay,int currentDay,int k){
            int nfb=0, bc = 0;
        for(int i = 0; i < bloomDay.length; i++){
            if(bloomDay[i] <= currentDay)
                nfb++;
            else
                nfb = 0;
            if(nfb == k){
                ++bc;
                nfb = 0;
            }
        }
        return bc;
    }
}
```
## [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
# Binary Tree

## [700. Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode searchBST(TreeNode root, int val) {
        while(root != null && root.val != val){
            if(val<root.val)
                root = root.left;
            else
                root = root.right;
        }
        return root;
    }
}
```
## [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        dfs(res,root);
        return res;
    }
    private void dfs(List<Integer> res,TreeNode root){
        if(root == null)   
            return ;
        dfs(res,root.left);
        res.add(root.val);
        dfs(res,root.right);
    }
}
```

## [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        dfs(res,root);
        return res;
    }
    private void dfs(List<Integer> res,TreeNode root){
        if(root == null)   
            return ;
        res.add(root.val);
        dfs(res,root.left);
        dfs(res,root.right);
    }
}
```
## [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        dfs(res,root);
        return res;
    }
    private void dfs(List<Integer> res,TreeNode root){
        if(root == null)   
            return ;
        dfs(res,root.left);
        dfs(res,root.right);
        res.add(root.val);
        
    }
}
```

## [222. Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/)

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int countNodes(TreeNode root) {
        if(root == null)
            return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }
}
```
## ** [100. Same Tree](https://leetcode.com/problems/same-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p==null&&q==null)
            return true;
        if(p==null||q==null||p.val!=q.val)
            return false;
        return isSameTree(p.left,q.left) && isSameTree(p.right,q.right);
    }
}
```
## ** [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root ==  null)
            return true;
        return areMirror(root.left,root.right);
    }
    public boolean areMirror(TreeNode p, TreeNode q) {
        if(p==null&&q==null)
            return true;
        if(p==null||q==null||p.val!=q.val)
            return false;
        return areMirror(p.left,q.right) && areMirror(p.right,q.left);
    }
}
```
## [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root == null) return null;
        TreeNode temp;
        invertTree(root.left);
        invertTree(root.right);
        temp =root.left;
        root.left=root.right;
        root.right=temp;
        return root;
    }
}
```
## [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null)
            return 0;
        return Math.max(maxDepth(root.left),maxDepth(root.right))+1;
    }
}
```
## [872. Leaf-Similar Trees](https://leetcode.com/problems/leaf-similar-trees/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        List<Integer> res1 = new ArrayList<>();
        List<Integer> res2 = new ArrayList<>();
        dfs(root1,res1);
        dfs(root2,res2);
        return res1.equals(res2);
    }
    void dfs(TreeNode root, List<Integer> res){
        if(root == null)    return;
        if(root.left ==  null && root.right == null)
            res.add(root.val);
        dfs(root.left,res);
        dfs(root.right,res);
    }
}
```
## [111. Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int minDepth(TreeNode root) {
        if(root == null) return 0;
        int level = 1;
        Deque<TreeNode> q = new ArrayDeque();
        q.offer(root);
        while(!q.isEmpty()){
            int size = q.size();
            for(int i = 0 ; i < size ;i++){
                TreeNode curr = q.poll();
                if(curr.left == null && curr.right == null)
                    return level;
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            ++level;
        }
        return 0;
    }
}
```
## [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
       List<List<Integer>> res = new ArrayList();
       if(root ==  null)    return res;
       Deque <TreeNode> q =  new ArrayDeque();
       q.offer(root);
       while(!q.isEmpty()){
            List<Integer> l1 = new ArrayList<>();
            int size = q.size();
            for(int i = 0;i<size;i++){
                TreeNode curr = q.poll();
                l1.add(curr.val);
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            res.add(l1);
       }
       return res;
    }
}
```
## [107. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
          List<List<Integer>> res = new ArrayList();
       if(root ==  null)    return res;
       Deque <TreeNode> q =  new ArrayDeque();
       q.offer(root);
       while(!q.isEmpty()){
            List<Integer> l1 = new ArrayList<>();
            int size = q.size();
            for(int i = 0;i<size;i++){
                TreeNode curr = q.poll();
                l1.add(curr.val);
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            res.add(l1);
       }
       Collections.reverse(res);
       return res;
    }
}
```
## [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
       List<List<Integer>> res = new ArrayList();
       if(root ==  null)    return res;
       boolean flag = false;
       Deque <TreeNode> q =  new ArrayDeque();
       q.offer(root);
       while(!q.isEmpty()){
            List<Integer> l1 = new ArrayList<>();
            int size = q.size();
            for(int i = 0;i<size;i++){
                TreeNode curr = q.poll();
                l1.add(curr.val);
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            if(flag)   
                Collections.reverse(l1);
            flag = !flag;
            res.add(l1);
       }
       return res;
    }
}
```
## [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
         List<Integer> res = new ArrayList();
       if(root ==  null)    return res;
       Deque <TreeNode> q =  new ArrayDeque();
       q.offer(root);
       while(!q.isEmpty()){
            TreeNode curr = root; 
            int size = q.size();
            for(int i = 0;i<size;i++){
                curr = q.poll();
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            res.add(curr.val);
       }
       return res;
    }
}
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
         List<Integer> res = new ArrayList();
       if(root ==  null)    return res;
       Deque <TreeNode> q =  new ArrayDeque();
       q.offer(root);
       while(!q.isEmpty()){
            List<Integer> l1 = new ArrayList<>();
            int size = q.size();
            for(int i = 0;i<size;i++){
                TreeNode curr = q.poll();
                l1.add(curr.val);
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            res.add(l1.getLast());
       }
       return res;
    }
}
```
## [257. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)
```java
class Solution {
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> result = new ArrayList<>();
        StringBuilder s = new StringBuilder();
        path(s,root,result);
        return result;
    }
    private void path(StringBuilder s,TreeNode root,List<String> result){
        int l = s.length();
        if (s.length() > 0)
            s.append("->");
        s.append(root.val);
        if(root.left == null && root.right == null){
            result.add(s.toString());
        }
        else{
        if(root.left!=null)
            path(s,root.left,result);
        if(root.right!=null)
            path(s,root.right,result);
            }
        s.setLength(l);
    }
}
```
## [637. Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
         List<Double> res = new ArrayList();
       if(root ==  null)    return res;
       Deque <TreeNode> q =  new ArrayDeque();
       q.offer(root);
       while(!q.isEmpty()){
            double sum = 0; 
            int size = q.size();
            for(int i = 0;i<size;i++){ 
                TreeNode curr = q.poll();
                 sum += curr.val;
                if(curr.left != null)
                    q.offer(curr.left);
                if(curr.right != null)
                    q.offer(curr.right);
            }
            sum/=size;
            res.add(sum);
       }
       return res;
    }
}
```
## [701. Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        if( root ==  null)
            return new TreeNode(val);
        TreeNode ans = root;
        while(true){
            if(ans.val<val){
                if(ans.right == null){
                    ans.right = new TreeNode(val);
                    break;
                }
                else
                    ans = ans.right;
            }
            else{
                if(ans.left == null){
                    ans.left = new TreeNode(val);
                    break;
                }
                else
                    ans = ans.left;
            }
        }
        return root;
    }
}
```
## [112. Path Sum](https://leetcode.com/problems/path-sum/)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {
        int rs = 0;
        return ps(root,rs,targetSum);
    }
    boolean ps(TreeNode root,int rs,int targetSum){
        if(root == null)    return false;
        if(root.left == null && root.right == null){
            rs +=root.val;
            if(rs==targetSum)
                return true;
        }
        return ps(root.left,rs+root.val,targetSum) || ps(root.right,rs+root.val,targetSum);
            
        
    }
}
```
## [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)
```java
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int sumNumbers(TreeNode root) {
        int rs = 0;
       return srl(root,rs);
    }
    int srl(TreeNode root,int rs){
        if(root == null)
            return 0;
        if(root.left == null && root.right == null)
            return rs * 10 + root.val;
       return srl(root.left,rs * 10 + root.val) + srl(root.right,rs * 10 + root.val);
    }
}
```
# Backtracking

If Not Satisfies ,Function backtracks by removing the last element added.
## [39. Combination Sum](https://leetcode.com/problems/combination-sum/)
```java
class Solution {
    private void backtracking(int start,List<List<Integer>> res, List<Integer> comb,int[] candidates, int target){
        if(target<0)
            return;
        if(target == 0){
            res.add(new  ArrayList<>(comb));
            return ;
        }
        for(int i=start;i<candidates.length;i++){
            comb.add(candidates[i]);
            backtracking(i,res,comb,candidates,target-candidates[i]);
            comb.remove(comb.size()-1);
        }
    }
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> comb = new ArrayList<>();
        backtracking(0,res,comb,candidates,target);
        return res;
     }
}
```
## [40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
```java
class Solution {
    private void backtracking(int start,List<List<Integer>> res, List<Integer> comb,int[] candidates, int target){
        if(target<0)
            return;
        if(target == 0){
            res.add(new  ArrayList<>(comb));
            return ;
        }
        for(int i=start;i<candidates.length;i++){
            if(i>start && candidates[i] == candidates[i-1])
                continue;
            comb.add(candidates[i]);
            backtracking(i+1,res,comb,candidates,target-candidates[i]);
            comb.remove(comb.size()-1);
        }
    }
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> comb = new ArrayList<>();
        Arrays.sort(candidates);
        backtracking(0,res,comb,candidates,target);
        return res;
     }
}
```
## [216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)
```java
class Solution {
    private void backtracking(int start,List<List<Integer>> res, List<Integer> comb,int k, int target){
        if(comb.size() == k){
            if( target == 0){
                res.add(new ArrayList(comb));
            }
            else
                return;
        }
        for(int i=start;i<=9;i++){
            comb.add(i);
            backtracking(i+1,res,comb,k,target-i);
            comb.remove(comb.size()-1);
        }
    }
    public List<List<Integer>> combinationSum3(int k, int n) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> comb = new ArrayList<>();
        backtracking(1,res,comb,k,n);
        return res;
     }
}
```
## [46. Permutations](https://leetcode.com/problems/permutations/)
```java
class Solution {
    private void backtracking(int[] nums,List<List<Integer>> res, List<Integer> curr){
        if(curr.size() == nums.length){
            res.add(new ArrayList(curr));
            return;
        }
        for(int num : nums){
            if(!curr.contains(num)){
            curr.add(num);
            backtracking(nums,res,curr);
            curr.remove(curr.size()-1); 
            }
        }
    }
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        backtracking(nums,res,curr);
        return res;
     }
}
```
## [47. Permutations II](https://leetcode.com/problems/permutations-ii/)
```java
class Solution {
    private void backtracking(int[] nums,List<List<Integer>> res, List<Integer> curr,boolean[] used){
        if(curr.size() == nums.length && !res.contains(curr)){
            res.add(new ArrayList(curr));
            return;
        }
        for(int i = 0;i<nums.length;i++){
            int num = nums[i];
            if(!used[i]){
            used[i]=true;
            curr.add(num);
            backtracking(nums,res,curr,used);
            curr.remove(curr.size()-1);
            used[i]=false; 
            }
        }
    }
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        backtracking(nums,res,curr,new boolean[nums.length]);
        return res;
     
```

Optimal code below

```java
import java.util.*;

class Solution {
    private void backtracking(int[] nums, List<List<Integer>> res, List<Integer> curr, boolean[] used) {
        if (curr.size() == nums.length) {
            res.add(new ArrayList<>(curr)); // Add a copy of the current permutation
            return;
        }
        
        for (int i = 0; i < nums.length; i++) {
            // Skip if the current number is already used or it's a duplicate of the previous number
            // and the previous number wasn't used in this branch of the recursion
            if (used[i] || (i > 0 && nums[i] == nums[i - 1] && !used[i - 1])) {
                continue; // Skip duplicates
            }

            used[i] = true;
            curr.add(nums[i]);
            backtracking(nums, res, curr, used);
            curr.remove(curr.size() - 1); // Backtrack by removing the last added number
            used[i] = false; // Mark the current number as unused for the next iterations
        }
    }

    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(nums); // Sort the array to handle duplicates
        backtracking(nums, res, new ArrayList<>(), new boolean[nums.length]);
        return res;
    }
}
```
## [77. Combinations](https://leetcode.com/problems/combinations/)
```java
class Solution {
    private void backtrack( List<List<Integer>> res,List<Integer> curr,int j,int n,int k){
        if(curr.size() == k){
            res.add(new ArrayList(curr));
            return;
        }
        for(int i = j ; i <= n ; i++){
            curr.add(i);
            backtrack(res,curr,i+1,n,k);
            curr.remove(curr.size()-1); 
        }
    }
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        backtrack(res,curr,1,n,k);
        return res;
    }
}
```
## [17. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
```java
class Solution {
    private void backtracking(List<String> result, StringBuilder curr, String digits, int index, HashMap<Character, String> map) {
        if (curr.length() == digits.length()) {
            result.add(curr.toString());
            return;
        }
        String letters = map.get(digits.charAt(index));
        for (char c : letters.toCharArray()) {
            curr.append(c);  
            backtracking(result, curr, digits, index + 1, map); 
            curr.deleteCharAt(curr.length() - 1);
        }
    }

    public List<String> letterCombinations(String digits) {
        if (digits == null || digits.length() == 0) {
            return new ArrayList<>();
        }
        HashMap<Character, String> map = new HashMap<>();
        map.put('2', "abc");
        map.put('3', "def");
        map.put('4', "ghi");
        map.put('5', "jkl");
        map.put('6', "mno");
        map.put('7', "pqrs");
        map.put('8', "tuv");
        map.put('9', "wxyz");
        List<String> result = new ArrayList<>();
        backtracking(result, new StringBuilder(), digits, 0, map);
        return result;
    }
}
```
## ** [51. N-Queens](https://leetcode.com/problems/n-queens/)
```java
class Solution {

    private boolean canPlace(int row,int col, List<String> curr){
        for(int i = row-1;i>=0;i--){
            if(curr.get(i).charAt(col)=='Q')
                return false;
        }
        for(int i = row-1, j=col-1;i>=0 && j>=0;i--,j--){
            if(curr.get(i).charAt(j)=='Q')
                return false;
        }
        for(int i = row-1, j = col+1; i>=0 && j<curr.size(); i--,j++){
            if(curr.get(i).charAt(j)=='Q')
                return false;
        }
        return true;
    }
    private void solveNQueens(int row, List<List<String>> res ,  List<String> curr ){
        if(row == curr.size()){
            res.add(new ArrayList(curr));
            return;
        }
        for(int col = 0;col<curr.size();col++){
            if(canPlace(row,col,curr)){
                StringBuilder sb =  new StringBuilder(curr.get(row));
                sb.setCharAt(col,'Q');
                curr.set(row,sb.toString());
                solveNQueens(row+1 ,res, curr );
                sb.setCharAt(col,'.');
                curr.set(row,sb.toString());
            }
        }
    }
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> res = new ArrayList<>();
        List<String> curr = new ArrayList<>();
        for(int i=0; i<n;i++)
            curr.add(".".repeat(n));
        solveNQueens(0,res,curr);
        return res;
    }
}
```
## ** [52. N-Queens II](https://leetcode.com/problems/n-queens-ii/)
```java
class Solution {

    private boolean canPlace(int row,int col, List<String> curr){
        for(int i = row-1;i>=0;i--){
            if(curr.get(i).charAt(col)=='Q')
                return false;
        }
        for(int i = row-1, j=col-1;i>=0 && j>=0;i--,j--){
            if(curr.get(i).charAt(j)=='Q')
                return false;
        }
        for(int i = row-1, j = col+1; i>=0 && j<curr.size(); i--,j++){
            if(curr.get(i).charAt(j)=='Q')
                return false;
        }
        return true;
    }
    private void totalNQueens(int row, int[] res ,  List<String> curr ){
        if(row == curr.size()){
            res[0]++;
            return;
        }
        for(int col = 0;col<curr.size();col++){
            if(canPlace(row,col,curr)){
                StringBuilder sb =  new StringBuilder(curr.get(row));
                sb.setCharAt(col,'Q');
                curr.set(row,sb.toString());
                totalNQueens(row+1 ,res, curr );
                sb.setCharAt(col,'.');
                curr.set(row,sb.toString());
            }
        }
    }
    public int totalNQueens(int n) {
        int[] res =  {0};
        List<String> curr = new ArrayList<>();
        for(int i=0; i<n;i++)
            curr.add(".".repeat(n));
        totalNQueens(0,res,curr);
        return res[0];
    }
}
```

## [127. Word Ladder](https://leetcode.com/problems/word-ladder/)
```java
import java.util.*;

class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        // Check if the endWord is present in the wordList
        Set<String> s = new HashSet<>(wordList);
        if (!s.contains(endWord)) {
            return 0; // endWord must be in the wordList to have a valid transformation
        }
        
        // Initialize BFS
        Queue<String> q = new LinkedList<>();
        q.add(beginWord);
        int level = 1; // Starting level is 1 because we start with the beginWord

        // Perform BFS
        while (!q.isEmpty()) {
            int levelSize = q.size(); // Number of elements at the current level
            
            // Process all nodes at the current level
            for (int i = 0; i < levelSize; i++) {
                String curr = q.poll(); // Dequeue the current word
                
                // Try to transform each character of the current word
                for (int j = 0; j < curr.length(); j++) {
                    StringBuilder temp = new StringBuilder(curr);
                    
                    // Change each character to every letter from 'a' to 'z'
                    for (char c = 'a'; c <= 'z'; c++) {
                        temp.setCharAt(j, c);
                        String tempWord = temp.toString();
                        
                        // Skip if the word hasn't changed
                        if (tempWord.equals(curr)) {
                            continue;
                        }
                        
                        // If transformed word is the endWord, return the length of the sequence
                        if (tempWord.equals(endWord)) {
                            return level + 1;
                        }
                        
                        // If the transformed word is in the set, add it to the queue and remove it from the set
                        if (s.contains(tempWord)) {
                            q.add(tempWord);
                            s.remove(tempWord); // Remove to avoid revisiting
                        }
                    }
                }
            }
            level++; // Increment level after processing all nodes at this level
        }

        return 0; // Return 0 if no transformation sequence is found
    }
}
```
## [200. Number of Islands](https://leetcode.com/problems/number-of-islands/)
```java
class Solution {
    void dfs(char[][]grid,int r,int c,int nR,int nC){
        if(r<0 || c<0 || r>=nR || c>=nC || grid[r][c] == '0')
            return;
        grid[r][c] = '0';
        dfs(grid,r+1,c,nR,nC);
        dfs(grid,r-1,c,nR,nC);
        dfs(grid,r,c+1,nR,nC);
        dfs(grid,r,c-1,nR,nC);
    }
    public int numIslands(char[][] grid) {
        int nR = grid.length;
        int nC = grid[0].length;
        int numIsLands = 0;
        for(int i=0 ;i<nR;i++){
            for(int j=0;j<nC;j++){
                if(grid[i][j] == '1'){
                    ++numIsLands;
                    dfs(grid,i,j,nR,nC);
                }
            }
        }
        return numIsLands;
    }
}
```
## [1863. Sum of All Subset XOR Totals](https://leetcode.com/problems/sum-of-all-subset-xor-totals/)
```java
class Solution {
    public int subsetXORSum(int[] nums) {
        int[] sum  = {0};
        int n = nums.length;
        subXor(0,0,sum,nums);
        return sum[0];
    }
    private void subXor(int i,int currXor,int[] sum,int[] nums){
        if(i == nums.length){
            sum[0]+=currXor;
            return;
        }
         subXor(i+1,currXor^nums[i],sum,nums);
         subXor(i+1,currXor,sum,nums);
    }
}
```
## [79. Word Search](https://leetcode.com/problems/word-search/)
```java
class Solution {
    private boolean isexist(char[][] board, String word, int i, int j, int k, int m, int n) {
        if (k == word.length()) {
            return true;
        }
        if (i < 0 || i >= m || j < 0 || j >= n || board[i][j] != word.charAt(k)) {
            return false;
        }
        char temp = board[i][j];
        board[i][j] = '#';
        boolean found = isexist(board, word, i + 1, j, k + 1, m, n) || 
                        isexist(board, word, i - 1, j, k + 1, m, n) || 
                        isexist(board, word, i, j + 1, k + 1, m, n) ||
                        isexist(board, word, i, j - 1, k + 1, m, n); 
        board[i][j] = temp;
        return found;
    }

    public boolean exist(char[][] board, String word) {
        int m = board.length;
        int n = board[0].length;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (board[i][j] == word.charAt(0) && isexist(board, word, i, j, 0, m, n)) {
                    return true;
                }
            }
        }
        return false;
    }
}
```
## [494. Target Sum](https://leetcode.com/problems/target-sum/)
```java
class Solution {
    private int count = 0;
    private void backtrack(int[] nums, int target, int currSum, int currIndex) {
        if (currIndex == nums.length) {
            if (currSum == target) {
                count++;
            }
            return;
        }
        backtrack(nums, target, currSum + nums[currIndex], currIndex + 1);
        backtrack(nums, target, currSum - nums[currIndex], currIndex + 1);
    }
    public int findTargetSumWays(int[] nums, int target) {
        count = 0;
        backtrack(nums, target, 0, 0);
        return count;
    }
}
```
# Compare function
## [179. Largest Number](https://leetcode.com/problems/largest-number/)
```java
public class Solution {
    public String largestNumber(int[] nums) {
        // Convert integer array to string array
        String[] strNums = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            strNums[i] = Integer.toString(nums[i]);
        }

        // Sort the string array based on custom comparator
        Arrays.sort(strNums, new Comparator<String>() {
            public int compare(String s1, String s2) {
                // Compare concatenated results
                return (s2 + s1).compareTo(s1 + s2);
            }
        });

        // If the largest number is "0", return "0"
        if (strNums[0].equals("0")) {
            return "0";
        }

        // Concatenate sorted strings
        StringBuilder result = new StringBuilder();
        for (String str : strNums) {
            result.append(str);
        }

        return result.toString();
    }
    
}
```
# Bit Manipulation
```java
class Solution {
    public int hammingWeight(int n) {
        String binaryRepresentation = Integer.toBinaryString(n);
        int count = 0;
        for (char c : binaryRepresentation.toCharArray()) {
            if (c == '1') {
                count++;
            }
        }
        
        return count;
    }
}
```
## [67. Add Binary](https://leetcode.com/problems/add-binary/)
```java
class Solution {
    private int append(int carry, int A, int B, StringBuilder s) {
        int sum = A + B + carry;
        int temp = sum % 2;
        int newCarry = sum / 2;
        s.append(temp);
        return newCarry;
    }

    public String addBinary(String a, String b) {
        int carry = 0;
        StringBuilder s = new StringBuilder();
        int i = a.length() - 1;
        int j = b.length() - 1;
        while (i >= 0 || j >= 0) {
            int A = (i >= 0) ? a.charAt(i) - '0' : 0;
            int B = (j >= 0) ? b.charAt(j) - '0' : 0;
            carry = append(carry, A, B, s);
            i--;
            j--;
        }
        if (carry == 1) {
            s.append(carry);
        }
        return s.reverse().toString();
    }
}
```
## [338. Counting Bits](https://leetcode.com/problems/counting-bits/)
```java
class Solution {
    public int[] countBits(int n) {
        int[] ans = new int[n+1];
        ans[0] = 0;
        for(int i = 1; i<=n;i++){
            ans[i] = ans[i/2] + (i & 1);
        }
        return ans;
    }
}
```
## [2859. Sum of Values at Indices With K Set Bits](https://leetcode.com/problems/sum-of-values-at-indices-with-k-set-bits/)
```java
class Solution {
    public int sumIndicesWithKSetBits(List<Integer> nums, int k) {
        int result = 0;
        for (int i = 0; i < nums.size(); i++) {
            int index = i;
            int count = 0;
            while (index != 0) {
                if ((index & 1) == 1) {
                    count++;
                }
                index >>= 1;
            }
            if (count == k) {
                result += nums.get(i);
            }
        }
        return result;
    }
}
```

```java
class Solution {
    public int sumIndicesWithKSetBits(List<Integer> nums, int k) {
        int result = 0;
       for(int i = 0;i<nums.size();i++){
        if(Integer.bitCount(i)==k)
            result+=nums.get(i);
       }
       return result;
    }
}
```
# Queue
## [264. Ugly Number II](https://leetcode.com/problems/ugly-number-ii/) (DP and Queue & TreeSet)
```java
class Solution {
    public int nthUglyNumber(int n) {
        int dp[]=new int[n+1];
        dp[1]=1;
        int i2=1,i3=1,i5=1;
        for(int i=2;i<=n;i++)
        {
            int i2ugly=dp[i2]* 2;
            int i3ugly=dp[i3]* 3;
            int i5ugly=dp[i5]* 5;
            int minUgly=Math.min(i2ugly,Math.min(i3ugly,i5ugly));
            dp[i]=minUgly;
            if(minUgly == i2ugly)
              i2++;
            if(minUgly == i3ugly)
              i3++;
            if(minUgly == i5ugly)
              i5++;
        }
        return dp[n];
    }
}
```

```java
class Solution {
    public int nthUglyNumber(int n) {
        PriorityQueue<Long> uglynos = new PriorityQueue<>();
        HashSet<Long> seen =  new HashSet<>();
        seen.add(1L);
        uglynos.add(1L);
        long Ugly = 0;
        int[] factors = {2,3,5};
        for(int i = 0 ; i< n;i++){
            Ugly = uglynos.poll();
            for(int factor : factors){
                long newUgly = factor * Ugly;
                if(!seen.contains(newUgly)){
                    uglynos.add(newUgly);
                    seen.add(newUgly);
                }
            }
        }
        return (int)Ugly;
    }
}
```

```java
import java.util.TreeSet;

class Solution {
    public int nthUglyNumber(int n) {
        TreeSet<Long> uglynos = new TreeSet<>();  // TreeSet to store and maintain order
        uglynos.add(1L);  // Start with 1 as the first super ugly number
        
        long Ugly = 0;  // Variable to store the current ugly number
        int[] primes = {2,5,3};
        for (int i = 0; i < n; i++) {
            Ugly = uglynos.pollFirst();  // Get the smallest element (the next super ugly number)
            
            for ( int prime : primes) {
                Long newUgly = prime * Ugly;
                // Check to avoid overflow before adding
                if (newUgly > 0 && !uglynos.contains(newUgly)) {
                    uglynos.add(newUgly);  // Add new super ugly number if it's not already in the set
                }
            }
        }
        return (int)Ugly;
    }
}
```

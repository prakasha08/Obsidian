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
## [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/)```java
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
## [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
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
# Dynamic Programming

**Memoization +(Recursion (Or) Iteration) = DP**
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
# Binary Search

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
## ** [100. Same Tree](https://leetcode.com/problems/same-tree/)\
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
## 
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
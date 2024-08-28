# list
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
# HashMap
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
 
# HashMap
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
``
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
 
# Subarrays

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
## [713. Subarray Product Less Than K](https://leetcode.com/problems/subarray-product-less-than-k/)
```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        if (k <= 1) return 0;
        int prod = 1, count = 0, left = 0;
        for (int right = 0; right < nums.length; right++) {
            prod *= nums[right];
            while (prod >= k) {
                prod /= nums[left++];
            }
            count += right - left + 1;
        }
        return count;
    }
}
```
## [523. Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/)
```java
class Solution {
    public boolean checkSubarraySum(int[] nums, int k) {
    Map<Integer, Integer> modMap = new HashMap<>();
    modMap.put(0, -1);

    int sum = 0;
    for (int i = 0; i < nums.length; i++) {
        sum += nums[i];
        int mod = k == 0 ? sum : sum % k;

        if (modMap.containsKey(mod)) {
            if (i - modMap.get(mod) >= 2) {
                return true;
            }
        } else {
            modMap.put(mod, i); 
        }
    }
    return false;
}
}
```
## [525. Contiguous Array](https://leetcode.com/problems/contiguous-array/)
```java
class Solution {
    public int findMaxLength(int[] nums) {
        HashMap<Integer,Integer> map = new HashMap<>();
        map.put(0,-1);
        int sum = 0;
        int max = 0;
        for(int i= 0; i<nums.length;i++){
            sum += nums[i] == 0?-1:1;
            if(map.containsKey(sum)){
                max = Math.max(max,i-map.get(sum));
            }
            else{
                map.put(sum,i);
            }
        }
        return max;
    }
}
```
## [974. Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
```java
class Solution {
    public int subarraysDivByK(int[] nums, int k) {
        Map<Integer, Integer> modMap = new HashMap<>();
    modMap.put(0, 1);
    int sum = 0,count = 0;
    for (int i = 0; i < nums.length; i++) {
        sum += nums[i];
        int mod = sum % k;
        mod = mod<0?mod+k:mod;
        if (modMap.containsKey(mod)) {
            count+=modMap.get(mod);
        } 
        modMap.put(mod, modMap.getOrDefault(mod,0)+1); 
        
    }
    return count;
    }
}
```
## [1248. Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)
```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        int n = nums.length;
        int odd =0,count=0;
        HashMap<Integer,Integer> map = new HashMap<>();
        map.put(0,1);
        for(int i = 0;i<n;i++){
            if(nums[i]%2!=0)
                odd++;
            count+=map.getOrDefault(odd-k,0);
            map.put(odd,map.getOrDefault(odd,0)+1);
        }

        return count;
    
```

## [1658. Minimum Operations to Reduce X to Zero](https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/)
```java
class Solution {
    public int minOperations(int[] nums, int x) {
        int total = 0;
        for (int num : nums) total += num;

        int target = total - x;
        if (target < 0) return -1;
        if (target == 0) return nums.length;

        int maxLen = -1, currSum = 0, left = 0;

        for (int right = 0; right < nums.length; right++) {
            currSum += nums[right];

            while (currSum > target && left <= right) {
                currSum -= nums[left++];
            }

            if (currSum == target) {
                maxLen = Math.max(maxLen, right - left + 1);
            }
        }

        return maxLen == -1 ? -1 : nums.length - maxLen;
    }
}
```
## [2762. Continuous Subarrays](https://leetcode.com/problems/continuous-subarrays/)

**O(n^2)**
```java
class Solution {
    public long continuousSubarrays(int[] nums) {
        long count = 0;
        int n = nums.length;
        
        for (int l = 0; l < n; l++) {
            int max = nums[l];
            int min = nums[l];
            for (int r = l; r < n; r++) {
                max = Math.max(max, nums[r]);
                min = Math.min(min, nums[r]);
                if (max - min <= 2) {
                    count++;
                } else {
                    break;
                }
            }
        }
        
        return count;
    }
}
```
**O(nlogn)**

```java
class Solution {
    public long continuousSubarrays(int[] nums) {
        int left = 0;
        long count = 0;
        TreeMap<Integer, Integer> map = new TreeMap<>();
        for (int right = 0; right < nums.length; right++) {
            map.put(nums[right], map.getOrDefault(nums[right], 0) + 1);
            while (map.lastKey() - map.firstKey() > 2) {
                map.put(nums[left], map.get(nums[left]) - 1);
                if (map.get(nums[left]) == 0) {
                    map.remove(nums[left]);
                }
                left++;
            }
            count += right - left + 1;
        }
        return count;
    }
}
```

## [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int l = 0, r, sum = 0, min = Integer.MAX_VALUE;
        for (r = 0; r < nums.length; r++) {
            sum += nums[r];
            while (sum >= target) {
                min = Math.min(min, r - l + 1);
                sum -= nums[l];
                l++;
            }
        }
        return min == Integer.MAX_VALUE ? 0 : min;
    }
}
```
## [795. Number of Subarrays with Bounded Maximum](https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/)
```java
class Solution {
    public int numSubarrayBoundedMax(int[] nums, int left, int right) {
        int n=nums.length, start=0, end=0, prevCnt=0, ans=0, result=0;
        while(end<n){
            if(nums[end]>=left && nums[end]<=right){
                prevCnt = end-start+1;
                result += prevCnt;
            }else{
                if(nums[end]<left){
                    result += prevCnt;
                }else{
                    start = end+1;
                    prevCnt=0;
                }
            }
            end++;
        }
        return result;
    }
}
```
# 1920. Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/)
![[Pasted image 20240319212449.png]]
```java
class Solution {

    public int[] buildArray(int[] nums) {

        // Scanner n= new Scanner(System.in);

        int[] arr= new int[nums.length];

        for(int i=0;i<nums.length;i++){

            arr[i]=nums[nums[i]];

        }

        return arr;

    }

}
```
# 1929. Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/)
![[Pasted image 20240319215420.png]]
```java
class Solution {

    public int[] getConcatenation(int[] nums) {

        int []arr= new int[nums.length*2];

        System.arraycopy(nums,0, arr, 0, nums.length);

        System.arraycopy(nums, 0, arr, nums.length, nums.length);

        return arr;

    }

}
```
# 1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

![[Pasted image 20240407221605.png]]
```java 
class Solution {

    public int[] runningSum(int[] nums) {

        int[] arr= new int[nums.length];

        arr[0]=nums[0];

        for(int i=1;i<nums.length;i++){

            arr[i]=arr[i-1]+nums[i];

        }

        return arr;

    }

}
```
# 1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)
![[Pasted image 20240407222128.png]]
```java
class Solution {

    public int maximumWealth(int[][] accounts)

    {

     int count=0;

        for(int i=0;i<accounts.length;i++){

           int sum=0;

             for(int j=0;j<accounts[i].length;j++){

                      sum+=accounts[i][j];

                     }

                 if(sum>count)

                    count=sum;

             }

             return count;

         }

 }
 
```
# 1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)
![[Pasted image 20240407224636.png]]
```java
class Solution {

    public int[] shuffle(int[] nums, int n) {

        int[] arr = new int[nums.length];

        int j = 0; // Initialize a separate index for the new array

        for (int i = 0; i < n; i++) { // Loop through the first half of nums

            arr[j++] = nums[i]; // Assign the current element of nums to the new array

            arr[j++] = nums[i + n]; // Assign the corresponding element from the second half of nums to the new array

        }

        return arr;

    }

}
```
#   1431. Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)
![[Pasted image 20240407225419.png]]
```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        int max = 0;

        for(int candy : candies)
            max = Math.max(max, candy);

        List<Boolean> result = new ArrayList<>();

        for(int candy : candies)
            result.add(max <= candy + extraCandies);

        return result;
    }
}

```
# 1512. Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)
![[Pasted image 20240407225938.png]]
```java
class Solution {

    public int numIdenticalPairs(int[] nums) {

        int count=0;

        for(int i=0;i<nums.length;i++){

            for(int j=i+1;j<nums.length;j++){

                if(nums[i]==nums[j]){

                    count++;

                }

            }

        }

          return count;

    }

}
```
  
# 1773. Count Items Matching a Rule](https://leetcode.com/problems/count-items-matching-a-rule/)
![[Pasted image 20240408232141.png]]
```java
class Solution {

    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {

        int j,count=0;

        if(ruleKey.equals("type"))

            j=0;

        else if(ruleKey.equals("color"))

            j=1;

        else

            j=2;

        for(int i=0;i<items.size();i++){

            if(items.get(i).get(j).equals(ruleValue))

                    count+=1;

        }

        return count;

    }

}
```
# [66. Plus One](https://leetcode.com/problems/plus-one/)
![[Pasted image 20240524103603.png]]
```java
class Solution {

    public int[] plusOne(int[] digits) {

        int n = digits.length;

        int[] arr = new int[n];

        int carry = 1;

        for (int i = n - 1; i >= 0; i--) {

            int sum = digits[i] + carry;

            arr[i] = sum % 10;

            carry = sum / 10;

        }

        if (carry == 1) {

            arr = new int[n + 1];

            arr[0] = 1;

        }

        return arr;

    }

}
```
# [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
![[Pasted image 20240525213219.png]]
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int n = nums.length;
        int arr[] = new int[n];

        // Initialize the auxiliary array to 0
        for (int i = 0; i < n; i++) {
            arr[i] = 0;
        }

        // Mark duplicates in the auxiliary array
        for (int i = 0; i < n; i++) {
            if (arr[i] == 0) {
                for (int j = i + 1; j < n; j++) {
                    if (nums[i] == nums[j]) {
                        arr[j] = 1;  // Mark duplicate elements
                    }
                }
            }
        }

        // Count the number of unique elements
        int k = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] == 0) {  // If not marked as duplicate
                nums[k] = nums[i];  // Move unique element to the front
                k += 1;
            }
        }
        
        return k;  // Number of unique elements
    }
}

```

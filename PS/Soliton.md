## Sorting in O(n)
```c
#include <stdio.h>
#include <string.h>

void countingSort(int arr[], int size, int maxVal) {
    int count[maxVal + 1];  
    memset(count, 0, sizeof(count));  // Initialize count array to 0

    // Count occurrences
    for (int i = 0; i < size; i++) {
        count[arr[i]]++;
    }

    // Reconstruct sorted array
    int index = 0;
    for (int i = 0; i <= maxVal; i++) {
        while (count[i] > 0) {
            arr[index++] = i;
            count[i]--;
        }
    }
}

int main() {
    int arr[] = {4, 2, 2, 8, 3, 3, 1};
    int size = sizeof(arr) / sizeof(arr[0]);
    int maxVal = 8;  // Assuming maximum value is known

    countingSort(arr, size, maxVal);

    printf("Sorted array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}

```

## 2nd largest in o(n)
```c
#include <stdio.h>
#include <limits.h>  // For INT_MIN

void findSecondLargest(int arr[], int size) {
    if (size < 2) {
        printf("Array must have at least two elements.\n");
        return;
    }

    int largest = INT_MIN, secondLargest = INT_MIN;

    for (int i = 0; i < size; i++) {
        if (arr[i] > largest) {
            secondLargest = largest;  // Update second largest
            largest = arr[i];         // Update largest
        } else if (arr[i] > secondLargest && arr[i] != largest) {
            secondLargest = arr[i];  // Update second largest if it's not equal to largest
        }
    }

    if (secondLargest == INT_MIN) {
        printf("No second largest element found (all elements might be the same).\n");
    } else {
        printf("Second largest element: %d\n", secondLargest);
    }
}

int main() {
    int arr[] = {12, 35, 1, 10, 34, 1};
    int size = sizeof(arr) / sizeof(arr[0]);

    findSecondLargest(arr, size);

    return 0;
}

```

## Duplicate
```c
#include <stdio.h>

int sumOfDuplicates(int arr[], int size) {
    int maxVal = 0;
    
    // Find the maximum value in the array to size the frequency array
    for (int i = 0; i < size; i++) {
        if (arr[i] > maxVal)
            maxVal = arr[i];
    }

    int freq[maxVal + 1]; // Frequency array
    for (int i = 0; i <= maxVal; i++) {
        freq[i] = 0; // Initialize all values to 0
    }

    int sum = 0;

    // Count occurrences
    for (int i = 0; i < size; i++) {
        freq[arr[i]]++;

        // If it's counted for the second time, add it to the sum
        if (freq[arr[i]] == 2) {
            sum += arr[i]; 
        }
    }

    return sum;
}

int main() {
    int arr[] = {1, 3, 3, 4, 2, 2};  // Example array
    int size = sizeof(arr) / sizeof(arr[0]);

    int sum = sumOfDuplicates(arr, size);
    printf("Sum of Duplicate Elements: %d\n", sum);

    return 0;
}

```

## For duplicates ,if the numbers in an array with 1 to n(size of array)

```c
#include <stdio.h>

int findDuplicate(int arr[], int size) {
    int slow = arr[0];
    int fast = arr[0];

    // Phase 1: Detect cycle
    do {
        slow = arr[slow];      // Move one step
        fast = arr[arr[fast]]; // Move two steps
    } while (slow != fast);

    // Phase 2: Find start of the cycle (duplicate)
    slow = arr[0];  // Reset slow to start
    while (slow != fast) {
        slow = arr[slow];
        fast = arr[fast];
    }

    return slow;  // The duplicate element
}

int main() {
    int arr[] = {1, 3, 4, 2, 2};  // Contains duplicate '2'
    int size = sizeof(arr) / sizeof(arr[0]);

    int duplicate = findDuplicate(arr, size);
    printf("Duplicate element: %d\n", duplicate);

    return 0;
}

```

## Max subarray
```c
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    
    int num[n];
    for (int i = 0; i < n; i++) {
        scanf("%d", &num[i]);
    }
    
    int max_sum = num[0];  // Stores the maximum subarray sum
    int current_sum = num[0];  // Current sum including num[i]
    
    for (int i = 1; i < n; i++) {
        // Decide whether to add num[i] to the current sum or start fresh
        if (current_sum < 0) {
            current_sum = num[i];  
        } else {
            current_sum += num[i];
        }

        // Update max_sum if we found a larger sum
        if (current_sum > max_sum) {
            max_sum = current_sum;
        }
    }
    
    printf("%d\n", max_sum);
    return 0;
}

```
## Remove vowels using ASCII value
```c
#include <stdio.h>
#include <string.h>

#define MAX_LEN 100

// Function to remove vowels using ASCII values
void removeVowels(char str[]) {
    int index = 0;
    char result[MAX_LEN];

    for (int i = 0; str[i] != '\0'; i++) {
        char ch = str[i];
        // Convert uppercase to lowercase for checking
        char lowerCh = (ch >= 'A' && ch <= 'Z') ? ch + 32 : ch;

        // ASCII values of vowels: a=97, e=101, i=105, o=111, u=117
        if (!(lowerCh == 97 || lowerCh == 101 || lowerCh == 105 || lowerCh == 111 || lowerCh == 117)) {
            result[index++] = ch;  // Store non-vowel characters
        }
    }
    
    result[index] = '\0'; // Null terminate the modified string
    printf("String after removing vowels: %s\n", result);
}

int main() {
    char str[MAX_LEN];

    // Input string
    printf("Enter a string: ");
    fgets(str, MAX_LEN, stdin);
    
    // Remove newline character if present
    str[strcspn(str, "\n")] = '\0';

    removeVowels(str);

    return 0;
}

```

## Find Duplicate Count in O(n) Without Extra Space in C
```c
#include <stdio.h>
#include <stdlib.h>

void findDuplicateCount(int arr[], int n) {
    printf("Duplicate elements:\n");
    
    for (int i = 0; i < n; i++) {
        int index = abs(arr[i]);  // Use absolute value as index

        // If the value at index is already negative, it's a duplicate
        if (arr[index] < 0) {
            printf("%d\n", index);
        } else {
            arr[index] = -arr[index];  // Mark index as visited
        }
    }
}

int main() {
    int arr[] = {3, 1, 3, 4, 2, 2, 4};
    int n = sizeof(arr) / sizeof(arr[0]);

    findDuplicateCount(arr, n);
    return 0;
}

```
## Determinant
```c
#include <stdio.h>

#define MAX 10 // Maximum matrix size

// Function to compute the determinant of a matrix
int determinant(int matrix[MAX][MAX], int n) {
    int det = 0; // Initialize determinant
    
    // Base case: If matrix is 1x1, return the single element
    if (n == 1)
        return matrix[0][0];

    // Base case: If matrix is 2x2, use direct formula
    if (n == 2)
        return (matrix[0][0] * matrix[1][1]) - (matrix[0][1] * matrix[1][0]);

    int temp[MAX][MAX]; // Temporary matrix for cofactors
    int sign = 1;       // Sign for cofactor expansion

    // Loop through first row to expand determinant
    for (int j = 0; j < n; j++) {
        // Create minor matrix (excluding first row and column j)
        int sub_i = 0; // Row index for submatrix
        for (int i = 1; i < n; i++) {
            int sub_j = 0; // Column index for submatrix
            for (int k = 0; k < n; k++) {
                if (k != j) { // Skip column `j`
                    temp[sub_i][sub_j] = matrix[i][k];
                    sub_j++;
                }
            }
            sub_i++;
        }
        // Recursively calculate determinant using minors
        det += sign * matrix[0][j] * determinant(temp, n - 1);
        sign = -sign; // Alternate sign
    }

    return det;
}

int main() {
    int matrix[MAX][MAX], n;

    // Input matrix size
    printf("Enter the size of the square matrix (n x n): ");
    scanf("%d", &n);

    // Input matrix elements
    printf("Enter the elements of the matrix:\n");
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            printf("element [%d][%d]: ", i, j);
            scanf("%d", &matrix[i][j]);
        }
    }

    // Compute determinant
    int det = determinant(matrix, n);
    printf("\nDeterminant of the matrix is: %d\n", det);

    return 0;
}

```
## Odd count Number Using XOR
```c
#include <stdio.h>

// Function to find the element occurring odd number of times in the array using XOR operation
int findOddCountElem(int *arr1, int n) {
    int i, ResultXor = 0;

    // Performing XOR operation on all array elements
    for (i = 0; i < n; i++) {
        ResultXor = ResultXor ^ arr1[i];
    }
    return ResultXor; // Returns the element occurring odd number of times
}

// Main function
int main() {
    int i;
    int arr1[] = {8, 3, 8, 5, 4, 3, 4, 3, 5};
    int ctr = sizeof(arr1) / sizeof(arr1[0]);

    // Display the given array
    printf("The given array is :  ");
    for (i = 0; i < ctr; i++) {
        printf("%d  ", arr1[i]);
    }
    printf("\n");

    // Function call to find the element occurring odd number of times
    printf("Number of odd number occur(s) : %d times.\n", findOddCountElem(arr1, ctr));

    return 0;
}

```
## Spiral MAtrix
```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

int* spiralOrder(int** matrix, int matrixSize, int* matrixColSize, int* returnSize) {
    if (matrixSize == 0 || matrixColSize[0] == 0) {
        *returnSize = 0;
        return NULL;
    }

    int row = matrixSize;
    int col = matrixColSize[0];
    bool visited[row][col];
    for (int i = 0; i < row; ++i) {
        for (int j = 0; j < col; ++j) {
            visited[i][j] = false;
        }
    }

    int* result = (int*)malloc(row * col * sizeof(int));
    *returnSize = 0;

    int d[4][2] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
    int k = 0, r = 0, c = 0;

    while (*returnSize < row * col) {
        result[(*returnSize)++] = matrix[r][c];
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

int main() {
    int rows = 3, cols = 3;
    int* matrix[3];
    int matrixColSize[3] = {3, 3, 3};
    int data[3][3] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    for (int i = 0; i < rows; ++i) {
        matrix[i] = data[i];
    }

    int returnSize;
    int* result = spiralOrder(matrix, rows, matrixColSize, &returnSize);

    for (int i = 0; i < returnSize; ++i) {
        printf("%d ", result[i]);
    }
    printf("\n");

    free(result);
    return 0;
}

```

## Max subarray in circular Array
```c
class Solution {
    public int maxSubArray(int[] nums) {
        int currSum = nums[0];
        int maxSum = nums[0];
        for (int i = 1; i < nums.length; i++) {
            currSum = Math.max(nums[i], currSum + nums[i]);
            maxSum = Math.max(maxSum, currSum);
        }
        return maxSum;
    }

    public int maxCircularSubarraySum(int[] nums) {
        int maxKadane = maxSubArray(nums);  // Standard Kadane's Algorithm
        
        // Compute total sum and invert array values
        int totalSum = 0;
        for (int i = 0; i < nums.length; i++)
            totalSum += nums[i];

        // Invert the array to find the minimum subarray sum
        for (int i = 0; i < nums.length; i++)
            nums[i] = -nums[i];

        int minKadane = maxSubArray(nums);  // Find max sum of inverted array (negative min sum)
        int maxCircular = totalSum + minKadane;  // Max circular sum

        // If all elements are negative, return maxKadane
        return (maxCircular == 0) ? maxKadane : Math.max(maxKadane, maxCircular);
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        int[] nums = {10, 8, -20, 5, -3, -5, 10, -13, 11};
        System.out.println("The given array is: ");
        for (int num : nums) {
            System.out.print(num + " ");
        }
        System.out.println("\nThe maximum circular sum in the above array is: " + sol.maxCircularSubarraySum(nums));
    }
}

```
## LCS
```c
#include <stdio.h>
#include <string.h>

int lcs(const char *s1, const char *s2, int i, int j, int m, int n) {
    if (i >= m || j >= n) {
        return 0;
    }
    if (s1[i] == s2[j]) {
        return 1 + lcs(s1, s2, i + 1, j + 1, m, n);
    } else {
        int skipS1 = lcs(s1, s2, i + 1, j, m, n);
        int skipS2 = lcs(s1, s2, i, j + 1, m, n);
        return (skipS1 > skipS2) ? skipS1 : skipS2;
    }
}

int longestCommonSubsequence(const char *text1, const char *text2) {
    int m = strlen(text1);
    int n = strlen(text2);
    return lcs(text1, text2, 0, 0, m, n);
}

int main() {
    char text1[100], text2[100];
    printf("Enter the first string: ");
    scanf("%s", text1);
    printf("Enter the second string: ");
    scanf("%s", text2);

    int result = longestCommonSubsequence(text1, text2);
    printf("Length of Longest Common Subsequence: %d\n", result);
    return 0;
}

```
## Find the Length of the Longest Substring Without Repeating Characters
```c
#include <stdio.h>
#include <string.h>

int lengthOfLongestSubstring(char *s) {
    int charIndex[256]; // Array to store the last index of each character
    for (int i = 0; i < 256; i++) {
        charIndex[i] = -1; // Initialize all indices to -1
    }

    int maxLength = 0; // Variable to store the maximum length
    int start = 0; // Start index of the current substring

    for (int i = 0; s[i] != '\0'; i++) {
        if (charIndex[s[i]] >= start) {
            start = charIndex[s[i]] + 1; // Move the start index to the right of the last occurrence
        }
        charIndex[s[i]] = i; // Update the last index of the character
        int currentLength = i - start + 1; // Calculate the current length of the substring
        if (currentLength > maxLength) {
            maxLength = currentLength; // Update maxLength if the current length is greater
        }
    }

    return maxLength;
}

int main() {
    char str[100];

    printf("Input a string: ");
    fgets(str, sizeof(str), stdin);
    
    // Remove the newline character at the end, if it exists
    str[strcspn(str, "\n")] = '\0';

    int length = lengthOfLongestSubstring(str);
    printf("Length of the longest substring without repeating characters: %d\n", length);
    
    return 0;
}

```
## Valid Paranthesis
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

#define MAX_SIZE 100

// Stack implementation
bool isValid(char *s) {
    char stack[100];
    int top = -1;

    for (int i = 0; s[i] != '\0'; i++) {
        char c = s[i];
        if (c == '(' || c == '{' || c == '[' || c == '<') {
            stack[++top] = c;
        } else {
            if (top == -1)
                return false;
            char topChar = stack[top];
            if ((c == ')' && topChar != '(') ||
                (c == '}' && topChar != '{') ||
                (c == ']' && topChar != '[') ||
                (c == '>' && topChar != '<')) {
                return false;
            }
            top--;
        }
    }
    return top == -1;
}


int main() {
    char str[MAX_SIZE];
    printf("Input a string: ");
    scanf("%s", str);

    if (isValid(str)) {
        printf("Check bracket in the said string is valid or not? 1\n");
    } else {
        printf("Check bracket in the said string is valid or not? 0\n");
    }

    return 0;
}

```
##
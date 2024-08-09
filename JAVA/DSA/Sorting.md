# Merge sort
 Merge Sort is a popular and efficient sorting algorithm based on the divide-and-conquer principle. It divides the unsorted list into two roughly equal halves, recursively sorts each half, and then merges the two sorted halves back together.
### Merge Sort Algorithm

1. **Divide**: Split the array into two halves.
2. **Conquer**: Recursively sort each half.
3. **Combine**: Merge the two sorted halves to produce a single sorted array.

### Merge Sort in Java

Here is an implementation of Merge Sort in Java:

```java
public class MergeSort {

    // Main function to sort an array using merge sort
    public static void mergeSort(int[] array) {
        if (array.length < 2) {
            return; // Base case: array is already sorted
        }
        
        int mid = array.length / 2;
        int[] left = new int[mid];
        int[] right = new int[array.length - mid];
        
        // Copy data to temporary arrays
        System.arraycopy(array, 0, left, 0, mid);
        System.arraycopy(array, mid, right, 0, array.length - mid);
        
        // Recursively sort the halves
        mergeSort(left);
        mergeSort(right);
        
        // Merge sorted halves
        merge(array, left, right);
    }

    // Merge two sorted arrays
    private static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;
        
        // Merge the two arrays into the original array
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                array[k++] = left[i++];
            } else {
                array[k++] = right[j++];
            }
        }
        
        // Copy remaining elements of left[] if any
        while (i < left.length) {
            array[k++] = left[i++];
        }
        
        // Copy remaining elements of right[] if any
        while (j < right.length) {
            array[k++] = right[j++];
        }
    }

    // Example usage
    public static void main(String[] args) {
        int[] array = {5, 1, 1, 2, 0, 0};
        System.out.println("Original array: ");
        for (int num : array) {
            System.out.print(num + " ");
        }
        System.out.println();

        mergeSort(array);

        System.out.println("Sorted array: ");
        for (int num : array) {
            System.out.print(num + " ");
        }
    }
}
```

### Explanation

1. **`mergeSort(int[] array)`**:
   - Base Case: If the array has fewer than 2 elements, it's already sorted.
   - Divide: Split the array into two halves (`left` and `right`).
   - Recursively sort the two halves by calling `mergeSort` on each half.
   - Merge the sorted halves using the `merge` method.

2. **`merge(int[] array, int[] left, int[] right)`**:
   - Merge two sorted arrays (`left` and `right`) into the original `array`.
   - Use three pointers (`i`, `j`, and `k`) to track positions in `left`, `right`, and `array`, respectively.
   - Compare elements from `left` and `right`, placing the smaller element into `array`.
   - Copy any remaining elements from `left` or `right` into `array`.

### Complexity

- **Time Complexity**: \(O(n \log n)\), where \(n\) is the number of elements. This is because the array is split into halves recursively (logarithmic), and merging takes linear time.
- **Space Complexity**: \(O(n)\) due to the extra space needed for temporary arrays.

Merge Sort is highly effective for sorting large arrays and is a stable sort, meaning it maintains the relative order of equal elements.
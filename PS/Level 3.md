### Topic : Arrays
### Count of array elements divisible by specific number

```C
#include <stdio.h>

int main(){
    int size;
    scanf("%d",&size);
    int nums[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&nums[i]);
    }
    
    int divisor,count=0;
    scanf("%d",&divisor);
    
    for(int i=0;i<size;i++){
        
        if(nums[i]%divisor == 0){
            count++;
        }
        
    }
    
    printf("The array elements divisible by %d is %d",divisor,count );
}
```

### Removing even numbers from an array

```C
#include <stdio.h>

int main(){
    int size;
    scanf("%d",&size);
    
    int nums[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&nums[i]);
    }
    
    int res[size];
    
    for(int i=0;i<size;i++){
        res[i] = 0;
    }
    
    int count = 0;
    for(int i=0;i<size;i++){
        if(nums[i]%2 != 0){
            res[count] = nums[i];
            count++;
        }
    }
    
    for(int i =0;i<size;i++){
        if(res[i] == 0){
            break;
        }else{
            printf("%d\n",res[i]);
        }
    }
}
```

### Give c program to print the number of occurrence of a number in an array

```C
#include <stdio.h>

int main() {
   int size;
   scanf("%d",&size);
   int no;
   scanf("%d",&no);
   int arr[size];
   int count = 0;
   for(int i=0;i<size;i++){
       scanf("%d",&arr[i]);
       if(arr[i] == no){
           count++;
       }
   }
   printf("%d",count);
}   
```

### Sum, product of an array

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
   int size;
   scanf("%d",&size);
   
    int num[size];
   
   for(int i=0;i<size;i++){
       scanf("%d",&num[i]);
   }
   
   int sum = 0;
   for(int i=0;i<size;i++){
       sum+=num[i];
   }
   int prod = 1;
   for(int i=0;i<size;i++){
       prod*=num[i];
   }
   
   printf("Sum : %d\n",sum);
   printf("Pro : %d",prod);
   
}   
```

### Print square of the elements in an array

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
   int size;
   scanf("%d",&size);
   
    int num[size];
   
   for(int i=0;i<size;i++){
       scanf("%d",&num[i]);
   }
   
   for(int i=0;i<size;i++){
       int temp = (num[i]*num[i]);
       printf("%d ",temp);
   }
   
}   
```

### Difference between maximum and minimum element of an array

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
   int size;
   scanf("%d",&size);
   int arr[size];
   for(int i=0;i<size;i++){
       scanf("%d",&arr[i]);
   }
   int max = -1;
   int min = 100000;
   for(int i=0;i<size;i++){
       if(max < arr[i]) max = arr[i];
       if(min > arr[i]) min = arr[i];
   }
   
   printf("%d",max-min);
   
}   
```

### Print negative elements in array

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
   int size;
   scanf("%d",&size);
   
   int arr[size];
   
   for(int i=0;i<size;i++){
       scanf("%d",&arr[i]);
   }
   
   for(int i=0;i<size;i++){
       if(arr[i] < 0) printf("%d ",arr[i]);
   }
   
}   
```

### Print the peak elements in array
`
```C
#include <stdio.h>

int main() {
    int i,j;
    int arr[]={1,2,3,4,3,4,5};
    int n=sizeof(arr)/sizeof(arr[0]);
    for(i=0;i<n;i++){
       if(i==0&&arr[i+1]<arr[i])
            arr[i]=arr[i]+arr[i+1];
        else if(i==n-1&&arr[i]>arr[i-1]){
            arr[i]=arr[i]+arr[i-1];
        }
        else if(arr[i-1]<arr[i]&&arr[i]>arr[i+1]){
            arr[i]=arr[i-1]+arr[i+1];
        }
    }
    return 0;
} 
```

### Find the count of the positive number

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
   int size;
   scanf("%d",&size);
   
   int arr[size];
   
   for(int i=0;i<size;i++){
       scanf("%d",&arr[i]);
   }
   int count = 0;
   for(int i=0;i<size;i++){
       if(arr[i] > 0){
           count++;
       }
   }
   printf("%d",count);
   
}   
```

### Delete the element in the given position in an array
```C
#include<stdio.h>

int main(){
    int size;
    scanf("%d",&size);
    int num[size];
    
    int position;
    scanf("%d",&position);
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=0;i<size;i++){
        if(i == position) continue;
        printf("%d ",num[i]);
    }
}
```

### Find the non prime numbers in an array

```C
#include<stdio.h>

int isPrime(int n){
    if(n == 1 || n == 0) return 0;
    int divi = 2;
    while(divi<n){
        if(n%divi == 0){
            return 0;
        }
        divi++;
    }
    return 1;
}

int main(){
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=0;i<size;i++){
        if(isPrime(num[i]) == 0){
            printf("%d ",num[i]);
        }
    } 
}
```


### replace the peak number by adding it neighbor elements  (example:-   input: 1 2 4 3    output: 1 2 9 3   )

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=1;i<size-1;i++){
        if(num[i-1] < num[i] && num[i+1]<num[i]){
            num[i] = num[i]+num[i-1]+num[i+1];
            break;
        }
    }
    for(int i =0;i<size;i++){
        printf("%d ",num[i]);
    }
}
```

### Array Input range 2-10 if exceeds print "Invalid". print two elements which is the sum of two element closest to 0(zero). 

Input: [-1,-10,8,2] output: [-1 , 2]. Explanation -1+2=-1 is the closest to 0 than other combinations.

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int size;
    scanf("%d",&size);
    int arr[size];
    for(int i=0;i<size;i++){
        scanf("%d",&arr[i]);
    }
    
    int ans[] = {0,0};
    int min = 100000;
    for(int i=0;i<size;i++){
        for(int j=i+1;j<size;j++){
            int no = abs(arr[i]+arr[j]);
            if(no < min || (i==0 && j==1)){
                min = abs(arr[i]+arr[j]);
                ans[0] = i; ans[1] = j;
            }
        }
    }
    printf("%d %d",ans[0],ans[1]);
}
```

### Print the median of an array after sorting

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    for(int i=0;i<size;i++){
        for(int j=i+1;j<size;j++){
            if(arr[i]>arr[j]){
                int a=arr[i];
                arr[i]=arr[j];
                arr[j]=a;
            }
        }
    }
    
    printf("%d",num[size/2]);
}
```

### Print the average of an array
```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    int sum = 0;
    
    for(int i=0;i<size;i++){
        sum+=num[i];
    }
    
    printf("%.2f ",(float)sum / (float)size);
}
```

### Second largest
```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
   for(int i=0;i<size;i++){
        for(int j=i+1;j<size;j++){
            if(num[i]>num[j]){
                int a=num[i];
                num[i]=num[j];
                num[j]=a;
            }
        }
    }
    
    printf("%d",num[size-2]);
    
}
```

### Sort the array in ascending order and print even numbers first and odd numbers

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=0;i<size;i++){
        for(int j=0;j<size-1;j++){
            if(num[j] > num[j+1]){
                int temp = num[j];
                num[j] = num[j+1];
                num[j+1] = temp;
            }
        }
    }
    for(int i=0;i<size;i++){
        if(num[i]%2 == 0) {
            printf("%d ",num[i]);
            break;
        }
    }
    for(int i=0;i<size;i++){
        if(num[i]%2 == 1){
            printf("%d ",num[i]);
            break;
        }
    }
    
}
```

### Remove even number

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=0;i<size;i++){
        if(num[i]%2 != 0) printf("%d ",num[i]);
    }
    
}
```

### Sum the array after removing duplicate elements
```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    int sum1=0;
    for(int i=0;i<size;i++){
        sum1+=num[i];
    }
    
    int sSum = 0;
    for(int i=0;i<size;i++){
        for(int j=i+1;j<size;j++){
            if(num[i] == num [j]){
                sSum+=num[i];
            }
        }
    }
    
    printf("%d",sum1-sSum);
    
}
```

### Sum of duplicates in an array

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size;
    scanf("%d",&size);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    int sSum = 0;
    for(int i=0;i<size;i++){
        for(int j=i+1;j<size;j++){
            if(num[i] == num [j]){
                sSum+=num[i];
            }
        }
    }
    
    printf("%d",sSum);
}
```
### Array chunking 

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int size,k;
    scanf("%d",&size);
    scanf("%d",&k);
    int num[size];
    
    for(int i=0;i<size;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=0;i<size;i=i){
        for(int j=0;j<k;j++){
            printf("%d ",num[i]);
            i++;
            if(i==size) break;
        }
        printf("\n");
    }
    
}
```
### Remove continue duplicates

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int n;
    scanf("%d",&n);
    int num[n];
    for(int i=0;i<n;i++){
        scanf("%d",&num[i]);
    }
    
    for(int i=0;i<n;i++){
        if(num[i] != num[i+1]) printf("%d",num[i]);
    }
    //printf("%d",num[n-1]);
    
}
```
### Maximum sum of the array

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int n;
    scanf("%d",&n);
    int num[n];
    for(int i=0;i<n;i++){
        scanf("%d",&num[i]);
    }
    
    int sum = num[0];
    int max = sum;
    
    for(int i=1;i<n;i++){
        sum += num[i];
        if(max < sum) max = sum;
    }
    printf("%d",max);
}
```

### Maximum count of the duplicate

```C
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int n;
    scanf("%d",&n);
    int num[n];
    for(int i=0;i<n;i++){
        scanf("%d",&num[i]);
    }
    
    int arr[n];
    
    for(int i=0;i<n;i++){
        arr[i] = 1;
    }
    
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(num[i] == num[j]){
                arr[j] = arr[j]+1;
            }
        }
    }
    
    int max = -1; int count=0;
    for(int i=0;i<n;i++){
        if(arr[i] == 1) continue;
        if(arr[i] == max) count++;
        if(arr[i] > max){
            max = arr[i];
            count=1;
        }
    }
    
    for(int i=0;i<count;i++){
        printf("%d ",max);
    }
    
}
```
### Matrix Multipilcation
```c
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int arr[3][3]={{1,2,3},{4,5,6},{7,8,9}};
    int a[3][3];
    int n = sizeof(arr) / sizeof(arr[0]);
    int m = sizeof(arr[0]) / sizeof(arr[0][0]);
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            int sum=0;
            for(int k=0;k<m;k++){
               sum+=arr[i][k]*arr[k][j];
            }
            a[i][j]=sum;
        }
    }
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
           printf("%d ",a[i][j]);
    }
    printf("\n");
}
  return 0;
}

```
### chunk 
```java
#include<stdio.h>
int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
   
    printf("The entered array is: ");
    for(int i=0;i<n;i++){
        printf("%d ",arr[i]);
    }
   
    int size=2;
    for(int i=0;i<n;i+=size){
        printf("[");
        for(int j=i;j<i+size && j<n;j++){
            printf("%d",arr[j]);
            if(j<i+size-1 && j<n-1){
                printf(",");
            }
        }
        printf("]");
        if(i<n-2){
            printf(",");
        }
    }
}
```
### given degree as input, convert it into radian and store it in an array and then print the cosine values of the radian
```java
#include <stdio.h>
#include <math.h>

#define MAX_DEGREES 100

int main() {
    int n;
    
    // Read the number of degrees
    printf("Enter the number of degrees: ");
    scanf("%d", &n);
    
    // Ensure the number of degrees does not exceed the maximum limit
    if (n > MAX_DEGREES) {
        printf("Error: Number of degrees exceeds maximum limit.\n");
        return 1;
    }
    
    // Read the degrees and convert them into radians
    double radians[MAX_DEGREES];
    printf("Enter the degrees:\n");
    for (int i = 0; i < n; i++) {
        double degree;
        scanf("%lf", &degree);
        radians[i] = degree * M_PI / 180.0; // Convert degrees to radians
    }
    
    // Print the cosine values of the radian angles
    printf("Cosine values:\n");
    for (int i = 0; i < n; i++) {
        printf("cos(%.2f°) = %.4f\n", radians[i] * 180.0 / M_PI, cos(radians[i]));
    }
    
    return 0;
}

```


# Example
## Age and Name
 ```java
public class Main {  
    public static void main(String[] args) {  
        System.out.println("Enter ur name and age: ");  
        Scanner I = new Scanner(System.in);  
        System.out.println(I.nextLine()+"! you are "+I.nextInt()+"years Old");  
  
    }  
}
```
![[Screenshot 2024-02-01 222319.png]]

## Age ,gender and Room no
```java
 Scanner age = new Scanner(System.in);  
    int Age =age.nextInt();  
    if(Age>=18 ){  
        System.out.println("You are eligible to Vote");  
        System.out.println("Enter Your Gender ");  
        Scanner Name = new Scanner(System.in);  
        String name = Name.nextLine();  
        if(name.equals("Female"))  
            System.out.println("Go to room no: 3");  
        else{  
            System.out.println("Go to room no 4");  
        }}  
    else {  
        System.out.println("You are not eligible to vote");  
    }  
```
## Name , Age and Adult Or NOt
```java
public static void main(String[] args) {  
    Scanner scanner=new Scanner(System.in);  
    System.out.println("What is your Name");  
    String Name =scanner.nextLine();  
    System.out.println("Hello! "+Name);  
    System.out.println("What is your Age");  
    int Age = scanner.nextInt();  
   int year =  LocalDate.now().minusYears(Age).getYear();  
    System.out.println("You were born in"+year);  
    if(Age>=18){  
        System.out.println("You are an  adult :)");  
    }  
    else {  
        System.out.println("You are not an  adult :(");  
    }  
}
```
![[Pasted image 20240207111943.png]]
## Find number of occurrence of given number
```java
  
public class Main {  
    public static void main(String[] args) {  
        Scanner n = new Scanner(System.in);  
        System.out.print("Enter the number: ");  
        int N=n.nextInt();  
        int rem,count = 0;  
        System.out.print("Enter the no to be count: ");  
        int s = n.nextInt();  
        while (N > 0) {  
            rem=N%10;  
            if(rem==s){  
                count++;  
            }  
            N/=10;  
        }  
        System.out.println(+s+" Occur "+count+" times");  
    }  
}
```
![[Pasted image 20240307230801.png]]
# Lucky number
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    System.out.println("Enter a 4 Digit Number :");  
    int N = n.nextInt();  
   int FirstDigit=(N/1000)%10;  
   int SecondDigit=(N/100)%10;  
   int ThirdDigit=(N/10)%10;  
   int FourthDigit=N%10;  
   String result =(FirstDigit+SecondDigit)==(ThirdDigit+FourthDigit)?"Lucky Number":"NOT Lucky Number";  
    System.out.println(result);  
}
```
![[Pasted image 20240214144726.png]]

# LOOPS
#LOOPS
## STOPS WHEN SUM OF NOS EXCEED 100
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    int sum=0;  
    while(sum<100){  
        System.out.print("Enter a Number: ");  
  
        sum+=n.nextInt();  
    }  
    System.out.println("Done: "+sum);  
}
```
![[Pasted image 20240215151626.png]]
## Vowels and Non-Vowels Count
```java
public class Main {  
  
    public static void main(String[] args) {  
        Scanner scanner = new Scanner(System.in);  
        System.out.print("Enter a String:  ");  
        String n = scanner.nextLine();  
        int sum =0,count=0;  
        for(int i=0;i<n.length();i++){  
            if(n.charAt(i)!='a'&& n.charAt(i)!='i'&&n.charAt(i)!='e'&& n.charAt(i)!='u'&&n.charAt(i)!='o'&&n.charAt(i)!='A'&&n.charAt(i)!='E'&&n.charAt(i)!='I'&&n.charAt(i)!='O'&&n.charAt(i)!='U'){  
                sum+=1;  
            }else{  
                count++;  
            }  
            }  
        System.out.println("No of VOWEL LETTERS: "+count);  
        System.out.println("No of NON-VOWEL LETTERS: "+sum);  
    }  
}
```
![[Pasted image 20240215213712.png]]
# sum of each digits in Number
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    System.out.print("Enter a number: ");  
    int s= n.nextInt();  
    int sum =0;  
    while(s>0){  
        sum+=s%10;  
        s/=10;  
    }  
    System.out.println("Sum of digit = "+sum);  
}
```
![[Pasted image 20240215155844.png]]
# Fibonnacci
### own(printing series and sum of series)
```java
public class Main {  
    public static void  main(String[] args) {  
        Scanner n = new Scanner(System.in);  
        System.out.print("Enter the number of terms you want in the Fibonacci sequence: ");  
        int s = n.nextInt();  
        int Result = 0, N1 = 0, N2 = 1,sum=0;  
        for (int i = 1; i <= s; i++) {  
            if (i == 1) {  
                System.out.print(N1+" ");  
                sum+=N1;  
            } else if (i== 2) {  
                System.out.print(N2+" ");  
                sum+=N2;  
            } else {  
                Result = N1 + N2;  
                System.out.print( Result+" ");  
                sum+=Result;  
                N1 = N2;  
                N2 = Result;  
            }   
        }  
        System.out.println("\n SUM OF FIBONACCI SERIES = "+sum);  
    }  
}
```
![[Pasted image 20240215193249.png]]
### By calling Method
```java
import java.util.Scanner;

public class Fibonacci {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the number of terms you want in the Fibonacci sequence: ");
        int n = scanner.nextInt();
        
        System.out.println("Fibonacci Sequence:");
        for (int i = 0; i < n; i++) {
            System.out.print(fibonacci(i) + " ");
        }
        
        scanner.close();
    }

    public static int fibonacci(int n) {
        if (n == 0) {
            return 0;
        } else if (n == 1) {
            return 1;
        } else {
            int prev = 0;
            int current = 1;
            int next = 1;
            for (int i = 2; i <= n; i++) {
                next = prev + current;
                prev = current;
                current = next;
            }
            return next;
        }
    }
}
```
### **Another method**(by calling method)
```java
import java.util.Scanner;

public class Fibonacci {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the number of terms you want in the Fibonacci sequence: ");
        int n = scanner.nextInt();
        
        System.out.println("Fibonacci Sequence:");
        for (int i = 0; i < n; i++) {
            System.out.print(fibonacci(i) + " ");
        }
    }

    public static int fibonacci(int n) {
        if (n <= 1) {
            return n;
        } else {
            return fibonacci(n - 1) + fibonacci(n - 2);
        }
    }
}

```


## Find nth Number in fibonacci(without recursion)
### wihtout ternary
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner n = new Scanner(System.in);  
        System.out.print("Enter the nth fibonacci ");  
        int s = n.nextInt();  
        int  N1 = 0, N2 = 1;  
        if(s==1){  
            System.out.println(N1);  
            System.exit(0);  
        } else if (s==2) {  
            System.out.println(N2);  
            System.exit(0);  
        }  
        for (int i = 3; i <= s; i++) {  
            int temp=N2;  
         N2=N2+N1;  
         N1=temp;  
        }  
        System.out.println("\n THE "+s+"th NUMBER OF FIBONACCI SERIES = " + N2);  
    }  
}
```
### using Ternary Operator
```java
package com.prakii;

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner n = new Scanner(System.in);
        System.out.print("Enter the nth Fibonacci term: ");
        int s = n.nextInt();
        int N1 = 0, N2 = 1;

        for (int i = 3; i <= s; i++) {
            int temp = N2;
            N2 = N2 + N1;
            N1 = temp;
        }

        int nthFibonacci = (s == 1) ? N1 : N2; // Handling the case when s is 1

        System.out.println("\nThe " + s + "th Fibonacci term = " + nthFibonacci);
    }
}

```
![[Pasted image 20240307224536.png]]
# Armstrong Number
```java
public static void main(String[] args) {  
    Scanner n=new Scanner(System.in);  
    int OriginalNo= n.nextInt();  
    int N=OriginalNo;  
    String num =Integer.toString(N);  
    int sizeofN = num.length(),Armstrong=0;  
    while(N>0){  
            int rem = N % 10;  
            Armstrong += Math.pow(rem, sizeofN);  
            N /= 10;  
    }  
    String Arm=Armstrong==OriginalNo?"Given no is Armstrong Number":"Not Armstrong";  
    System.out.println(Arm);  
}
```
![[Pasted image 20240313223000.png]]
## Using Method
```java
public static void main(String[] args) {  
    Scanner n=new Scanner(System.in);  
    int N= n.nextInt();  
	System.out.println(isArmstring(N)); 
}  
private static boolean isArmstring(int n) {  
    String num =Integer.toString(n);  
    int sizeofn = num.length(),Armstrong=0,OriginalNo=n;  
    while(n>0){  
        int rem = n % 10;  
        Armstrong += Math.pow(rem, sizeofn);  
        n /= 10;  
    }  
    return Armstrong==OriginalNo;  
}
```
![[Pasted image 20240313223710.png]]
## Print all Amstrong Number In Certain Range
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner n=new Scanner(System.in);  
        System.out.print("Enter the in Range for Armstrong:");  
        int M1=n.nextInt();  
        int M2=n.nextInt();  
        System.out.print("Armstrong Number btw "+M1+" And "+M2+" Are:");  
        for(int i=M1;i<M2;i++){  
            if (isArmstrong(i)) {  
                System.out.print(i+" ");  
            }  
        }  
    }  
    private static boolean isArmstrong(int n) {  
        String num =Integer.toString(n);  
        int sizeofn = num.length(),Armstrong=0,OriginalNo=n;  
        while(n>0){  
            int rem = n % 10;  
            Armstrong += Math.pow(rem, sizeofn);  
            n /= 10;  
        }  
        return Armstrong==OriginalNo;  
    }
```
![[Pasted image 20240313225235.png]]
# PATTERN PRINTING
#PATTERNPRINTING
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    for(int i=1;i<=N;i++){  
        for(int j=1;j<=i;j++){  
            System.out.print(i+" ");  
        }  
        System.out.println();  
    }  
}
```
![[Pasted image 20240216210415.png]]
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    int num=1;
    for(int i=1;i<=N;i++){  
        for(int j=1;j<=i;j++){  
            System.out.print(num + " ");  
            num++;
        }  
        System.out.println();  
    }  
}
```
![[Pasted image 20240222072554.png]]

```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    int n = 65;
    if(N>0){
        for (int i = 1; i<=N;i++){
            for(int j=1;j<=i;j++){
                System.out.print("%c ",n);
                n++;
            }
             System.out.print();
        } 
}
```
![[Pasted image 20240222071908.png]]

```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    for(int i=1;i<=N;i++){  
        for(int j=1;i>=j;j++){  
            System.out.print("* ");  
        }  
        System.out.println();  
    }  
}
```
![[Pasted image 20240216212921.png]]
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    for(int i=1;i<=N;i++){  
        for(int j=0;j<=N-i;j++){  
            System.out.print("* ");  
        }  
        System.out.println();  
    }  
}
```
![[Pasted image 20240216224142.png]]
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    for(int i=1;i<=N;i++){  
        for(int j=1;j<=N-i;j++){  
            System.out.print("  ");  
        }for(int j=1;j<=i;j++){  
        System.out.print("* ");  
    }  
        System.out.println();  
    }  
}
```
![[Pasted image 20240216212744.png]]

```java
    public static void main(String[] args) {  
        Scanner n =new Scanner(System.in);  
        int N = n.nextInt();  
for(int i = 1;i<=N;i++){  
    for(int j=1;j<=N-i;j++){  
        System.out.print(" ");  
    }for(int k=1;k<=i;k++){  
        System.out.print("* ");  
    }  
    System.out.println();  
}  
    }
```
![[Pasted image 20240208215921.png]]
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
   for(int i =N;i>=1;i--){  
    for(int j=1;j<=N-i;j++){  
        System.out.print("  ");  
    }for(int k=1;k<=i;k++){  
        System.out.print("* ");  
    }  
    System.out.println();  
}
}
```
![[Pasted image 20240216220804.png]]
```java
    public static void main(String[] args) {  
        Scanner n =new Scanner(System.in);  
        int N = n.nextInt();  
for(int i =N;i>=1;i--){  
    for(int j=1;j<=N-i;j++){  
        System.out.print(" ");  
    }for(int k=1;k<=i;k++){  
        System.out.print("* ");  
    }  
    System.out.println();  
}  
    }
```
![[Pasted image 20240208220021.png]]
```java
    public static void main(String[] args) {  
        Scanner n =new Scanner(System.in);  
        int N = n.nextInt();  
for(int i = 1;i<=N;i++){  
    for(int j=1;j<=N-i;j++){  
        System.out.print(" ");  
    }for(int k=1;k<=2*i-1;k++){  
        System.out.print("*");  
    }  
    System.out.println();  
}  
    }
```
![[Pasted image 20240216221256.png]]
```java
    public static void main(String[] args) {  
        Scanner n =new Scanner(System.in);  
        int N = n.nextInt();  
for(int i = 1;i<=N;i++){  
    for(int j=1;j<=N-i;j++){  
        System.out.print("  ");  
    }for(int k=1;k<=2*i-1;k++){  
        System.out.print("*");  
    }  
    System.out.println();  
}  
    }

```
![[Pasted image 20240216221329.png]]
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    for(int i=1;i<=N;i++){  
        for(int j=1;j<=N-i;j++){  
            System.out.print(" ");  
        }for(int j=1;j<=2*i-1;j++){  
            if(i==N)  
                System.out.print("*");  
            else if(j==1||j==2*i-1)  
                 System.out.print("*");  
            else  
                System.out.print(" ");  
        }  
        System.out.println();  
    }  
}
```
```java
public static void main(String[] args) {  
    Scanner s = new Scanner(System.in);  
    System.out.print("Enter an Int: ");  
    int n = s.nextInt();  
    for(int i = 1; i <= n; i++){  
        for(int j = n; j > i; j--)  
            System.out.print(" ");  
        System.out.print("*");  
        for(int x = 1; x < (i * 2) - 2; x++)  
            System.out.print(i == n ? "*" : " ");  
        if(i != 1)  
            System.out.print("*");  
        System.out.println();  
    }  
}
```
![[Pasted image 20240216223522.png]]
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.print("Enter the Number: ");  
    int N=scanner.nextInt();  
    for(int i=1;i<=N;i++){  
        for(int j=1;j<=N;j++){  
            System.out.print("* ");  
        }  
        System.out.println();  
    }  
}
```
![[Pasted image 20240216224312.png]]
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner scanner = new Scanner(System.in);  
        System.out.print("Enter the Number: ");  
        int N=scanner.nextInt();  
        for(int i=1;i<=N;i++){  
            for(int j=1;j<=N;j++)  
                if(i==1||i==N)  
                    System.out.print("* ");  
                 else  
                     if(j==1||j==N)  
                         System.out.print("* ");  
                      else  
                         System.out.print("  ");  
             System.out.println();  
        }  
    }
```
![[Pasted image 20240217211925.png]]
# FACTORIAL
#FACTORIAL
## Using do While: 
```JAVA
public class Main {  
    public static void main(String[] args) {  
        Scanner n =new Scanner(System.in);  
        int N = n.nextInt();  
        int Factorial  =1;  
        int No = N;  
	do{  
    Factorial*=N;  
    N--;  
    }
	while(N>=1);  
        System.out.println("FACTORIAL OF "+ No +" =  "+Factorial);  
    }  
}
```
# Palindrome
## (string)
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.println("Enter the String: ");  
    String N = scanner.nextLine();  
    boolean ispalindrome=true;  
    for(int i=0,j=N.length()-1;i<j;i++,j--){  
        if(N.charAt(i) == N.charAt(j)){  
            continue;  
        }  
            ispalindrome=false;  
            break;  
          
    }  
    System.out.println(ispalindrome?"Palindrome":"Not Palindrome");  
}
```
![[Pasted image 20240215225243.png]]
# Perfect No
#PerfectNo
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner n =new Scanner(System.in);  
        int N = n.nextInt();  
        int sum=0;  
        for(int i=1;i<N;i++){  
            if(N%i==0){  
                 sum+=i;  
            }  
        }
        
    }  
	String result = (sum == N) ? "Perfect Number" : "Not Perfect Number";
	System.out.println(N + " is " + result);
}
```
![[Pasted image 20240212210406.png]]
![[Pasted image 20240212210441.png]]
# Reverse
## Number
#ReverseNumber
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.println("Enter the Number:");  
    int N = scanner.nextInt();  
    int reversed = 0;  
  
    while (N > 0) {  
        int digit = N % 10;  
        reversed = reversed * 10 + digit;  
        N /= 10;  
    }  
  
    System.out.println("Reversed Number: " + String.format("%04d", reversed));  
}
```
![[Pasted image 20240212215401.png]]
## String
```java
public static void main(String[] args) {  
    Scanner scanner = new Scanner(System.in);  
    System.out.println("Enter the String: ");  
    String N = scanner.nextLine();  
    System.out.println("Reversed string: ");  
    for(int i=N.length()-1;i>=0;i--){  
        System.out.print(N.charAt(i));  
    }  
}
```
![[Pasted image 20240215222756.png]]
# LCM and GCD
## LCM (simple)
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner n=new Scanner(System.in);  
        System.out.print("Enter 2 Numbers: ");  
        int a = n.nextInt(),b=n.nextInt();  
        int ans=a>b?a:b;  
        while(true){  
            if(ans%a==0 && ans%b==0)  
                break;  
            ans++;  
        }  
        System.out.println("LCM of "+a+" and "+b+" = "+ans);  
    }  
}
```
![[Pasted image 20240316085449.png]]
## GCD
```java
  public static void main(String[] args) {  
        Scanner n = new Scanner(System.in);  
        System.out.print("Enter 2 Numbers: ");  
        int a = n.nextInt(), b = n.nextInt();  
        int ans = a > b ? a : b;  
        System.out.println("gcd of " + a + " and " + b + " = " + gcd(a, b));  
    }  
    public static int gcd(int a, int b) {  
        if (b == 0) {  
            return a;  
        }  
        return gcd(b, a % b);  
    }
```
![[Pasted image 20240316090410.png]]
## LCM using Formulae(with GCD)
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    System.out.print("Enter 2 Numbers: ");  
    int a = n.nextInt(), b = n.nextInt();  
    int ans = a > b ? a : b;  
    System.out.println("LCM of " + a + " and " + b + " = " + lcm(a, b));  
}  
  
public static int lcm(int a, int b) {  
    int lcm = a * b / gcd(a, b);  
    return lcm;  
}  
  
public static int gcd(int a, int b) {  
    if (b == 0) {  
        return a;  
    }  
    return gcd(b, a % b);  
}
```
![[Pasted image 20240316090200.png]]
# Pythagorean Triplet
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    System.out.print("Enter size of Array : ");  
    int[] arr = new int[n.nextInt()];  
    System.out.print("Enter the elements : ");  
    for (int i = 0; i < arr.length; i++) {  
        arr[i] = n.nextInt();  
    }  
    String ans;  
    ans = pythogroianTriplet(arr, arr.length) == true ? "Yes, Given array have Pythogorian Triplet " : "NO,  Given array have no Pythogorian Triplet";  
    System.out.println(ans);  
  
}  
  
private static boolean pythogroianTriplet(int ar[], int n) {  
    for (int i = 0; i < n; i++) {  
        for (int j = i + 1; j < n; j++) {  
            for (int k = j + 1; k < n; k++) {  
                // Calculate square of array elements  
                int x = ar[i] * ar[i], y = ar[j] * ar[j], z = ar[k] * ar[k];  
  
                if (x == y + z || y == x + z || z == x + y)  
                    return true;  
            }  
        }  
    }            return false;  
}
```
![[Pasted image 20240319211014.png]]
# Calculator using Switch case
#Calculator
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    double d1 =n.nextDouble();  
    char c=n.next().charAt(0);  
    double d2=n.nextDouble();  
    switch(c){  
        case '+':  
            System.out.println("Answer -> "+(d1 + d2));  
            break;  
        case '-':  
            System.out.println("Answer -> "+(d1- d2));  
            break;  
        case '/':  
            System.out.println("Answer -> "+(d1 / d2));  
            break;  
        case '*':  
            System.out.println("Answer -> "+(d1 * d2));  
        case '%':  
            System.out.println("Answer -> "+(d1 % d2));  
        default:  
            System.out.println("Invalid Operator"); 
    }  
}
```
# Swapping array
#Swapingarray
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
  int N = n.nextInt();  
  int[] amal= new int[N];  
  for(int i=0;i<N;i++){  
      amal[i]=n.nextInt();  
  }  
  int start=0,end=amal.length-1;  
  while(start<end){  
      int temp = amal[start];  
      amal[start++]=amal[end];  
      amal[end--]=temp;  
  }  
  for(int i=0;i<amal.length;i++){  
      System.out.print(amal[i]+" ");  
  }  
}
```
![[Pasted image 20240213213546.png]]
# Array eg:
### +ve nos in even index no and -ve nos in odd index no
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    int N = n.nextInt();  
    int[] amal = new int[N];  
    for (int i = 0; i < N; i++) {  
        amal[i] = n.nextInt();  
    }  
  
    int[] result = new int[N];  
    int p = 0, Neg = 1;  
  
    for (int j = 0; j < amal.length; j++) {  
        if (amal[j] >= 0) {  
            result[p] = amal[j];  
            p += 2;  
        } else {  
            result[Neg] = amal[j];  
            Neg += 2;  
        }  
    }  
    for (int i = 0; i < result.length; i++) {  
        System.out.print(" "+result[i]);  
    }  
}
```
![[Pasted image 20240214111700.png]]
### EVEN numbers after ODD numbers
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    int N = n.nextInt();  
    int[] amal = new int[N];  
    for (int i = 0; i < N; i++) {  
        amal[i] = n.nextInt();  
    }  
  
    int[] result = new int[N];  
    int p = 0, Neg = 1;  
  
    for (int j = 0; j < amal.length; j++) {  
        if (amal[j]/2==0) {  
            result[Neg] = amal[j];  
            Neg += 2;  
        } else {  
            result[p] = amal[j];  
            p += 2;  
        }  
    }  
    for (int i = 0; i < result.length; i++) {  
        System.out.print(" "+result[i]);  
    }  
```
![[Pasted image 20240221204119.png]]
### ![[Pasted image 20240219221552.png]]
#### For numbers
```java
public static void main(String[] args) {  
    System.out.print("Enter array length : ");  
    Scanner scanner = new Scanner(System.in);  
    int n =scanner.nextInt();  
    while(n>20||n<=0){  
        System.out.println("Invalid array lenght enter within 20");  
        n=scanner.nextInt();  
    }  
        int[] arr=new int[n];  
        System.out.println("Enter the Values: ");  
        for(int i=0;i<arr.length;i++) {  
            arr[i] =scanner.nextInt();  
        }  
    System.out.print("The Elements are : ");  
        System.out.print(Arrays.toString(arr));  
}
```
![[Pasted image 20240219215435.png]]}```

#### For Points

```java
public static void main(String[] args) {  
    System.out.print("Enter array length(max 20) : ");  
    Scanner scanner = new Scanner(System.in);  
    int n =scanner.nextInt();  
    while(n>20||n<=0){  
        System.out.println("Invalid array lenght enter within 20");  
        n=scanner.nextInt();  
    }  
        Point[] points=new Point[n];  
        for(int i=0;i<points.length;i++) {  
            System.out.print("Enterx x and y for Points "+(i+1)+":");  
            points[i]=new Point(scanner.nextInt(),scanner.nextInt());  
        }  
    System.out.print("The Points are : ");  
        for(int i=0;i<points.length;i++){  
        System.out.print("("+points[i].x+","+points[i].y+") ");  
        }  
}
```
![[Pasted image 20240219221725.png]]
### ![[Pasted image 20240220214816.png]]
```java
public static void main(String[] args) {  
    Scanner input = new Scanner(System.in);  
    int sum = 0;  
    double product = 1, average = 0;   
    System.out.print("Enter the size of Array: ");  
    int n = input.nextInt();  
    int[] arr = new int[n];  
    System.out.print("Enter the elements:");  
    for (int i = 0; i < arr.length; i++) {  
        arr[i] = input.nextInt();  
    }  
    for (int i = 0; i < arr.length; i++) {  
        sum += arr[i];  
        product *= arr[i];  
    }  
    average = (double) sum / n;   
    System.out.println("Sum:" + sum + " , Product:" + product + " , Average:" + average);  
}
```
![[Pasted image 20240220214906.png]]
### ![[Pasted image 20240220220640.png]]
```java
public static void main(String[] args) {  
    Scanner input = new Scanner(System.in);  
    System.out.print("Enter the size of Array: ");  
    int n = input.nextInt();  
    int[] arr = new int[n];  
    System.out.print("Enter the elements:");  
    for (int i = 0; i < arr.length; i++) {  
        arr[i] = input.nextInt();  
    }  
    System.out.print("Enter to be search:");  
    int searchNumber= input.nextInt();  
    int count=Searchnumber(arr,searchNumber);  
    System.out.println(searchNumber + " is occurs :" + count + " times");  
}  
private static int Searchnumber(int[] arr, int searchNumber) {  
    int count = 0;  
    for (int Arr : arr) {  
        if (searchNumber == Arr) {  
            count++;  
        }  
    }     return count;  
}
```
![[Pasted image 20240220220716.png]]
### Max & Min of element of Array
```java
public static void main(String[] args) {  
    Scanner input = new Scanner(System.in);  
    System.out.print("Enter the size of Array: ");  
    int n = input.nextInt();  
    int[] arr = new int[n];  
    System.out.print("Enter the elements:");  
    for (int i = 0; i < arr.length; i++) {  
        arr[i] = input.nextInt();  
    }  
    int Max=arr[0],Min=arr[0];  
    for (int i = 1; i < arr.length; i++) {  
        Max=(arr[i]>Max)?arr[i]:Max;  
        Min=(arr[i]<Min)?arr[i]:Min;  
    }  
    System.out.println("Max no:" + Max + " & Min no:" + Min);  
}
```
![[Pasted image 20240220224157.png]]
# 2D Array
## Sum of elements along row And column
### Along Row
```java
public static void main(String[] args) {  
    Scanner input =new Scanner(System.in);  
    System.out.print("Enter the Row And Column:");  
    int n1= input.nextInt();  
    int n2 = input.nextInt();  
    int[][] arr=new int[n1][n2];  
    System.out.print("Enter the elements: ");  
    for(int i=0;i<arr.length;i++) {  
        for (int j = 0; j < arr[i].length; j++) {  
            arr[i][j] = input.nextInt();  
        }  
    }  
    for(int i=0;i<arr.length;i++) {  
        int sum=0;  
        for (int j = 0; j < arr[i].length; j++) {  
            sum+=arr[i][j];  
        }  
        System.out.println("Sum of Row " + (i+1) + " : " + sum);  
    }  
}
```
![[Pasted image 20240221212017.png]]
### Along Column
```java
public static void main(String[] args) {  
    Scanner input =new Scanner(System.in);  
    System.out.print("Enter the Row And Column:");  
    int n1= input.nextInt();  
    int n2 = input.nextInt();  
    int[][] arr=new int[n1][n2];  
    System.out.print("Enter the elements: ");  
    for(int i=0;i<arr.length;i++) {  
        for (int j = 0; j < arr[i].length; j++) {  
            arr[i][j] = input.nextInt();  
        }  
    }  
    for(int i=0;i<arr[i].length;i++) {  
        int sum=0;  
        for (int j = 0; j < arr.length; j++) {  
            sum+=arr[j][i];  
        }  
        System.out.println("Sum of Column " + (i+1) + " : " + sum);  
    }  
}
```
![[Pasted image 20240221212430.png]]
## Max And Min Along each Row and Column
### Along Row
```java
public static void main(String[] args) {  
    Scanner input =new Scanner(System.in);  
    System.out.print("Enter the Row And Column:");  
    int n1= input.nextInt();  
    int n2 = input.nextInt();  
    int[][] arr=new int[n1][n2];  
    System.out.print("Enter the elements: ");  
    for(int i=0;i<arr.length;i++) {  
        for (int j = 0; j < arr[i].length; j++) {  
            arr[i][j] = input.nextInt();  
        }  
    }  
    for(int i=0;i<arr.length;i++) {  
        int Max=arr[i][0];  
        int Min=arr[i][0];  
        for (int j = 0; j < arr[i].length; j++) {  
           Max=(arr[i][j]>Max)?arr[i][j]:Max;  
           Min=(arr[i][j]<Min)?arr[i][j]:Min;  
        }  
        System.out.println("Maximum Along Row" + (i+1) + " : " + Max);  
        System.out.println("Minimum Along Row" + (i+1) + " : " + Min);  
    }  
}
```
![[Pasted image 20240221213847.png]]
### Along Column
```java
public static void main(String[] args) {  
    Scanner input =new Scanner(System.in);  
    System.out.print("Enter the Row And Column:");  
    int n1= input.nextInt();  
    int n2 = input.nextInt();  
    int[][] arr=new int[n1][n2];  
    System.out.print("Enter the elements: ");  
    for(int i=0;i<arr.length;i++) {  
        for (int j = 0; j < arr[i].length; j++) {  
            arr[i][j] = input.nextInt();  
        }  
    }  
    for(int i=0;i<arr[i].length;i++) {  
        int Max=arr[i][0];  
        int Min=arr[i][0];  
        for (int j = 0; j < arr.length; j++) {  
           Max=(arr[j][i]>Max)?arr[j][i]:Max;  
           Min=(arr[j][i]<Min)?arr[j][i]:Min;  
        }  
        System.out.println("Maximum Along Column " + (i+1) + " : " + Max);  
        System.out.println("Minimum Along Column " + (i+1) + " : " + Min);  
    }  
}
```
![[Pasted image 20240221214229.png]]
# Array List
## Unique Elements
### Way1:
```java
public static <Set> void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    ArrayList<Integer> unique = new ArrayList<>();  
    System.out.print("Enter the number of elements: ");  
    int numberOfElements = n.nextInt();  
    System.out.print("Enter the Elements:");  
  
    for (int i = 0; i < numberOfElements; i++) {  
        int element = n.nextInt();  
        unique.add(element);  
    }  
    java.util.Set<Integer> uniqueSet = new HashSet<>(unique);  
    unique.clear();  
    unique.addAll(uniqueSet);  
    Collections.sort(unique);  
    System.out.println("Your Unique Sorted Array: " + unique);  
}
```
### Way2:
```java
public static <Set> void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    ArrayList<Integer> unique = new ArrayList<>();  
    System.out.print("Enter the number of elements: ");  
    int numberOfElements = n.nextInt();  
    System.out.print("Enter the Elements:");  
  
    for (int i = 0; i < numberOfElements; i++) {  
        int element = n.nextInt();  
        unique.add(element);  
    }  
    java.util.Set<Integer> uniqueSet = new HashSet<>(unique);  
    unique.clear();  
    unique.addAll(uniqueSet);  
    Collections.sort(unique);  
    System.out.println("Your Unique Sorted Array: " + unique);  
}
``` 
![[Pasted image 20240222214557.png]]
## ![[Pasted image 20240222221532.png]]
```java
public static void main(String[] args) {  
    Scanner n = new Scanner(System.in);  
    ArrayList<Integer> menuList = new ArrayList<>();  
  
    while (true) {  
        System.out.println("1. ADD\n2. REMOVE\n3. DISPLAY\n4. Exit");  
        System.out.print("Enter your choice: ");  
        switch (n.nextInt()) {  
            case 1:  
                System.out.println("Enter the element to ADD: ");  
                menuList.add( n.nextInt());  
                break;  
            case 2:  
                System.out.println("Enter the Element to Remove: ");  
                int remove = n.nextInt();  
                if (menuList.contains(remove)) {  
                    menuList.remove(Integer.valueOf(remove)); // Remove the specific value, not the index  
                } else {  
                    System.out.println("Not found");  
                }  
                break;  
            case 3:  
                System.out.println("Your Array list: " + menuList);  
                break;  
            case 4:  
                System.out.println("Exiting the program.");  
                System.exit(0); // Terminate the program  
  
            default:  
                System.out.println("Invalid choice. Please enter a valid option.");  
        }  
    }  
}
```
![[Pasted image 20240222221753.png]]
![[Pasted image 20240222221811.png]]
# Method 
## Prime no
```java
public static void main(String[] args) {  
    System.out.print("Enter your Range : ");  
    Scanner scanner = new Scanner(System.in);  
    int n1 = scanner.nextInt(), n2 = scanner.nextInt();  
    Primenumber(n1, n2);  
}  
  
public static void Primenumber(int n1, int n2) {  
    for (int i = n1; i <= n2; i++) {  
        if (isPrime(i)) {  
            System.out.print(i + " ");  
        }  
    }  
}  
public static boolean isPrime(int i) {  
    for (int j = 2; j <= i / 2; j++) {  
        if (i <= 2)  
            return false;  
            if (i % j == 0)  
                return false;  
    } return true;  
}
```
![[Pasted image 20240218210900.png]]
``
## Example 1(Total mark percentage)
```java
public class Main {  
    public static void main(String[] args) {  
        double percetage=markpercentage(75,43,90,300);  
        System.out.println(percetage);  
    }  
    private static double markpercentage(int sub1,int sub2,int sub3,int totalmark)  
    {  
        double markscored = sub1 + sub2 + sub3;  
        double percentage = (markscored/totalmark)*100;  
        return percentage;  
    }  
  
    }
```
![[Pasted image 20240130214257.png]]
## EXAMPLE 2 (char search count)
```java
public static void main(String[] args) {  
    char[] Alphapets = {'A', 'A', 'B', 'C', 'D', 'D', 'D'};  
    int count = Alpha(Alphapets, 'D');  
    System.out.println(count);  
}  
public static int Alpha(char[] Alphapets, char searchletter) {  
    int count = 0;  
    for (char alphapet : Alphapets) {  
        if (alphapet == searchletter) {  
            count++;  
        }  
    }  
    return count;  
}
```
![[Pasted image 20240207115619.png]]
## Largest and Smallest Among 3 Numbers
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner n=new Scanner(System.in);  
        System.out.print("Enter 3 Numbers: ");  
        int firstNo= n.nextInt(),secondNo=n.nextInt(),thirdNo=n.nextInt();  
        int max=Maxno(firstNo,secondNo,thirdNo);  
        int min=Minno(firstNo,secondNo,thirdNo);  
        System.out.println("Largest Number among "+firstNo+","+secondNo+","+thirdNo+" = "+max);  
        System.out.println("Smallest Number among "+firstNo+","+secondNo+","+thirdNo+" = "+min);  
    }  
  
    private static int Minno(int firstNo, int secondNo, int thirdNo) {  
        int min = firstNo;  
        if(secondNo<min)  
            min = secondNo;  
        if(thirdNo<min)  
            min = thirdNo;  
        return min;  
    }  
  
    private static int Maxno(int firstNo, int secondNo, int thirdNo) {  
        int max = firstNo;  
        if(secondNo>max)  
            max = secondNo;  
        if(thirdNo>max)  
            max = thirdNo;  
        return max;  
    }  
}
```
# Class And Object
## Passport Prblm
```java
public static void main(String[] args) {  
  Passport ukPassport = new Passport("323","UK",LocalDate.of(2025,02,24));  
  Passport usPassport = new Passport("123","USA",LocalDate.of(2026,9,26));  
  Passport indiaPassport = new Passport("123","INDIA",LocalDate.of(2029,12,23));  
    System.out.println("UK passport");  
    System.out.println(ukPassport.Number);  
    System.out.println(ukPassport.Country);  
    System.out.println(ukPassport.Expirydate);  
    System.out.println();  
    System.out.println("USA Passport");  
    System.out.println(usPassport.Number);  
    System.out.println(usPassport.Country);  
    System.out.println(usPassport.Expirydate);  
    System.out.println();  
    System.out.println("INDIA passport");  
    System.out.println(indiaPassport.Number);  
    System.out.println(indiaPassport.Country);  
    System.out.println(indiaPassport.Expirydate);  
}  
static class Passport{  
    String Number;  
    String Country;  
    LocalDate Expirydate;  
    Passport(String Number ,String Country,LocalDate Expirydate){  
      this.Number=Number;  
      this.Country=Country;  
      this.Expirydate=Expirydate;  
    }  
  
}
```
![[Pasted image 20240207214343.png]]
## Quadrant
```java
public static void main(String[] args) {  
 Scanner Quadrant= new Scanner(System.in);  
 int x= Quadrant.nextInt();  
 int y=Quadrant.nextInt();  
 if(x>0&&y>0){  
     System.out.println("QUADRANT 1");  
 }  
 else if (x<0&&y>0){  
     System.out.println("QUADRANT 2");  
 }  
 else if (x<0&&y<0){  
     System.out.println("QUADRANT 3");  
 }  
 else if (x>0&&y<0){  
     System.out.println("QUADRANT 4");  
 }  
 else if (x==0 && y==0){  
     System.out.println("ORIGIN");  
 }  
 else{  
     System.out.println("defualt");  
 }  
  
}
```
![[Pasted image 20240208210641.png]]


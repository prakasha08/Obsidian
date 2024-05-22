# Structure
#Structure
![[Pasted image 20240123144603.png]]
## Public Static void
-  Is an Method
-  Entry for a program.       
# Shortcut Keywords
- Sout + tab -> System .out. println.
# VARIABLES AND ITS SIZE
#VARIABLESANDITSSIZE
- ![[Pasted image 20240124103502.png]]
## Variable Declaration
![[Pasted image 20240124102622.png]]

# OPERTORS
#OPERTORS
## ARITHMETIC OPERTORS

 ![[Screenshot 2024-01-24 104511.png]]
![[Screenshot 2024-01-24 104540.png]]
###  **Increment
![[Screenshot 2024-01-24 105622.png]]
![[Screenshot 2024-01-24 105638.png]]
### Decrement
![[Screenshot 2024-01-24 105802.png]]
![[Screenshot 2024-01-24 105815.png]]
- x+=1->x=x+1
- x-=1->x=x-1
## Comparison operators
- it retrieves only Boolean Values as output.
- it compares to values
- ![[Screenshot 2024-01-30 130313.png]]
- ![[Screenshot 2024-01-30 130335.png]]
- ![[Pasted image 20240130130612.png]]
# String
#String
```java
String I="Its";  
String P="_Prakii";  
String Prakii=I+P;  
    System.out.println(I);  
    System.out.println(P);  
    System.out.println(Prakii);  
    System.out.println(Prakii.toUpperCase());  
    System.out.println(Prakii.toLowerCase());  
    System.out.println(Prakii.substring(4));  
    System.out.println("A".isBlank());  
    System.out.println("  ".isBlank());  
    System.out.println(" ".isEmpty());  
    System.out.println("".isEmpty());  
    System.out.println("    a    ");  
    System.out.println("    a    ".trim());
```
o/p
- ![[Screenshot 2024-01-30 150714.png]]
# Arrays
#Arrays
```java
public static void main(String[] args) {  
    int[] num1= new int[2];  
    num1[0]=1;  
    num1[1]=2;  
    System.out.println(Arrays.toString(num1));  
    System.out.println(num1.length);  
    int[] num2={0,1,2,3,4,5};  
    System.out.println(Arrays.toString(num2));  
    num2[0]=1;  
    System.out.println(Arrays.toString(num2));  
    double[] num3={0,1,2,3,4,5};  
    System.out.println(Arrays.toString(num3));  
    String[] names={"Prakii","ish"};  
    System.out.println(Arrays.toString(names));  
  
}
```
![[Pasted image 20240130154902.png]]
### 0  and Null in array
```java
public static void main(String[] args) {  
    int[] num1= new int[3];  
    num1[0]=1;  
    System.out.println(Arrays.toString(num1));  
    Arrays.fill(num1,-1);  
    System.out.println(Arrays.toString(num1));  
    String[] names=new String[4];  
    names[3]="Prakii";  
    System.out.println(Arrays.toString(names));  
    Arrays.fill(names,"Hey");  
    System.out.println(Arrays.toString(names));  
}
```
![[Pasted image 20240130155911.png]]
# LOOPS
#LOOPS
## FOR LOOPS
```java
public static void main(String[] args) {  
  
   for(int i=0;i<3;i++)  
   {  
       System.out.println(i+" : Hello");  
   }  
    System.out.println("Reverse");  
   for(int i=3;i>=0;i--)  
    {  
        System.out.println(i+" : Hello");  
    }  
}
```
![[Pasted image 20240130161303.png]]
## If statements
```java
  public static void main(String[] args) {  
if(true){  
    System.out.println("Its True");  
}else{  
    System.out.println("Its False");  
}  
        }
```
![[Pasted image 20240130210708.png]]
### With condition
```java
   public static void main(String[] args) {  
        int age=17;  
        boolean adult= age>=18;  
if(adult){  
    System.out.println("Is adult");  
}else{  
    System.out.println("Is not adult");  
}  
        }
```
### Elseif
```java
public static void main(String[] args) {  
        int mark=99;  
        boolean adult= mark>=90;  
if(adult){  
    System.out.println("excellent");  
}else if(mark>=50){  
    System.out.println("AVerage");  
}else{  
    System.out.println("Fail");  
}  
        }
```
![[Pasted image 20240130211336.png]]
# Method
#Methodcreation
- ## Format
- ![[Pasted image 20240130214126.png]]
- Access modifier -> Public ,Private ,Protected.
- optional Static ->static
- return type -> double , int, void.
- Name -> method Name.
- optional parameter -> string[],double.
- method -> content in body within{};
- optional return value -> return.
- ## Method creation
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
# PACKAGES
#Packages
![[Pasted image 20240131204249.png]]
# Class , Object and Method
## class
#class
- blueprint for a program
## Object
#Object
- an instance of class
## initiating Object
``` java 
String course=new String("Neso academy")
```
- String(class name) course(Object name) .
- new is the keyword the word to create object .
- "String("Neso academy )" is a special method called CONSTRUCTOR.

## Method
#Method
- Group of instruction to do some specific task.
- every Method inside a class
- class is container of methods
- ![[Pasted image 20240131203712.png]]

# Public(access modifier) Static void(return type) name
-  Is an Method
-  Entry for a program.  
## Access modifier of class, method
Specific how to access class ,methods and fields
#Accessmodifier
### Public
- Access level in everywhere(Inside and outside packages ,inside and outside classes)
### Private
- Access level is only inside class
## Static keyword

#Statickeyword
Public static or private static where static is allows the access methos and class by ".".we can access only by static keyword.
## Return type
![[Pasted image 20240131212341.png]]
### Return type
- ![[Pasted image 20240131212403.png]]
### Void Return type
- ![[Pasted image 20240131212455.png]]

# Naming
- pascal case->This Is A Name
- Camel case->this Is A Name
![[Pasted image 20240131204101.png]]
# Structure
![[Pasted image 20240123144603.png]]  
# System.out
#Systemout
- 'out' is an object of Print Stream class.
- out is an camel case 
- print and println are methods in print Stream class where it can be called by using ".out".
- System is class(Pascal case)
- out is in system field. where out can access by "."  System.
- System.out.println->println method can access by out. where it can access by system.
# Types of errors
#errors
## Syntax error
whenever you error related to java syntax.
## Run time error
we have identify during the execution of  code.
## Logical Error
error arise by user.it can be avoid by careful while coding
# VARIABLES AND ITS SIZE
![[Pasted image 20240131224113.png]]
- ![[Pasted image 20240124103502.png]]
## Variable Declaration
![[Pasted image 20240124102622.png]]
# Datatypes
#Datatypes

![[Pasted image 20240131224157.png]]
# CONSTANTS
#CONSTANTS
KEYWORD "final".
![[Pasted image 20240131225648.png]]
![[Pasted image 20240131225722.png]]
![[Pasted image 20240131225804.png]]
# Assignment Operator
![[Screenshot 2024-02-12 111032.png]]
# Casting
![[Screenshot 2024-02-12 111211.png]]

![[Screenshot 2024-02-12 111227.png]]

## IMPLICIT CASTING
![[Screenshot 2024-02-12 111237.png]]

## EXPLICIT CASTING
![[Screenshot 2024-02-12 111306.png]]

![[Screenshot 2024-02-12 111505.png]]

![[Screenshot 2024-02-12 111529.png]]

![[Screenshot 2024-02-12 111552.png]]

![[Screenshot 2024-02-12 111601.png]]

# OPERTORS
## ARITHMETIC OPERTORS(+,-,*,%,/)

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
### Division Operator I/P & O/P
![[Screenshot 2024-02-12 112653.png]]

![[Screenshot 2024-02-12 113128.png]]
##  RELATIONAL OPERATOR(COMPARISON OPERATORS)
- it retrieves only Boolean Values as output.
- it compares to values
- ![[Screenshot 2024-01-30 130313.png]]
- ![[Screenshot 2024-01-30 130335.png]]
- ![[Pasted image 20240130130612.png]]
## LOGICAL OPERATORS(AND,OR,NOT,.....)
```java 
public static void main(String[] args) {  
    boolean Prakii= true;  
    boolean prakash = false;  
    System.out.println(Prakii && prakash);  
    System.out.println(Prakii && !prakash);  
    System.out.println(Prakii || prakash);  
    System.out.println(!Prakii || !prakash);  
    System.out.println(10>=2||2>=3);  
}
```
![[Pasted image 20240205185621.png]]
# Ternary Operator
```java 
public class Main {  
    public static void main(String[] args) {  
        Scanner Age = new Scanner(System.in);  
        int age = Age.nextInt();  
     String Adult = age>18 ? "Iam an Adult":"Iam an child";  
        System.out.println(Adult);  
    }  
}
```
![[Pasted image 20240205190733.png]]
# Null value 
#Nullvalue
![[Pasted image 20240218212153.png]]
# Scanner Class
"Scanner is  class which reads input from keyboard".![[Pasted image 20240201213506.png]]
```java
public class Main {  
    public static void main(String[] args) {  
        Scanner Name = new Scanner(System.in);  
        System.out.println(Name.next());  
        Scanner name = new Scanner(System.in);  
        System.out.println(name.nextLine());  
        Scanner No = new Scanner(System.in);  
        System.out.println(No.nextInt());  
        Scanner no = new Scanner(System.in);  
        System.out.println(no.nextDouble());  
    }  
}
```
![[Pasted image 20240201213356.png]]
# String
```java
{  
    public static void main(String[] args) {  
        String I = "Its";  
        String P = "_Prakii";  
        String Prakii = I + P;  
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
        System.out.println(I.charAt(2));  
        System.out.println(I.indexOf('t'));  
        String op = Prakii.concat("0888");  
        System.out.println(op);  
        String its=new String ("Its");  
        System.out.println(Prakii.contains("Its"));  
        System.out.println(Prakii.contains("its"));  
  
    }  
}
```
o/p
- ![[Screenshot 2024-02-03 152123.png]]
## new vs =
![[Pasted image 20240218195941.png]]
## Strings are Immutable
- Immutable means it cannot be changed. 
- that Means reference Type are immutable. 
- string is an Immutable.
- ![[Pasted image 20240201210906.png]]

# Primitive and Reference Type
- ![[Screenshot 2024-02-01 204748.png]]![[Screenshot 2024-02-01 204815.png]]![[Screenshot 2024-02-01 204839.png]]

![[Screenshot 2024-02-01 204850.png]]

![[Screenshot 2024-02-01 204855.png]]

# Break And Continue
```java
public static void main(String[] args) {
        String[] Name ={"prakii","ish","Lakshmi"};
        for (String s : Name) {
            if(s.equal("ish")){
                break;
            }
            System.out.println(s);

        }
    }

```
![[Screenshot 2024-02-06 225033 1.png]]\
```java
public static void main(String[] args) {  
    String[] Name ={"prakii","ish","Lakshmi"};  
    for (String s : Name) {  
        if(s.equals("ish")){  
            continue;  
        }  
        System.out.println(s);  
  
    }  
}
```
![[Pasted image 20240206225548.png]]
```java 
  public static void main(String[] args) {
        String[] Name ={"prakii","ish","Lakshmi"};
        for (String s : Name) {
            if(s.startsWith("L")){
                break;
            }System.out.println(s);
        }
    }
```
![[Pasted image 20240206230344.png]]
```java
  public static void main(String[] args) {
        String[] Name ={"prakii","ish","Lakshmi"};
        for (String s : Name) {
            if(s.startsWith("i")){
                continue;
            }System.out.println(s);
        }
    }

```
![[Pasted image 20240206225548.png]]
# LOOPS
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
## While LOOP
```java
  
public static void main(String[] args) {  
    int no=0;  
    while(no>10){  
        System.out.println("Count"+no);  
        no++;  
    }  
}
```
![[Pasted image 20240206232109.png]]
## Do While LOOP
```java
public static void main(String[] args) {  
    int no=3;  
    do{  
        System.out.println("Count"+no);  
        no++;  
    }  
    while(no<0);  
}
```
![[Pasted image 20240206232335.png]]
# If statements
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
# Switch case
```java 
public static void main(String[] args) {  
    Scanner gender = new Scanner(System.in);  
    String Gender = gender.next();  
    switch(Gender.toUpperCase()) {  
        case "MALE":  
            System.out.println("Iam an Male");  
            break;  
        case "FEMALE":  
            System.out.println("Iam an Female");  
            break;  
        case "TRANSGENDER":  
            System.out.println("Iam an Trans");  
            break;  
        default:  
            System.out.println("Unknown Gender");  
    }  
    }
```
![[Pasted image 20240205191813.png]]
![[Pasted image 20240313220729.png]]

# Math class
```java
public static void main(String[] args) {  
    System.out.println(Math.abs(-100));  
    System.out.println(Math.max(2,424));  
    System.out.println(Math.min(2,223));  
    System.out.println((Math.pow(4,4)));  
    System.out.println((int)Math.pow(4,4));  
    System.out.println(Math.sqrt(25));  
    System.out.println((int)Math.sqrt(25));  
    System.out.println(Math.PI);  
}
```
![[Screenshot 2024-02-04 211456.png]]
# Arrays
#Arrays
![[Screenshot 2024-02-18 212537.png]]
![[Screenshot 2024-02-18 212730.png]]
## 0  and Null in array
![[Screenshot 2024-02-18 212657.png]]
## Returning Array in method
![[Screenshot 2024-02-18 215024.png]]

![[Screenshot 2024-02-18 215039.png]]
![[Screenshot 2024-02-18 215129.png]]
- Array  in getNumber() will  not destroy after execution because it always referred by a array numbers.
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
## Array class
#Arrayclasses 
![[Pasted image 20240219203231.png]]
#### Sorting Array
#SortingArray
![[Pasted image 20240219203819.png]]
### Searching Array
#searchingArray
![[Pasted image 20240219204055.png]]

![[Screenshot 2024-02-19 204209.png]]
### Comparing Arrays
#ComparingArrays
![[Screenshot 2024-02-19 204428.png]]
![[Pasted image 20240219205014.png]]
![[Pasted image 20240219205058.png]]
### Filling Arrays
#FillingArray
![[Pasted image 20240219205352.png]]
![[Pasted image 20240219205525.png]]
### Printing Arrays
#PrintingArray
![[Pasted image 20240219205810.png]]

## Array using For Loop
```java
public class Practice  
{  
    public static void main(String[] args) {  
        String[] Name ={"prakii","ish","Lakshmi"};  
        for (String s : Name) {  
            System.out.println(s);  
        }  
    }  
}
```
![[Pasted image 20240206224037.png]]
# Array List
 
  - In Array size is fixed. But in "Array list " the size is resizable and dynamic.
  - Here Array List are objects.
 ![[Pasted image 20240221221017.png]]
 ![[Screenshot 2024-02-21 221221.png]]

![[Screenshot 2024-02-21 221306.png]]

![[Screenshot 2024-02-21 221329.png]]

![[Screenshot 2024-02-21 221408.png]]

![[Screenshot 2024-02-21 221432.png]]
## Sorting An Arraylist
![[Pasted image 20240222204528.png]]
![[Pasted image 20240222204558.png]]
# For Each Loop(Array list)
- used for iteration in Array/Array list
## syntax of For Each
![[Pasted image 20240222205226.png]]
## In Array list
![[Pasted image 20240222205304.png]]
## In Array 
![[Pasted image 20240222205318.png]]
# Scope And Local Variables!
[[Screenshot 2024-02-17 213246.png]]

![[Screenshot 2024-02-17 213402.png]]
# Method
## Variable-Length argument List
- ***it means variable number of arguments can be passed through a method

![[Pasted image 20240219211033.png]]
![[Pasted image 20240219211254.png]]
- In Above content that "Int . . ." means ellipse.it want to variable number of argument that continue calling by the parameter "numbers". here the parameter is act as an Array.
![[Pasted image 20240219211805.png]]
![[Pasted image 20240219211924.png]]
![[Pasted image 20240219212058.png]]
- In Above content 1st line have error  because we have passes only one variable length parameter("Double . . . ) is to be present.
- in 2nd also error  because we need to pass variable length parameter as last parameter.
- Last line is correct ,because all the parameters are pass before the variable length parameter(it must be last).
- "void print(String name ,double . . . numbers)".
## Format
- ![[Pasted image 20240130214126.png]]
- Access modifier -> Public ,Private ,Protected.
- optional Static ->static
- return type -> double , int, void.
- Name -> method Name.
- optional parameter -> string[],double.
- method -> content in body within{};
- optional return value -> return.
## Method Overloading
![[Screenshot 2024-02-17 223827.png]]

![[Screenshot 2024-02-17 223853.png]]

![[Screenshot 2024-02-17 224240.png]]
- two methods with same name leads to error.
- To avoid this overload we must have different parameter and different return type.
- same name but each have Different arguments for each method
##  Method creation
```java
public static void main(String[] args) {  
    System.out.print("Enter your name and Age :");  
    System.out.println("Hello! "+Name()+" Your are "+age()+" Old.");  
}  
  
public static int age() {  
return new Scanner(System.in).nextInt();  
}  
public static String Name() {  
    return new Scanner(System.in).nextLine();
```
![[Pasted image 20240218201359.png]]
### Example 1
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
### EXAMPLE 2
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
# Class And Object Creation
## Class Structure 
```java
public static void main(String args) {  
}  
static class lens{  
    String company;  
    String Focus;  
    Double Price;  
    String Colour;  
    boolean isprime;  
    lens(String company,String Focus ,Double Price,String colour,boolean isprime){  
        this.company=company;  
        this.Focus=Focus;  
        this.Price=Price;  
        this.Colour=Colour;  
        this.isprime=isprime;  
    }  
  
}
```
## Object Creation
```java
public static void main(String[] args) {  
    lens L1=new lens("Sony","30MM",3234.99,"RED",true);  
    lens L2=new lens("Canon","40MM",40.00,"BLACK",true);  
    lens L3=new lens("Gopro","10MM",3500.00,"BLACK",false);  
  
}
```
### final Code 
```java
public static void main(String[] args) {  
    lens L1=new lens("Sony","30MM",3234.99,"RED",true);  
    lens L2=new lens("Canon","40MM",40.00,"BLACK",true);  
    lens L3=new lens("Gopro","10MM",3500.00,"BLACK",false);  
    System.out.println("Lens 1->"+L1.company+" FocalLength-> "+L1.Focus+",  Price-> "+L1.Price+",  Colour-> "+L1.Colour+",  isPrime-> "+L1.isprime);  
    System.out.println("Lens 2->"+L2.company+" FocalLength-> "+L2.Focus+",  Price-> "+L2.Price+",  Colour-> "+L2.Colour+",  isPrime-> "+L2.isprime);  
    System.out.println("Lens 3->"+L3.company+" FocalLength-> "+L3.Focus+",  Price-> "+L3.Price+",  Colour-> "+L3.Colour+",  isPrime-> "+L3.isprime);  
  
}  
static class lens{  
    String company;  
    String Focus;  
    Double Price;  
    String Colour;  
    boolean isprime;  
    lens(String company,String Focus ,Double Price,String colour,boolean isprime){  
        this.company=company;  
        this.Focus=Focus;  
        this.Price=Price;  
        this.Colour=Colour;  
        this.isprime=isprime;  
    }  
}
```
![[Pasted image 20240207212408.png]]
## Example(Passport Problem)
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
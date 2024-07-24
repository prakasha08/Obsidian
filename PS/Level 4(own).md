https://onedrive.live.com/edit?id=C56496F3943DF4DE!sd863b62d99884b5eb48df655b8d30e9a&resid=C56496F3943DF4DE!sd863b62d99884b5eb48df655b8d30e9a&cid=c56496f3943df4de&ithint=file%2Cxlsx&redeem=aHR0cHM6Ly8xZHJ2Lm1zL3gvYy9jNTY0OTZmMzk0M2RmNGRlL0VTMjJZOWlJbVY1THRJMzJWYmpURHBvQkNMTUhUeEEzSzQ3NU1pSEc2SWFUT3c_ZT1MbGFlaGY&migratedtospo=true&wdo=2
### Removing Vowels
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>
#include<stdlib.h>
int main() {
    char str[10],lstr[10];
    scanf("%[^\n]s",str);
      for(int i=0;i<strlen(str);i++){
        lstr[i] = tolower(str[i]);
    }
    for(int i=0;i<strlen(lstr);i++){
        if(lstr[i]=='a'||lstr[i]=='e'||lstr[i]=='i'||lstr[i]=='o'||lstr[i]=='u'){
        continue;
            }
            else{
                printf("%c",str[i]);
            }
    }
    return 0;
}
```
### Replace specific char with another char and numbers with 'n'  . 'a' -> 'b',  't' -> 'g', number -> 'n' Input: "Education4all", Output : "Educbgionnbll"
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>
#include<stdlib.h>
int main() {
    char str[10],lstr[10];
    scanf("%[^\n]s",str);
    for(int i=0;i<strlen(str);i++){
        if(str[i]=='a'){
                 str[i]='b';
          }
          else if(str[i]=='t'){
                 str[i]='g';
          }
            else if(isdigit(str[i])){
                str[i]='n';
            }
            else{
                continue;
            }
    }
    printf("%s",str);
    return 0;
}
```
### program to print maximum character that is repeated in the string i.e Hello World - l ( l 3 repetition )
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main() {
    int i,j;
    char str[100];
    char lstr[100];
    scanf("%[^\n]s",&str);
    int len = strlen(str);
    int max = 0; char c;
    int count=1;
    
    for(i=0;i<len;i++){
        lstr[i] = tolower(str[i]);
    }
    
    for(i = 0 ; i<len;i++){
        for(j=i+1;j<len;j++){
            if(lstr[i] == lstr[j]){
                count++;
            }
        }
        if(max<count){
            max = count;
            c = lstr[i];
        }
        count = 1;
    }
    
    printf("%c max repeated times %d",c,max);
    return 0;
}
```
### Removing Alphabets
```c
// Online C compiler to run C program online
#include <stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]s",&str);
    for(int i=0;i<strlen(str);i++){
        if(!(isalpha(str[i]))){
            printf("%c",str[i]);
        }
    }
    return 0;
}
```
### print the string replacing the space with given character -- input : string - "Hello World" replace :- "$" -- output : "Hello$World"
```c
// Online C compiler to run C program online
#include <stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]s",&str);
    for(int i=0;i<strlen(str);i++){
        if(str[i]==' '){
            printf("%c",'$');
        }
        else{
            printf("%c",str[i]);
        }
    }
    return 0;
}
```
### Print the First UpperCase Letter. Eg. Input: "hello World" --> Ouput: W
```c
// Online C compiler to run C program online
#include <stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]s",&str);
    for(int i=0;i<strlen(str);i++){
        if(isupper(str[i])){
            printf("%c",str[i]);
            return 0;
        }
    }
    return 0;
}
```
### Program to print the first non repeating character in a string. Input1 :- gaming Output :- First non-repeating character is 'a' at index 1. Input2 :- momo Output :- No non-repeating character present.
```c
// Online C compiler to run C program online
#include <stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main() {
    char str[20],lstr[20];
    int count;
    scanf("%[^\n]s",&str);
       for(int i=0;i<strlen(str);i++){
        lstr[i] = tolower(str[i]);
        }
    for(int i=0;i<strlen(str);i++){
        count=0;
        for(int j=0;j<strlen(lstr);j++){
        if(lstr[i]==lstr[j]){
           count+=1;
         }
        }
        if(count==1){
             printf("%c",str[i]);
             return 0;
        }
     }
    return 0;
}
```
### Reverse a word in string! (Input: Hello World, || Output: olleH dlorW)
```c
#include <stdio.h>
#include <string.h>
int main() {
    char str[20], rstr[20];
    printf("Enter a string: ");
    scanf("%[^\n]", str);
    int length = strlen(str);
    int start = 0;
    for (int i = 0; i <= length; i++) {
        if (str[i] == ' ' || str[i] == '\0') {
            int end = i - 1;
            int k = 0;
            for (int j = end; j >= start; j--) {
            printf("%c",str[j]);
            }
            if(str[i]!='\0')
            printf(" ");
            start = i + 1;
         }
    }
    return 0;
}

```
### Find the largest and smallest word in a string. Input: The bottle is full Output: is bottle
```c
#include <stdio.h>
#include<string.h>
int main() {
    char in[1024];
    scanf("%[^\n]",&in);
    int start = 0;
    int min = 10000;
    int mS=0;
    int count=0;
    int max =0;  
    int maxS = 0;
    for(int i=0;i<=strlen(in);i++){
        if(in[i] == ' ' || in[i]=='\0'){
            if(min > count){
                min = count;
                mS=start;
            }
            if(max<count){
                max = count;
                maxS = start;
            }
            start=i+1;
            count=0;
        }else{
            count++;
        }
    }
    
    for(int i=mS;in[i] != ' ' &&i < strlen(in);i++){
        printf("%c",in[i]);
    }
    printf("\t");
    
    for(int i=maxS;in[i] != ' ' && i < strlen(in);i++){
        printf("%c",in[i]);
    }
    
}
```
### Find the largest number length in the given sentence. Input :- 4(range of words) This question is easy. Output:- 8(length of the largest word)
```c
#include <stdio.h>
#include<string.h>
int main() {
    char in[1024];
    scanf("%[^\n]",&in);
    int start = 0;
    int count=0;
    int max =0;
    for(int i=0;i<=strlen(in);i++){
        if(in[i] == ' ' || in[i] == '\0'){
            if(max<count){
                max = count;
            }
            start=i+1;
            count=0;
        }else{
            count++;
        }
    }
      printf("%d",max);
    return 0;
}
```
###  Smallest word in a String! (Input: I like cricket, || Output: I )
```c
#include <stdio.h>
#include<string.h>
int main() {
    char in[1024];
    scanf("%[^\n]",&in);
    int start = 0;
    int min = 10000;
    int mS=0;
    int count=0;
    for(int i=0;i<=strlen(in);i++){
        if(in[i] == ' ' || in[i]=='\0'){
            if(min > count){
                min = count;
                mS=start;
            }
            start=i+1;
            count=0;
        }else{
            count++;
        }
    }
    
    for(int i=mS;in[i] != ' ' &&i < strlen(in);i++){
        printf("%c",in[i]);
 }
}
```
### Replace space in a string with character("%20"). Input : world is big#Output:world%20is%20big
```c
#include <stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]s",&str);
    for(int i=0;i<strlen(str);i++){
        if(str[i]==' '){
            printf("%s","%20");
        }
        else{
            printf("%c",str[i]);
        }
    }
    return 0;
}
```
### Remove duplicate characters in a string input engineering output enginr

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[20];
    scanf("%[^\n]",str);
     int visited[20];
    for(int i=0;i<20;i++){
        visited[i]=0;
    }
    for(int i=0;i<strlen(str);i++){
      for(int j=i+1;j<strlen(str);j++){
          if(str[i]==str[j]){
              visited[j]=1;
      }
    }
    }
    for(int i=0;i<strlen(str);i++){
        if(!visited[i]){
            printf("%c",str[i]);
        }
    }

        return 0;
}


```
### Railway timing
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int main() {
    char s[9];
    int hours, minutes, seconds;
    scanf("%8s", s);
    if (strlen(s) != 8 || s[2] != ':' || s[5] != ':' ||
        !isdigit(s[0]) || !isdigit(s[1]) || !isdigit(s[3]) || !isdigit(s[4]) || !isdigit(s[6]) || !isdigit(s[7])) {
        printf("Invalid\n");
        return 0;
    }
    sscanf(s, "%d:%d:%d", &hours, &minutes, &seconds);
    if (hours < 0 || hours > 23 || minutes < 0 || minutes > 59 || seconds < 0 || seconds > 59) {
            printf("Invalid\n");
        } else {
            printf("Hour:%d Minutes:%d seconds:%d",hours,minutes,seconds);
        }

    return 0;
}
```
### swap adjacent characters in a given string 
#### for i/p->openai,o/p->poenia
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[1024];
    scanf("%[^\n]",str);
    for(int i=0;i<strlen(str);i++){
        if(i==0||i==strlen(str)-2){
            int temp=str[i];
            str[i]=str[i+1];
            str[i+1]=temp;
        }
    }
    printf("%s",str);
    return 0;
}

```
#### for input: OpenAI , output: pOneIA
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char s[100];
    fgets(s, sizeof(s), stdin);
    s[strcspn(s, "\n")] = '\0';
    for (int i = 0; i < strlen(s) - 1; i++) {
        if (!isspace(s[i]) && !isspace(s[i + 1])) {
            char temp = s[i];
            s[i] = s[i + 1];
            s[i + 1] = temp;
            i++; 
        }
    }
    printf("%s", s);
    return 0;
}
```
### count the total characters in a string and check the number is odd,even,prime
```c
#include <stdio.h>
#include <string.h>

int oddeven(int count){
    if(count%2==0){
        printf(" Even");
        return 0;
    }
    else{
    printf(" odd");
    return 0;
    }
}
int main() {
    char str[10];
    int count=0,prime=1;
    scanf("%[^\n]",str);
    for(int i=0;i<strlen(str);i++){
        if(str[i]==' '){
            continue;
        }
       count+=1;
    }
    if(count<=1){
        printf("%d is ",count);
        oddeven(count);
        return 0;
    }
    else{
    for(int i=2;i<count/2;i++){
        prime=0;
          }
     }
     printf("%d is",count);
    if(prime)
        printf(" prime",count);
    else
        oddeven(count);
    return 0;
}
```

```c
#include <stdio.h>
#include <string.h>
void oddeven(int count) {
    if(count % 2 == 0) {
        printf("%d is Even", count);
    } else {
        printf("%d is Odd", count);
    }
}
int isPrime(int count) {
    if (count <= 1) {
        return 0;
    }
    for (int i = 2; i <= count / 2; i++) {
        if (count % i == 0) {
            return 0;
        }
    }
    return 1;
}

int main() {
    char str[100];
    int count = 0;

    // Reading input string
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0'; 

    for(int i = 0; i < strlen(str); i++) {
        if(str[i] != ' ') {
            count++;
        }
    }

    oddeven(count);

    if (isPrime(count)) {
        printf(" & Prime\n");
    } else {
        printf(" & Not Prime\n");
    }

    return 0;
}

```
### Smallest appeared character in a string
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main() {
    int i,j;
    char str[100];
    scanf("%[^\n]s",str);
    int len = strlen(str);
    int max = 10000;
    char c;
    int count=1;
    
    for(i=0;i<len;i++){
        str[i] = tolower(str[i]);
    }
    
    for(i = 0 ; i<len;i++){
        for(j=0;j<len;j++){
            if(str[i] == str[j]&&i!=j){
                count++;
            }
        }
        if(max>count){
            max = count;
            c = str[i];
        }
        count = 1;
    }
    
    printf("%c min repeated times %d",c,max);
    return 0;
}

```
### Rotate a matrix to 90 degree!
```c
#include <stdio.h>
#include <string.h>

int main() {
    int m;
    scanf("%d",&m);
    getchar();
    char s[m][m];
    char temp[10]; // temporary buffer to read each row
    // Reading the input
    for (int i = 0; i < m; i++) {
        fgets(temp, sizeof(temp), stdin);
        temp[strcspn(temp, "\n")] = '\0';
        for (int j = 0, k = 0; j < m; j++, k += 2) {
            s[i][j] = temp[k];
        }
    }

    // Printing the array in reverse order
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
           printf("%c ",s[j][i]);
        }
        printf("\n");
    }

    return 0;
}

```

```c
#include <stdio.h>
#include <string.h>
int main() {
    int n;
    printf("Enter the Dimension: ");
    scanf("%d",&n);
    char str[n][n];
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            scanf(" %c",&str[i][j]);
        }
    }
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            int temp=str[i][j];
            str[i][j]=str[j][i];
            str[j][i]=temp;
        }
    }
    for(int i=0;i<n;i++){
        int start=0;
        int end=n-1;
        while(start<end){
            int temp=str[i][start];
            str[i][start]=str[i][end];
            str[i][end]=temp;
            end-=1;
            start+=1;
        }
    }
     for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            printf("%c ",str[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```
### Vowel Counting in String. Sample Input: Hello World Sample Output: 3.
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]",str);
     int n=strlen(str),count=0;
    for(int i=0;i<n;i++){
        str[i]=tolower(str[i]);
    }
    for(int i=0;i<n;i++){
        if(str[i]=='a'||str[i]=='e'||str[i]=='o'||str[i]=='i'||str[i]=='u')
        count+=1;
    }
    printf("%d",count);
    return 0;
}
```
### Removing Punctuation
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]",str);
    for(int i=0;i<strlen(str);i++){
        if(isalnum(str[i])){
             printf("%c",str[i]);
        }
        else{
            continue;
        }
    }
    return 0;
}
```

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]",str);
    for(int i=0;i<strlen(str);i++){
        if((str[i]>=33&&str[i]<=47)||(str[i]>=58&&str[i]<=64)||(str[i]>=91&&str[i]<=96)){
            continue;
        }
        else{
            printf("%c",str[i]);
        }
    }
    return 0;
}
```
### Palindrome
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int main() {
    char str[20];
    scanf("%[^\n]",str);
    int n=strlen(str);
    for(int i=0;i<n;i++){
       if(str[i]!=str[n-i-1]){
           printf("Not a Palindrome");
           return 0;
       }
    }
    printf("Palindrome");
    return 0;
}
```
### Anagram
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[100], str2[100];
    printf("Enter the first string: ");
    scanf("%s", str1);

    printf("Enter the second string: ");
    scanf("%s", str2);

    int n1 = strlen(str1);
    int n2 = strlen(str2);

    if (n1 != n2) {
        printf("Not an Anagram\n");
        return 0;
    }

    int visited[100] = {0}; // Array to keep track of visited characters in str2

    for (int i = 0; i < n1; i++) {
        int found = 0; // Flag to check if a character of str1 is found in str2
        for (int j = 0; j < n2; j++) {
            if (str1[i] == str2[j] && !visited[j]) {
                visited[j] = 1;
                found = 1;
                break; // Move to the next character of str1
            }
        }
        if (!found) { // If a character of str1 is not found in str2
            printf("Not an Anagram\n");
            return 0;
        }
    }

    printf("Anagram\n");

    return 0;
}

```
### Enter a sentence: rethu is girl:Reversed sentence: girl is rethu
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>
#include<math.h>
int main() {
    char s[100];
    fgets(s, sizeof(s), stdin);  
    s[strcspn(s, "\n")] = '\0';
    char words[100][100];
    int k = 0;
    char *word = strtok(s, " ");
    while (word != NULL) {
        strcpy(words[k++], word);
        word = strtok(NULL, " ");
    }
    for(int i=k-1;i>=0;i--){
        printf("%s",words[i]);
        if(i>0){
            printf(" ");
        }
    }
    return 0;
}
```
### Removing Word from sentence i/p :" the sun is hot". word: "is" o/p: "the sun hot".
```c
#include <stdio.h>
#include <string.h>

int main() {
    char arr[100], word[100];
    fgets(arr,100,stdin);
    fgets(word,100,stdin);
    arr[strlen(arr)-1]='\0';
    word[strlen(word)-1]='\0';
    int c=0;
    for(int i=0; i<sizeof(arr); i++){
        if(arr[i]==' '){
            c++;
         }
     }
    char *t = strtok(arr," ");
    int i=0;
    while(t!=NULL ){
         if(strcmp(t,word)!=0){
              if(c!=i&&i!=0){
                   printf(" ");
              }
              printf("%s",t);
              i++;
       }
        t = strtok(NULL, " ");
   }
   return 0;
}
```
### first occurrence of a word in a string Input string: I love programming! Input word to search: love Output 'love' is found at index 2.
```c
#include <stdio.h>
#include <string.h>

int main() {
    char arr[100], word[100];
    fgets(arr,100,stdin);
    fgets(word,100,stdin);
    arr[strlen(arr)-1]='\0';
    word[strlen(word)-1]='\0';
    int c=0;
    for(int i=0; i<sizeof(arr); i++){
        if(arr[i]==' '){
            c++;
         }
     }
    char *t = strtok(arr," ");
    int i=0;
    while(t!=NULL ){
         if(strcmp(t,word)==0){
            printf("word found at index: %d",i);
            return 0;
        }
        i+=strlen(t)+1;
        t = strtok(NULL, " ");
    }
   
   return 0;
}
```
### Isomorphic
```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

int main() {
    char str1[100], str2[100];
    int map1[256] = {0};
    int map2[256] = {0};
    printf("Enter the first string: ");
    fgets(str1, sizeof(str1), stdin);
    str1[strcspn(str1, "\n")] = '\0';
    printf("Enter the second string: ");
    fgets(str2, sizeof(str2), stdin);
    str2[strcspn(str2, "\n")] = '\0';
    int m = strlen(str1);
    int n = strlen(str2);
    if (m != n) {
        printf("Not a Isomorphic");
        return 0;
    } else {
        for (int i = 0; i < m; i++) {
            if (map1[(int)str1[i]] != 0) {
                if (map1[(int)str1[i]] != (int)str2[i]) {
                    printf("Not a Isomorphic");
                    return 0;
                }
            } else {
                if (map2[(int)str2[i]] != 0) {
                 printf("Not a Isomorphic");
                 return 0;
                }
                map1[(int)str1[i]] = (int)str2[i];
                map2[(int)str2[i]] = (int)str1[i];
            }
        }
    }
        printf("The strings are isomorphic.\n");
    return 0;
}

```
### Get num of words from user and get the num of words and print even positions words
```c
#include <stdio.h>
int main() {
    int numWords;
    printf("Enter the number of words: ");
    scanf("%d", &numWords);
    char words[numWords][100];
    printf("Enter the words:\n");
    for (int i = 0; i < numWords; i++) {
        scanf("%s", words[i]);
    }
    printf("Words at even positions:\n");
    for (int i = 1; i < numWords; i += 2) { 
        printf("%s ", words[i]);
    }

    return 0;
}
```
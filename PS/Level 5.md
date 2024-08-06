# 2.[125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
```c
#include <stdio.h>
#include <string.h>
#include<ctype.h>
int ispal(char *s) {
    int start=0;
    int end=strlen(s)-1;
    while(start<=end){
        if(s[start]!=s[end]){
            return 0;
        }
        start++;
        end--;
    }
    return 1;
}

int main() {
    char s[100];
    fgets(s, sizeof(s), stdin);
    s[strcspn(s, "\n")] = '\0';

    int k = 0;
    for (int i = 0; i < strlen(s); i++) {
        if (isalpha(s[i])) {
            s[k++] = tolower(s[i]);
        }
    }
     s[k] = '\0';
  if(ispal(s))
        printf("True");
    else
        printf("False");
    return 0;
}

```
# Prime Number Checker
```c
#include <stdio.h>
#include <string.h>
#include<ctype.h>
int isprime(int n) {
    if(n<=1)
        return 0;
    for(int i=2;i<=n/2;i++){
        if(n%i==0){
            return 0;
        }
    }
    return 1;
}
int main() {
  int n;
  scanf("%d",&n);
  if(isprime(n))
        printf("Prime");
    else
        printf("Not a Prime");
    return 0;
}

```
# Anagram
```c
#include <stdio.h>
#include <string.h>
#include<ctype.h>
int isanagram(char *s1,char * s2) {
   int count_a[256]={0},count_b[256]={0};
 
    for (int i = 0; i < strlen(s1); i++) {
        if (!isspace(s1[i])) {
            count_a[tolower(s1[i])]++;
        }
    }
    for (int i = 0; i < strlen(s2); i++) {
        if (!isspace(s2[i])) {
            count_b[tolower(s2[i])]++;
        }
    }
    for(int i=97;i<123;i++){
        if(count_a[i]!=count_b[i]){
            return 0;
        }
    }
    return 1;
}

int main() {
    char s1[100],s2[100];
    fgets(s1, sizeof(s1), stdin);
    s1[strcspn(s1, "\n")] = '\0';
    fgets(s2, sizeof(s2), stdin);
    s2[strcspn(s2, "\n")] = '\0';
    if(isanagram(s1,s2))
    printf("Anagram");
    else printf("Not an Anagram");
    return 0;
}

```
# 5. Recursive Factorial Calculator
```c
#include <stdio.h>
int fact(int n){
    if(n==1||n==0)
        return 1;
    return n*fact(n-1);
}
int main() {
    int n;
    scanf("%d",&n);
    if(n<0){
        printf("Invalid");
        return 0;
    }
    printf("%d",fact(n));
    return 0;
}
```
# 6. Power Function
```c
#include <stdio.h>
#include<math.h>
#include<ctype.h>
#include <stdlib.h>
int main() {
    float n1,n2;
    scanf("%f",&n1);
    scanf("%f",&n2);
    if(n1!=(int)n1||n2!=(int)(n2)){
    float k=pow(n1,n2);
    printf("%.2f",k);
    }
    else if(n2<0){
            float k=1/pow(n1,abs(n2));
            printf("%.3f",k);
            return 0;
        }
    else{
    int k=pow(n1,n2);
    printf("%d",k);
    }
    return 0;
}
```
# 7. String Compression
```c
#include <stdio.h>
#include<math.h>
#include<ctype.h>
#include <stdlib.h>
#include <string.h>
int main() {
    char s[100];
    fgets(s,sizeof(s),stdin);
    s[strcspn(s,"\n")]=0;
    int visited[100]={0};
    char s1[100];
    int k=0;
    int flag=0;
     if (strlen(s) == 0 || strcmp(s, " ") == 0) {
        printf("Invalid Input\n");
        return 0;
    }
    
    for(int i=0;i<strlen(s);i++){
        int count=1;
        if(!visited[i]){
        for(int j=i+1;j<strlen(s);j++){
            if(s[i]==s[j]&&!visited[j]){
                count++;
                flag=1;
                visited[i]=1;
                visited[j]=1;
            }
        }
        s1[k++]=s[i];
        s1[k++]=count+'0';
        }
    }
    s1[k]='\0';
    if(flag){
        printf("%s",s1);
    }
    else
        printf("%s",s);
    return 0;
}
```
# 8. Matrix Transposition
```c
#include <stdio.h>
#include <string.h>
void transpose(int n ,int str[n][n]){
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            scanf(" %d",&str[i][j]);
        }
    }
     for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(j>0){
                printf(" ");
            }
            printf("%d",str[j][i]);
        }
        printf("\n");
    }
}
int main() {
    int n;
    printf("Enter the Dimension: ");
    scanf("%d",&n);
    int str[n][n];
    transpose(n,str);
    return 0;
}
```

# Word Frequency 
Input: "hello world hello universe world"
Output: {'hello': 2, 'world': 2, 'universe': 1}
Explanation: The word 'hello' appears twice, 'world' appears twice, and 'universe' appears
once.
```c
#include <stdio.h>
#include<math.h>
#include<ctype.h>
#include <stdlib.h>
#include <string.h>
int main() {
    char s[100];
    fgets(s,sizeof(s),stdin);
    s[strcspn(s,"\n")]=0;
    char words[100][100];
    int k=0;
    char* word=strtok(s," ");
    while(word!=NULL){
        strcpy(words[k++],word);
        word=strtok(NULL," ");
    }
    int visited[100]={0};
    int count;
    printf("{");
    for(int i=0;i<k;i++){
        count =1;
        if(!visited[i]){
            if(i>0)
                printf(",");
            for(int j=0;j<k;j++){
                if(strcmp(words[i],words[j])==0&&!visited[j]){
                    count+=1;
                    visited[j]=1;
                }
            }
        printf("\'%s\':%d",words[i],count);
        }
    }
    printf("}");
    return 0;
}
```
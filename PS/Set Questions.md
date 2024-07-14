# Set 1
## 1.Anagram
```c
#include <stdio.h>
#include <string.h>

int main() {
    int b = 0, c = 0, k = 0;
    char s[100], g[100];
    fgets(s, 100, stdin);
    fgets(g, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    g[strcspn(g, "\n")] = 0;
    int len_s = strlen(s);
    int len_g = strlen(g);
    if (len_s != len_g) {
        printf("Strings must be of the same length\n");
        return 1;
    }
    int visited[100] = {0};
    for (int i = 0; i < len_s; i++) {
            b=0;
            for (int j = 0; j < len_g; j++){
                if(!visited[j]&&s[i] == g[j]){
                        visited[j] = 1;
                        b=1;
                        break;
                    }
               }
                if(!b){
                    printf("False");
                    return 0;
                }
    }
    printf("True");
    return 0;
}
```

```c
#include <stdio.h>
#include <string.h>

int main() {
    char s[100], g[100];
    int count_s[256] = {0};
    int count_g[256] = {0};
    fgets(s, 100, stdin);
    fgets(g, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    g[strcspn(g, "\n")] = 0;
    int len_s = strlen(s);
    int len_g = strlen(g);
    if (len_s != len_g) {
        printf("Strings must be of the same length\n");
        return 1;
    }
    for (int i = 0; i < len_s; i++) {
        count_s[(unsigned char)s[i]]++;
        count_g[(unsigned char)g[i]]++;
    }
    for (int i = 0; i < 256; i++) {
        if (count_s[i] != count_g[i]) {
            printf("False\n");
            return 0;
        }
    }
    printf("True\n");
    return 0;
}

```
## 3.Greatest English Letter in Upper and Lower Case
```c
#include <stdio.h>
#include <string.h>
#include<ctype.h>
int main() {
    int m=0,n=0;
    char s[100];
    fgets(s, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    int len = strlen(s);
    for(int i=0;i<len;i++){
        for(int j=0;j<len;j++){
           if(tolower(s[i])==s[j]&&i!=j){
            m=(int)(s[i])>m?(int)(s[i]):m;
           }
           if(toupper(s[i])==s[j]&&i!=j){
            n=(int)(s[i])>n?(int)(s[i]):n;
           }
        }
    }
        if(!(m||n)){
            printf("");
            return 0;
        }
    printf("%c",m);
    return 0;
}
```
## 4.Valid Parentheses
```c
#include <stdio.h>
#include <string.h>

int main() {
    int k = 0;
    char s[100], ch[100];
    fgets(s, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    int len = strlen(s);

    for (int i = 0; i < len; i++) {
        char c = s[i];
        if (c == '(' || c == '{' || c == '[') {
            ch[k++] = c;
        } else {
            if (k == 0) {
                printf("false\n");
                return 0;
            }
            if (c == ')' && ch[k - 1] != '(') {
                printf("false\n");
                return 0;
            }
            if (c == '}' && ch[k - 1] != '{') {
                printf("false\n");
                return 0;
            }
            if (c == ']' && ch[k - 1] != '[') {
                printf("false\n");
                return 0;
            }
            k--;
        }
    }

    if (k == 0) {
        printf("true\n");
    } else {
        printf("false\n");
    }

    return 0;
}

```
## 5.Minimum Length of String After Deleting Similar Ends.
```c
#include <stdio.h>
#include <string.h>

int main() {
    char s[100], ch[100];
    fgets(s, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    int len = strlen(s);
    int l=0,r=len-1,k=0;
   while(l<r) {
        if(s[l]==s[r]){
            char c=s[l];
            while(l<=r&&c==s[l]){
                l++;
                k+=1;
            }
            while(r>=l&&c==s[r]){
                r--;
                k+=1;
            }
        }
        else
            break;
    }
    printf("%d",len-k);
    return 0;
}

```
## 6.Simple FLAMES Game
```c
#include <stdio.h>
#include <string.h>
#include<ctype.h>
int main() {
    char s1[100];
    fgets(s1, 100, stdin);
    s1[strcspn(s1, "\n")] = 0;
     for (int i = 0; s1[i]; i++) {
        s1[i] = tolower(s1[i]);
    }
    char s2[100];
    fgets(s2, 100, stdin);
    s2[strcspn(s2, "\n")] = 0;
     for (int i = 0; s2[i]; i++) {
        s2[i] = tolower(s2[i]);
    }
    char Flames[6]={'F','L','A','M','E','S'}; 
    int visited[100] = {0};
    int count=0,n=6,c=0;
    int v[100]={0};
    for(int i=0;i<strlen(s1);i++){
        for(int j=0;j<strlen(s2);j++){
           if (!v[j] && s1[i] == s2[j]){
                    c+=2;
                    v[j]=1;
                    break;
                }
            }
        }
    count=strlen(s1)+strlen(s2)-c;
    int pos=0;
  while (n > 1) {
        pos = (pos + count - 1) % n; 
        for (int i = pos; i < n - 1; i++) {
            Flames[i] = Flames[i + 1]; 
        }
        n--;
    }
    printf("%c",Flames[0]);
    return 0;
}
```
## 7.Kth Distinct String in an Array
```c
#include <stdio.h>
#include <string.h>

int main() {
    char s[100];
    fgets(s, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    char words[100][100]; 
    int visited[100] = {0};
    int k = 0, m = 0;
    char *word = strtok(s, " ");
    while (word != NULL) {
        strcpy(words[k++], word);
        word = strtok(NULL, " ");
    }
    for (int i = 0; i < k; i++) {
        if (!visited[i]) {
            for (int j = i + 1; j < k; j++) {
                if (strcmp(words[i], words[j]) == 0) {
                    visited[j] = 1;
                    visited[i] = 1;
                }
            }
        }
    }
    char unique[100][100];
    for (int i = 0; i < k; i++) {
        if (!visited[i]) {
            strcpy(unique[m], words[i]);
            m++;
        }
    }
    int kth;
    scanf("%d", &kth);
    if (kth <= m) {
        printf("%s", unique[kth - 1]);
    } else {
        printf("!");
    }

    return 0;
}
```
# Set 4
## 1.Make Three Strings Equal by deleting rightmost element

```c
#include <stdio.h>  
#include <string.h>  
int main()  
{  
    char str1[100], str2[100], str3[100];  
    int count=0;  
    fgets(str1, sizeof(str1), stdin);  
    str1[strcspn(str1, "\n")] = '\0';  
    fgets(str2, sizeof(str2), stdin);  
    str2[strcspn(str2, "\n")] = '\0';  
    fgets(str3, sizeof(str3), stdin);  
    str3[strcspn(str3, "\n")] = '\0';  
     int ts=strlen(str1)+strlen(str2)+strlen(str3);  
        if (strcmp(str1, str2) == 0 && strcmp(str1, str3) == 0) { 
        printf("0");
         } 
        else {      
        printf("Strings are not identical.");
         } 
        for(int i=0;i<100;i++){  
          if(str1[i]!=str2[i]||str1[i]!=str3[i]||str3[i]!=str2[i]){  
              if(i==0){  
                  printf("-1");  
              return -1;  
              }  
           }  
        }  
        for(int i=0;i<ts;i++){  
            if(str1[i]==str2[i]&&str1[i]==str3[i]&&str3[i]==str2[i]){  
                count+=1;  
            }  
        }  
        int n;  
        n=ts-count;  
        printf("%d",n);  
        return 0;  
    }
```
## 2.First non repeated character and last repeated character in a word.  
```c
#include <stdio.h>  
#include <string.h>  
  
int main() {  
    char str[100];  
    int f1 = 0, f2 = 0;  
  
    fgets(str, sizeof(str), stdin);  
    str[strcspn(str, "\n")] = '\0';  
  
    for (int i = 0; i < strlen(str); i++) {  
        f1 = 1;  
        for (int j = i + 1; j < strlen(str); j++) {  
            if (str[i] == str[j]) {  
                f1 = 0;  
                break;  
            }  
        }  
        if (f1) {  
            printf("First non-repeated character: %c\n", str[i]);  
            break;  
        }  
    }  
  
    for (int i = strlen(str) - 1; i >= 0; i--) {  
        for (int j = i - 1; j >= 0; j--) {  
            if (str[i] == str[j]) {  
                printf("Last repeated character: %c\n", str[j]);  
                f2 = 1;  
                break;  
            }  
        }  
        if (f2) {  
            break;  
        }  
    }  
  
    return 0;  
}
```

```c
#include <stdio.h>
#include<string.h>

int main() {
    char ch[100];
    char ch1[100]={0};
    
    fgets(ch,sizeof(ch),stdin);
    ch[(strlen(ch)-1)]='\0';
    
    for(int i=0;i<strlen(ch);i++){
        for(int j=i+1;j<strlen(ch);j++){
            if(ch[i]==ch[j]){
                ch1[i]=1;
            }
        }
    }
    for(int i=0;i<strlen(ch);i++){
        if(ch1[i]!=1){
            printf("%c\n",ch[i]);
            break;
        }
    }
     for(int i=strlen(ch)-1;i>=0;i--){
        if(ch1[i]==1){
            printf("%c\n",ch[i]);
            break;
        }
    }
    return 0;
}
```
## 3.Bulls and Cows game
```C
#include <stdio.h>
#include <string.h>

int main() {
    int b = 0, c = 0, k = 0;
    char s[100], g[100];
    
    // Read input strings
    fgets(s, 100, stdin);
    fgets(g, 100, stdin);
    
    // Remove newline character if present
    s[strcspn(s, "\n")] = 0;
    g[strcspn(g, "\n")] = 0;
    
    int len_s = strlen(s);
    int len_g = strlen(g);
    
    // Check if lengths are the same
    if (len_s != len_g) {
        printf("Strings must be of the same length\n");
        return 1;
    }
    
    int visited_s[100] = {0};
    int visited_g[100] = {0};
    
    // Count A
    for (int i = 0; i < len_s; i++) {
        if (s[i] == g[i]) {
            visited_s[i] = 1;
            visited_g[i] = 1;
            b++;
        }
    }
    
    // Count B
    for (int i = 0; i < len_s; i++) {
        if (!visited_s[i]) {
            for (int j = 0; j < len_g; j++) {
                if (!visited_g[j] && s[i] == g[j]) {
                    visited_g[j] = 1;
                    c++;
                    break;
                }
            }
        }
    }
    
    printf("%dA%dB\n", b, c);
    return 0;
}

```
## 4.Email Id Validation.
```C
#include <stdio.h>
#include <string.h>

int main() {
    char mail[100];
    fgets(mail, 100, stdin);
     mail[strcspn(mail, "\n")] = 0;
    int k=1,b1=0,b2=0;
    
        for(int i=0;i<strlen(mail);i++){
            if(mail[0]=='@'&& mail[strlen(mail)-1]=='@'){
            if(mail[i]=='@'&&k!=0){
                b1=1;
                k--;
            }
            if((mail[i]=='.')){
                b2=1;
            }
        }
        }
    if(b1==1&&b2==1){
        printf("True");
        return 0;
    }
     printf("False");
    return 0;
}

```
## 6.Count the occurrence of special characters in the given string.
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char s[100];
    fgets(s, 100, stdin);
    s[strcspn(s, "\n")] = 0;
    int count;
    char visited[100] = {0};
    for (int i = 0; i < strlen(s); i++) {
        if (!visited[i] && !((isalpha(s[i]))&&!(s[i]==' ')) {
            char c = s[i];
            count = 1;
            visited[i] = 1;
            for (int j = i + 1; j < strlen(s); j++) {
                if (s[j] == c && !visited[j]) {
                    count++;
                    visited[j] = 1; 
                }
            }
            printf("%c:%d\n", c, count);
        }
    }
    return 0;
}

```
## 7.Word Frequency Counter
```c
// Online C compiler to run C program online
#include <stdio.h>
#include<string.h>
#include<ctype.h>                                             
int main() {
   char str[100];
   int k=0,count=0;
  fgets(str,100,stdin);
  str[strcspn(str,"\n")] = 0;
    int i, j = 0;
    for (i = 0; str[i] != '\0'; i++) {
        if (isalnum(str[i]) || isspace(str[i])) {
            str[j++] = tolower(str[i]);  // Convert to lowercase for case insensitivity
        }
    }
    str[j] = '\0'; 
  char words[100][100];
  char *word = strtok(str, " ");
  while(word!=NULL){
     strcpy(words[k], word);
      k+=1;
      word = strtok(NULL, " ");
  }
  int visited[100]={0};
  for (int i = 0; i < k; i++) {
      if(visited[i]==0){
          count=1;
      for (int j = i+1; j < k; j++) {
          if(!(strcmp(words[i],words[j]))){
              count+=1;
              visited[j]=1;
          }
         }
         printf("count of \"%s\" : %d \n", words[i],count);
       }
    }
    return 0;
}
```
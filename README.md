# para
P
@Type something…
































































Week 9
Q1
int compare(int a, int b) {
  if(a>b) return 1;
  	else if(a<b) return -1;
  		else return 0;
}

Q2
void swap(int *a,int *b){
  		int n=*a;
 		*a=*b;
  		*b=n;

Q3
void sort(int array[], int n){
	int y;
  	 for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            if(array[i]<array[j]){
                    y=array[i];
                    array[i]=array[j];
                    array[j]=y;
            }
        }
    }
}


Week10
Q1
int elementAt(int *pointer, int n)
{
  return*(pointer+n-1);
}
Q2
int between(int *a, int *b)
{
    int sum=0;
    int *i;
    for(a;a<b;a++) sum=sum+*a;
    return sum;
}

Q3
int merger(int *a, int *b, int *c)
{
  int x[10]={0};
  for(int i=0;i<5;i++) x[i]=*(a+i);
  int j=5;
  for(int k=0;k<5;k++){
    //printf("%d ",x[j]);
   x[j]=*(b+k);
  //printf("%d ",x[j]);
    j=j+1;
  }
  int k=0;
  for(int i=0;i<10;i++){
    for(int j=i+1;j<10;j++){
      int temp;
      if(x[i]>x[j]){
        temp=x[i];
        x[i]=x[j];
        x[j]=temp;
      }
    }
    *(c+k)=x[i];
    //printf("%d \n",x[i]);
    k++;
  }
}
Week12
Q1
char *mystrcat(char *dest, char *src)
{
       strcat(dest,src);
        return dest;
}
char *mystrncat(char *dest, char *src, int n)
{
		strncat(dest,src,n);
        return dest;
}




Q2
char *trim(char *dest)
{
    int count=0;
    char *first=dest;
    char *last=dest+strlen(dest)-1;
    while(*(first)=='\n'||*(first)=='\t'||*(first)==' ') first++;
    while(*(last)=='\n'||*(last)=='\t'||*(last)==' ') last--;
    for(first;first<=last;first++){
        *(dest+count)=*first;
        count++;
    }
    *(dest+count)='\0';
    return dest;
}
Q3
#include<string.h>
char *replace(char *source, char *pattern, char *replacement)
{
    if(strstr(source,pattern)==NULL) return source;
    char *begin=strstr(source,pattern);
    char *end=begin+strlen(pattern);
    char temp[10000];
    int count =0;
    for(end;end<source+strlen(source);end++) {
        temp[count]=*end;
        count++;
    }
    for(int i=0;i<strlen(replacement);i++){
        *(begin+i)=*(replacement+i);
    }
    for(int i=0;i<strlen(temp);i++){
        *(begin+strlen(replacement)+i)=temp[i];
    }
    *(begin+strlen(temp)+strlen(replacement))='\0';
    return source;
}
char *replaceAll(char *source, char *pattern, char *replacement)
{
    if(strstr(source,pattern)==NULL) return source;
    int times=0,length=strlen(source);
    while(strstr(source,pattern)!=NULL){
    char *begin=strstr(source,pattern);
    char *end=begin+strlen(pattern);
    char temp[10000]={'0'};
    int count =0;
    for(end;end<source+strlen(source);end++){
        temp[count]=*end;
        count++;
    }
    for(int i=0;i<strlen(replacement);i++){
        *(begin+i)=*(replacement+i);
    }
    for(int i=0;i<strlen(temp);i++){
        *(begin+strlen(replacement)+i)=temp[i];
        }
    if(strlen(replacement)<strlen(pattern)) *(source+strlen(source)-1)='\0';
    times++;
    }
    *(source+times*(strlen(replacement)-strlen(pattern))+length)='\0';
    return source;
}
Q4
#include <stdio.h>
#include<string.h>
int main()
{
  char str[10000];
  gets(str);
  for(int i=strlen(str);i>=0;i--)
  {
    if(str[i]==' ' ){
      for(int j=i+1;j<strlen(str);j++){
         if(str[j]!=' '){
            printf("%c",str[j]);
         }else{
            break;
         }
      }
    printf(" ");
    }
  }
  for(int i=0;i<strlen(str);i++){
    if(str[i]!=' ')
    printf("%c",str[i]);
    else
        break;
  }
  return 0;
}

#include <stdio.h>
#include <string.h>
#define MAX_SIZE 100 // Maximum string size

int main()
{
    char str[100], reverse[100];
    int len, i, index, wordStart, wordEnd;

    gets(str);

    len   = strlen(str);
    index = 0;

    // Start checking of words from the end of string
    wordStart = len - 1;
    wordEnd   = len - 1;

    while(wordStart > 0)
    {
        // If a word is found
        if(str[wordStart] == ' ')
        {
            // Add the word to the reverse string
            i = wordStart + 1;
            while(i <= wordEnd)
            {
                reverse[index] = str[i];

                i++;
                index++;
            }
            reverse[index++] = ' ';

            wordEnd = wordStart - 1;
        }

        wordStart--;
    }

    // Finally add the last word
    for(i=0; i<=wordEnd; i++)
    {
        reverse[index] = str[i];
        index++;
    }

    // Add NULL character at the end of reverse string
    reverse[index] = '\0';

    printf("%s", reverse);

    return 0;
}


Week14
Q1
#include<stdio.h>
#include<string.h>
int main(){
    int n;
    scanf("%d",&n);
    char str[1000][51];
    for(int i=0;i<n;i++) scanf("%s",*(str+i));
    for(int i=0;i<n;i++){
       for(int j=0;j<n;j++){
        if(strcmp(str+i,str+j)<0){
            char temp[51]={0};
            strcpy(temp,str+i);
            strcpy(str+i,str+j);
            strcpy(str+j,temp);
        }
      }
    }
    for(int i=0;i<n;i++) printf("%s\n",*(str+i));
return 0;
}
Q2
#include<stdio.h>
#include<ctype.h>
int main(){
    char str[10000];
    gets(str);
    int sum=0;
    for(int i=0;i<strlen(str);i++){
        if(str[i]=='F') sum++;
        else if(isdigit(str[i])){
            int times=0;
            char temp[10000]={0};
            while(isdigit(str[i])){
                temp[times]=str[i];
                i++;
                times++;
               }
               sum+=atoi(temp);
            }
        }
        printf("%d",sum);
    return 0;
}
Week15
Q1
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main()
{
  char str[10000];
  gets(str);
  int num[10000];
  int count=0,count1=0;
  char sign[10000];
  for(int i=0;i<strlen(str);i++){				//把字串中的數字或符號存到新陣列中
        if(isdigit(str[i])){
            char temp[10000]={0};
            int times=0;
            while(isdigit(str[i])){
                temp[times]=str[i];
                i++;
                times++;
            }
            i--;
            num[count]=atoi(temp);
            count++;
        }else if(str[i]=='+'|str[i]=='-'|str[i]=='*'|str[i]=='/'){
        sign[count1]=str[i];
        count1++;
        }
  }
  int temp[10000];
  int temp1[10000]={10001};
  int count2=0,count3=0,count4=0,count5=0;//count2 存加減 count3 已經運算完的數字 count4
    for(int i=0;i<strlen(sign);i++){       //運算乘和除
         if(sign[i]!='*'&&sign[i]!='/') {
                sign[count2]=sign[i];
                count2++;
        }else if(sign[i]=='*'){
            num[i+1]=num[i]*num[i+1];
            num[i]=0;
            temp1[count3]=i;
            count3++;
        }else if(sign[i]=='/'){
            num[i+1]=num[i]/num[i+1];
            num[i]=0;
            temp1[count3]=i;
            count3++;
        }
    }
    for(int i=0;i<count;i++){	//把還需要運算的數字存到新陣列裡
      if(i==temp1[count4]){
        count4++;
      }else {
          temp[count5]=num[i];
          count5++;
      }
    }
    for(int i=0;i<count2;i++){					//最後運算加和減
        if(sign[i]=='+'){
            temp[i+1]=temp[i]+temp[i+1];
        }else if(sign[i]=='-'){
            temp[i+1]=temp[i]-temp[i+1];
        }
    }
   printf("%d",temp[count5-1]);
    return 0;
}
Q2
#include <stdio.h>
#include <math.h>
void myprintf(int,int ,int,int ,int ,int ,int (*) []    );
int main(){
    int n,m,times=0;
    scanf("%d %d",&n,&m);
    int temp[n][1000];
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            scanf("%d",&temp[i][j]);
        }
    }
    int x=0,y=0;
    int k=m*n;
    n=n-1;
   myprintf(k,x,y,times,n,m,temp);
    return 0;
}
void myprintf(int k,int x,int y,int times,int n,int m,int (*a)[1000]){
  if(times<k) {
        for(int i=0;i<m;i++) {
            times++;
            if(times>k) break;
            printf("%d ",a[y][x]);
            x++;

        }
        x--;
        y++;
        m--;
        for(int i=0;i<n;i++){
            times++;
            if(times>k) break;
            printf("%d ",a[y][x]);
            y++;
        }
        x--;
        y--;
        n--;
        for(int i=0;i<m;i++){
            times++;
            if(times>k) break;
            printf("%d ",a[y][x]);
            x--;

        }
        y--;
        x++;
        m--;
        for(int i=0;i<n;i++){
            times++;
            if(times>k) break;
            printf("%d ",a[y][x]);
            y--;
        }
        n--;
        x++;
        y++;
    return myprintf(k,x,y,times,n,m,a);
        }
}
Q3
#include <stdio.h>
int main()
{
  char board[20][20];
  for(int i=0;i<19;i++){
    for(int j=0;j<20;j++){
        scanf("%c",&board[i][j]);
    }
  }
   for(int i=0;i<19;i++){
    for(int j=0;j<19;j++){
        if(board[i][j]=='O'&&board[i+1][j]=='O'&&board[i+2][j]=='O'&&board[i-1][j]=='O'&&board[i-2][j]=='O'){
            printf("White");
            return 0;
        }
        if(board[i][j]=='O'&&board[i][j+1]=='O'&&board[i][j+2]=='O'&&board[i][j-1]=='O'&&board[i][j-2]=='O'){
            printf("White");
            return 0;
        }
        if(board[i][j]=='O'&&board[i+1][j+1]=='O'&&board[i+2][j+2]=='O'&&board[i-1][j-1]=='O'&&board[i-2][j-2]=='O'){
            printf("White");
            return 0;
        }
        if(board[i][j]=='O'&&board[i+1][j-1]=='O'&&board[i+2][j-2]=='O'&&board[i-1][j+1]=='O'&&board[i-2][j+2]=='O'){
            printf("White");
            return 0;
        }
         if(board[i][j]=='X'&&board[i+1][j]=='X'&&board[i+2][j]=='X'&&board[i-1][j]=='X'&&board[i-2][j]=='X'){
            printf("Black");
            return 0;
        }
        if(board[i][j]=='X'&&board[i][j+1]=='X'&&board[i][j+2]=='X'&&board[i][j-1]=='X'&&board[i][j-2]=='X'){
            printf("Black");
            return 0;
        }
        if(board[i][j]=='X'&&board[i+1][j+1]=='X'&&board[i+2][j+2]=='X'&&board[i-1][j-1]=='X'&&board[i-2][j-2]=='X'){
            printf("Black");
            return 0;
        }
        if(board[i][j]=='X'&&board[i+1][j-1]=='X'&&board[i+2][j-2]=='X'&&board[i-1][j+1]=='X'&&board[i-2][j+2]=='X'){
            printf("Black");
            return 0;
        }
    }
  }
  printf("No winner");
  return 0;
}
Q4
#include <stdio.h>
#include<string.h>
int main()
{
  char str[10000];
  gets(str);
  char compare[10000];
  gets(compare);
  int sumA=0,sumB=0;
  for(int i=0;i<strlen(str);i++){
    if(str[i]==compare[i]) sumA++;
  }
   for(int i=0;i<strlen(str);i++){
        for(int j=0;j<strlen(str);j++){
            if(compare[i]==str[j]&&i!=j) sumB++;
        }
  }
  printf("%d %d",sumA,sumB);
  return 0;
}
Week16
Q1
#include<stdio.h>
#include<string.h>
struct country{
    double times;
    char name[32];
}temp[1000];
int main(){
    int times;
    scanf("%d",&times);
    char useless = getchar();
    useless = getchar();
    while(times>0){
    int count=0,count1=0;
    char str[32];
    while(fgets(str, 32, stdin) != NULL && str[0] != '\n'){
        if(str[strlen(str)-1] == '\n') str[strlen(str)-1] = '\0';
        if(count==0){
        temp[count].times=1;
        strcpy(temp[count].name,str);
        count++;
        }else {
        int repeat=0;
        for(int i=0;i<count;i++){
            if(strcmp(str,temp[i].name)==0) {
                    repeat++;
                    temp[i].times++;
            }
        }
        if(repeat==0){
        temp[count].times=1;
        strcpy(temp[count].name,str);
        count++;
        }
     }
      count1++;
    }
    for(int i=0;i<count;i++){
        for(int j=0;j<count;j++){
        if(strcmp(temp[i].name,temp[j].name)<0) {
                int temp1;
                char temp2[32];
                temp1=temp[i].times;
                temp[i].times=temp[j].times;
                temp[j].times=temp1;
                strcpy(temp2,temp[i].name);
                strcpy(temp[i].name,temp[j].name);
                strcpy(temp[j].name,temp2);
            }
        }
    }
   for(int i=0;i<count;i++){
    printf("%s %.4lf",temp[i].name,100*temp[i].times/count1);
    if(i+1!=count) printf("\n");
    }
    if(times-1!=0) printf("\n\n");
    times--;
    }
    return 0;
}
Q2
#include<stdio.h>
#include<string.h>
#include<ctype.h>
struct amount{
    int times;
    char alpha;
};
int main(){
    struct amount temp[27];
    int count,count1=0;
    char str[1000][1000];
    scanf("%d",&count);
    char useless=getchar();
    for(int i=0;i<count;i++){
        gets(*(str+i));
    }
    for(int i=0;i<count;i++){
        for(int j=0;j<strlen(*(str+i));j++){
            if(isalpha(str[i][j])){
                int repeat=0;
                for(int k=0;k<count1;k++) if(str[i][j]==temp[k].alpha||str[i][j]==temp[k].alpha+32||str[i][j]==temp[k].alpha-32) {
                        repeat++;
                        temp[k].times++;
                }
                if(repeat==0){
                    temp[count1].times=1;
                    temp[count1].alpha=str[i][j];
                    count1++;
                }
            }
        }
    }
    for(int i=0;i<count1;i++) temp[i].alpha=toupper(temp[i].alpha);
    for(int i=0;i<count1;i++){
       for(int j=0;j<count1;j++){
            if(temp[i].times==temp[j].times&&temp[i].alpha<temp[j].alpha){
                int temp1;
                char temp2;
                temp1=temp[i].times;
                temp[i].times=temp[j].times;
                temp[j].times=temp1;
                temp2=temp[i].alpha;
                temp[i].alpha=temp[j].alpha;
                temp[j].alpha=temp2;
            }else if(temp[i].times>temp[j].times){
                int temp1;
                char temp2;
                temp1=temp[i].times;
                temp[i].times=temp[j].times;
                temp[j].times=temp1;
                temp2=temp[i].alpha;
                temp[i].alpha=temp[j].alpha;
                temp[j].alpha=temp2;
            }
       }
    }
    for(int i=0;i<count1;i++) printf("%c %d\n",toupper(temp[i].alpha),temp[i].times);
    return 0;
}
Q3
#include<stdio.h>
#include<string.h>
struct country{
    int time;
    char name[100];
};
int main(){
    struct country temp[2100];
    int times,count=0;
    scanf("%d",&times);
   char useless=getchar();
    for(int i=0;i<times;i++){
        char str[100];
        char temp1[100];
        scanf("%s",temp1);
        gets(str);
    if(count==0){
        strcpy(temp[count].name,temp1);
        temp[count].time=1;
        count++;
    }else{
    int repeat=0;
    for(int j=0;j<count;j++){
        if(strcmp(temp[j].name,temp1)==0){
            repeat=1;
            temp[j].time++;
        }

    }
    if(repeat==0){
        strcpy(temp[count].name,temp1);
        temp[count].time=1;
        count++;
            }
        }
    }
    for(int i=0;i<count;i++){
        for(int j=0;j<count;j++){
            if(strcmp(temp[i].name,temp[j].name)<0){
                int temp3;
                char temp2[100]={'0'};
                temp3=temp[i].time;
                temp[i].time=temp[j].time;
                temp[j].time=temp3;
                strcpy(temp2,temp[i].name);
                strcpy(temp[i].name,temp[j].name);
                strcpy(temp[j].name,temp2);
            }
        }
    }
    for(int i=0;i<count;i++) {
            printf("%s %d\n",temp[i].name,temp[i].time);

    }
    return 0;
}
Q4
#include <stdio.h>
#include <string.h>

int main(){
    char n[10001];
    while (scanf("%s", n) == 1){
        int i, sum=0, max=1;
        for (i=0; i<strlen(n); i++){
            int d=0;
            if (isdigit(n[i]))
                d=n[i]-48;
            else if (isupper(n[i]))
                d=n[i]-55;
            else if (islower(n[i]))
                d=n[i]-61;
            sum+=d;
            if (d > max)
                max=d;
        }

        for (i=max; i<=62; i++){
            if (sum%i == 0){
                printf("%d\n", i+1);
                break;
            }
            else if (i == 62)
                printf("such number is impossible!\n");
        }
    }
    return 0;
}

#include <stdio.h>
#include <string.h>
int main() {
    char s[100005];
    int i, j;
    while(scanf("%s", s) == 1) {
        char *p = s;
        if(*p == '+')
        	p++;
        else if(*p == '-')
        	p++;
        int mn = 1, err = 0, len;
        len = strlen(p);
        for(i = 0; i < len; i++) {
        	if(p[i] >= '0' && p[i] <= '9') {
            	p[i] -= '0';
            } else if(p[i] >= 'A' && p[i] <= 'Z') {
            	p[i] = p[i]-'A'+10;
        	} else if(p[i] >= 'a' && p[i] <= 'z') {
            	p[i] = p[i]-'a'+36;
        	} else
            	err = 1;
        	if(p[i] > mn)
           	 mn = p[i];
        }
        mn++;
        for(i = mn; i <= 62; i++) {
        	int tmp = 0, k = i-1;
        	for(j = 0; j < len; j++) {
            	tmp = tmp*i + p[j];
            	tmp %= k;
        	}
        	if(tmp == 0)  break;
        }
        if(i == 63 || err == 1)
        	puts("such number is impossible!");
        else
        	printf("%d\n", i);
    }
    return 0;
}


Q5
#include<stdio.h>
int main(){
    int n,m,count=0;
    while(scanf("%d%d",&n,&m),n!=0||m!=0){
       count++;
       if(count>1) printf("\n");
       printf("Field #%d:\n",count);
       char board[100][100];
       char useless=getchar();
       for(int i=0;i<n;i++){
        for(int j=0;j<m+1;j++) scanf("%c",&board[i][j]);
       }
       for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            if(board[i][j]=='*') printf("%c",board[i][j]);
            else{
               int sum=0;
               if(board[i+1][j+1]=='*'&&i+1<n&&j+1<m) sum++;
               if(board[i-1][j-1]=='*'&&i-1>=0&&j-1>=0) sum++;
               if(board[i+1][j-1]=='*'&&i+1<n&&j-1>=0) sum++;
               if(board[i-1][j+1]=='*'&&i-1>=0&&j+1<m) sum++;
               if(board[i+1][j]=='*'&&i+1<n) sum++;
               if(board[i][j+1]=='*'&&j+1<m) sum++;
               if(board[i-1][j]=='*'&&i-1>=0) sum++;
               if(board[i][j-1]=='*'&&j-1>=0) sum++;
               printf("%d",sum);
         }
        }
       puts("");
       }
    }
    return 0;
}











































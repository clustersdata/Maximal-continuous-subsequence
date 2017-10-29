# 最大连续子序列

Problem Description

给定K个整数的序列{ N1, N2, ..., NK }，其任意连续子序列可表示为{ Ni, Ni+1, ...,
Nj }，其中 1 <= i <= j <= K。最大连续子序列是所有连续子序列中元素和最大的一个，
例如给定序列{ -2, 11, -4, 13, -5, -2 }，其最大连续子序列为{ 11, -4, 13 }，最大和
为20。要求编写程序得到最大和，现在增加一个要求，即还需要输出该
子序列的第一个和最后一个元素。

Input

测试输入包含若干测试用例，每个测试用例占2行，第1行给出正整数K( < 10000 )，第2行给出K个整数，中间用空格分隔。当K为0时，输入结束，该用例不被处理。

Output

对每个测试用例，在1行里输出最大和、最大连续子序列的第一个和最后一个元
素，中间用空格分隔。如果最大连续子序列不唯一，则输出序号i和j最小的那个（如输入样例的第2、3组）。若所有K个元素都是负数，则定义其最大和为0，输出整个序列的首尾元素。

Sample Input

6 -2 11 -4 13 -5 -2 10 -10 1 2 3 4 -5 -23 3 7 -21 6 5 -8 3 2 5 0 1 10 3 -1 -5 -2 3 -1 0 -2 0

Sample Output

20 11 13 10 1 4 10 3 5 10 10 10 0 -1 -2 0 0 0 

代码：

#include<stdio.h>

#include<string.h>

#define MAX 20000

int arr[MAX];


int main()

{

    int num,temp,i,flage;
    
    int sum,start,end,max=-32768;
    
    scanf("%d",&num);
    
    while(num!=0)
    
    {
    
        memset(arr,0,MAX*sizeof(int));
        
        for(i=0;i<num;i++)
        
            scanf("%d",&arr[i]);
            
        sum=0;
        
        temp=0;
        
        max=-32768;
        
        flage=0;
        
        for(i=0;i<num;i++)
        
        {
        
            if(arr[i]>=0)    flage=1;
            
            sum+=arr[i];
            
            
            if(max<sum)  {   max=sum;   start=temp;    end=i;   }
            
            if(sum<0)    {   sum=0;      temp=i+1;             }
            
        }
        
        if(flage)    printf("%d %d %d\n",max,arr[start],arr[end]);
        
        else        printf("0 %d %d\n",arr[0],arr[num-1]);
        
        scanf("%d",&num);
        
    }
    
    return 0;
    
}

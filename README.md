//函数与模块化程序设计笔记
模块化程序设计：通过功能分解实现模块化程序设计，功能分解是一个自顶向下，逐步求精的过程，不仅使程序更容易理解，也更容易调试与维护。
函数定义：函数与变量一样，在使用之前必须先定义；函数名是函数的唯一标识，用于说明函数的功能；函数体必须用一对花括号包围，“{}”是函数体的定界符。
函数的分类： 1.标准库函数：比如printf()、scanf()等。
            2.自定义函数：如果库函数不能满足程序者的编程需要，那么久需要编程者自行编写函数来完成自己的所需功能。
内部变量：在函数体的内部定义的变量，只能在函数体内访问。函数头部参数的变量，称为形参变量，也是内部变量，即只能在函数体内访问。
形参表：函数的入口
//计算整数n的阶乘n!方法：
1.迭代法
#include<stdio.h>
long Fact(int n)
{
  int i;
  long result = 1;
  for(i=2;i<=n;i++)
  {
    result *= i;
  }
  return result;
}
int main(void)
{
  int m;
  long ret;
  printf("Input m:");
  scanf("%d",&m);
  ret = Fact(m);
  printf("%d=%ld\n",m,ret);
  return 0;
}
2.计数控制的循环
#include<stdio.h>
int main(void)
{
  int i,n;
  long p = 1;
  printf("Input n:");
  scanf("%d",&n);
  for(i=1;i<=n;i++)
  {
    p = p * i;
  }
  printf("%d!=%ld\n",n,p);
  return 0;
}
//嵌套循环
#include <stdio.h> 
int main (void)
{
  int i,j， n;
  long p, sum = 0; 
  printf("Input n: ");
  scanf("%d",&n);
  for(i=1;i<=n;i++)
  {
    p = 1;
    for(j=1;j<=i;j++)
    {
      p = p * i;
    }
    sum += p; 
  }
  printf("sum=%ld\n",n,sum);
  return 0;
}
//函数的递归调用与递归函数
eg:
1.#include <stdio.h>
int Ack( int m, int n );
int main()
{
    int m, n;
    scanf("%d %d", &m, &n);
    printf("%d\n", Ack(m, n));
    return 0;
}

int Ack( int m, int n )
{
    if(m==0)
        return n+1;
    else if(n==0&&m>0)
        return Ack(m-1,1);
    else
        return Ack(m-1,Ack(m,n-1));
}
2.#include <stdio.h>
int f( int n );
int main()
{
    int n;
    scanf("%d", &n);
    printf("%d\n", f(n));
    return 0;
}
int f( int n )
{
    if(n==0)
        return 0;
    else if(n==1)
        return 1;
    else
        return f(n-2)+f(n-1);
}
//二维矩阵的转置
##通过输入行列式的行与列，再输入原矩阵，实现矩阵的二维转置
#include<stdio.h>

int main(void)
{

    int row,col;
    printf("请输入行数和列数(都小于10)：");
    scanf("%d %d",&row,&col);
    if(row>=10||col>=10)
    {
        printf("行数和列数都必须小于10！\n");
        return 1;
    }

    int arr[row][col];

    printf("原矩阵:\n");
    for(int i=0;i<row;i++)
    {
        for(int j=0;j<col;j++)
        {
            scanf("%d",&arr[i][j]);
        }
    }
    printf("转置后矩阵:\n");
    for(int i=0;i<row;i++)
    {
        for(int j=0;j<col;j++)
        {
            printf("%d ",arr[i][j]);
        }
        printf("\n");
    }
    return 0;
}
//求某两个整数之间的最大公约数（通过函数的递归调用）
#include<stdio.h>
int gcd(int x,int y)
{
    while(y!=0)
    {
       int temp=y;
        y=x%y;
        x=temp;
     }
    return x;
}
int main()
{
    int x, y;

    scanf("%d %d", &x, &y);
    printf("%d\n", gcd(x, y));
    return 0;
}
//用于多路选择的switch语句
#include<stdio.h>
void FindMax(int arr[],int n,int *max,int *maxd);
void FindMin(int arr[],int n,int *min,int *mind);
int main(void)
{
    int arr[10];
    int max,min,maxd,mind;
    int i;
    for(i=0;i<10;i++)
    {
        scanf("%d",&arr[i]);
    }
    FindMax(arr,10,&max,&maxd);
    FindMin(arr,10,&min,&mind);
    printf("max value %d position %d\n",max,maxd);
    printf("min value %d position %d\n",min,mind);
    return 0;
}
void FindMax(int arr[],int n,int *max,int *maxd)
{
    int i;
    *max=arr[0];
    *maxd=0;
    for(i=1;i<n;i++)
    {
        if(arr[i]>*max)
        {
            *max=arr[i];
            *maxd=i;
        }
    }
}
void FindMin(int arr[],int n,int *min,int *mind)
{
    int i;
    *min=arr[0];
    *mind=0;
    for(i=1;i<n;i++)
    {
        if(arr[i]<*min)
        {
           *min=arr[i];
           *mind=i;
        }

    }

}

//求一个数的同构数
#include<stdio.h>
int gcd(int x,int y)
{
    while(y!=0)
    {
       int temp=y;
        y=x%y;
        x=temp;
     }
    return x;
}
int main()
{
    int x, y;
    scanf("%d %d", &x, &y);
    printf("%d\n", gcd(x, y));
    return 0;
}
//排序与查找
在一堆乱序的数组中找出最大值最小值的数值并且输出其下角标
#include<stdio.h>
void FindMax(int arr[],int n,int *max,int *maxd);
void FindMin(int arr[],int n,int *min,int *mind);
int main(void)
{
    int arr[10];
    int max,min,maxd,mind;
    int i;
    for(i=0;i<10;i++)
    {
        scanf("%d",&arr[i]);
    }
    FindMax(arr,10,&max,&maxd);
    FindMin(arr,10,&min,&mind);
    printf("max value %d position %d\n",max,maxd);
    printf("min value %d position %d\n",min,mind);
    return 0;
}
void FindMax(int arr[],int n,int *max,int *maxd)
{
    int i;
    *max=arr[0];
    *maxd=0;
    for(i=1;i<n;i++)
    {
        if(arr[i]>*max)
        {
            *max=arr[i];
            *maxd=i;
        }
    }
}
void FindMin(int arr[],int n,int *min,int *mind)
{
    int i;
    *min=arr[0];
    *mind=0;
    for(i=1;i<n;i++)
    {
        if(arr[i]<*min)
        {
           *min=arr[i];
           *mind=i;
        }
    }
}
//通过对数字的分解求出其固定组合方式
#include<stdio.h>
int main(void)
{
    int n,b,g,c;
    scanf("%d",&n);
    for(b=0;b<=n/4;++b)
    {
        for(g=0;g<=(n-4*b)/3;++g)
        {
            c=n-b-g;
            if(c%2==0 && c/2+b+g==n)
            {
                printf("%d %d %d\n",b,g,c/2);
            }
        }
    }
    return 0;
}



















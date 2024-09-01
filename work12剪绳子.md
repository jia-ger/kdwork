给你一根长度为 n 绳子，请把绳子剪成 m 段（m、n 都是整数，2≤n≤58并且 m≥2）
每段的绳子的长度记为 k[1]、k[2]、……、k[m]
k[1]k[2]…k[m]可能的最大乘积是多少？
例如当绳子的长度是 8 时，我们把它剪成长度分别为 2、3、3 的三段，此时得到最大的乘积 18
样例
输入：8
输出：18

题解//https://blog.csdn.net/Y_Mlsy/article/details/107357681
#include<cstdio>
#include<cmath>
using namespace std;
int jia()
{    int n,m;
    scanf("%d%d",&n,&m);
    if(n==2) return 1;
    if(n==3)return 2;  
    int a=n/3;int b=n%3;
    if(b==0) return pow(3,a);
    if(b==1)return pow(3,a-1)*4;
    else return pow(3,a)*2;
}
int main()
{
    
    
    printf("%d",jia());
    
    return 0;
}

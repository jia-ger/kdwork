牛客例题<两数之和>
对于给定的正整数Z，你需要找出两个不同的正整数X,Y，使得X+Y=Z成立
如果不存在输出NO
存在输出YES且换行输出结果


题解
#include<stdio.h>
int main()
{
 int z;
 scanf("%d",&z);
    if(z<=2)
        printf("NO");
    else
            printf("YES\n%d %d",1,z-1);
    
    
    return 0;
}

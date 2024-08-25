给定 n组 ai,bi;pi，对于每组数据，求出 a 的b次方mod p 的值,
输入格式
第一行包含整数 n。
接下来n 行，每行包含三个整数 ai,bi,pi。
输出格式
对于每组数据，输出一个结果，表示a的b次方mod p的值。
每个结果占一行。

题解（不是最优解，暴力解法，当b过大，会导致数据溢出无法实现）
#include <stdio.h>
int jia(int a, int b,int c)
{
    int x = 1;
    for (int i = 1; i <= b; i++)
        x = x * a;
        x = x % c;
        return x;
}

int main() {
    int n;
    scanf("%d", &n); 

    for (int i = 0; i < n; ++i) {
        long long ai, bi, pi;
        scanf("%d %d %d", &ai, &bi, &pi);
        printf("%d\n", jia(ai, bi, pi));
    }
    return 0;
}

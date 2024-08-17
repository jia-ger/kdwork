一个楼梯共有 ” 级台阶，每次可以走一级或者两级，问从第0 级台阶走到第 ” 级台阶一共有多少种方案
输入格式
共一行，包含一个整数 n。
输出格式
共一行，包含一个整数，表示方案数。
数据范围
1 ≤n≤ 15

题解
#define _crt_secure_no_warnings 1
#include <stdio.h>
int jia( int n)
{
	if (n == 1)
		return 1;
	if (n == 2)
		return 2;
	if (n > 2)
		return jia(n - 1) + jia(n-2);
}
int main()
{
	int n;
	printf("请输入n的值：");
	scanf_s("%d", &n);
	if (n < 1 || n>15)
		printf("值不在范围内\n");
	else
		printf("一共有%d种方案\n", jia(n));
	return 0;
}

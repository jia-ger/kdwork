快速幂解法
#include <stdio.h>
int jia(int a, int b, int p)
{
	long long t = 1;
	while (b != 0)
	{if (b % 2 == 1)
	t = (t * a) % p;
	a = (a * a) % p;
	b = b >> 1;
    }
	return t;
}
int main()
{
	int n;
	scanf("%d", &n);
	for (int i = 1; i <= n; i++)
	{
		int ai, bi, pi;
		scanf("%d%d%d", &ai, &bi, &pi);
		printf("%d\n", jia(ai, bi, pi));
	}
	return 0;
}

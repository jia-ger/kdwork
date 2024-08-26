基础动态规划
从西北角进去，东南角出来地里每个道路的交叉点上都有种着一株花生苗，上面有若干颗花生，经过一株花生苗就能摘走该它上面所有的花
生。Hello Kitty只能向东或向南走，不能向西或向北走。问Hello Kitty最多能够摘到多少颗花生。
输入格式
第一行是一个整数T，代表一共有多少组数据。
接下来是T组数据。
每组数据的第一行是两个整数，分别代表花生苗的行数R和列数 C。
每组数据的接下来R行数据，从北向南依次描述每行花生苗的情况。每行数据有C个整数，按从西向东的顺序描述
了该行每株花生苗上的花生数目M。
输出格式
对每组输入数据，输出一行，内容为Hello Kitty能摘到得最多的花生颗数。
数据范围
1 <T< 100,
1<R,C<100
0< M < 1000
输入样例:
2
2 2
1 1
3 4
2 3
2 3 4
165
输出样例:
8
16

题解
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>
const int N = 110;
int n, m;
int x[N][N];
int ans[N][N];
int max(int a, int b)
{
	if (a > b)
		return a;
	else if (a < b)
		return b;
	else if (a == b)
		return a;
}
int solve()
{
	scanf("%d%d", &n, &m);
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			scanf("%d", &x[i][j]);
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			ans[i][j] = max(ans[i][j - 1] + x[i][j], ans[i - 1][j] + x[i][j]);
	return ans[n][m];
}
int main()
{
	int t;
	scanf("%d", &t);
	while (t--)
	{
		printf("%d", solve());
	}
	return 0;
}

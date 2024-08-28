有 N 件物品和一个容量是 V 的背包。每件物品只能使用一次。
第讠件物品的体积是 vi，价值是 wi。
求解将哪些物品装入背包，可使这些物品的总体积不超过背包容量，且总价值最大。
输出最大价值。
输入格式
第一行两个整数，N，V，用空格隔开，分别表示物品数量和背包容积。
接下来有 N 行，每行两个整数 v,w;，用空格隔开，分别表示第之件物品的体积和价值。
输出格式
输出一个整数，表示最大价值。
数据范围
0<N,V≤ 1000
0 < vi,wi< 1000
输入样例
4 5
1 2
2 4
3 4
4 5
输出样例:
8

题解
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>
int N, V;
const int Q = 110;
int v[Q], w[Q];
int ans[Q][Q];
int max(int a,int b)
{
	if (a > b)return a;
	if (a == b)return a;
	if (a < b)return b;
}
int solve()
{
	
	for (int i = 1; i <= N; i++)
	{   
		scanf("%d%d", &v[i], &w[i]);
	}
	for (int i = 1; i <= N; i++)
		for (int j = 0; j <= V; j++)
			if (v[i] < j) ans[i][j] = max(ans[i - 1][j], ans[i - 1][j - v[i]] + w[i]);
			else if (v[i] == j) ans[i][j] = max(w[i], ans[i - 1][j]);
			else if (v[i] > j)ans[i][j] = ans[i - 1][j];

				return ans[N][V];
}
int main()
{
	scanf("%d %d", &N, &V);
	printf("%d", solve());
	return 0;
}

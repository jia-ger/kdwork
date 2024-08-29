#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>
int N, V;
const int Q = 1010;
int v[Q], w[Q];
int ans[Q];
int max(int a,int b)
{
	if (a > b)return a;
	if (a == b)return a;
	if (a < b)return b;
}
int solve()
{
	ans[0]=0;
	for (int i = 1; i <= N; i++)
	{   
		scanf("%d%d", &v[i], &w[i]);
	}
	for (int i = 1; i <= N; i++)
		for (int j = V; j >=v[i]; j--)//这里采用逆序是因为逆序 ans[j - v[i]]相当于ans[i-1][j-v[i]]如果是顺序则认为是ans[i][j-v[i]]
			if (v[i] < j) ans[i] = max(ans[j], ans[j - v[i]] + w[i]);
			else if (v[i] == j) ans[i][j] = max(w[i], ans[j]);
			else if (v[i] > j)ans[i][j] = ans[j];

				return ans[V];
}
int main()
{
	scanf("%d %d", &N, &V);
	printf("%d", solve());
	return 0;
}

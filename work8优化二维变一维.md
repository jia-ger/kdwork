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
			 ans[j] = max(ans[j], ans[j - v[i]] + w[i]);
				return ans[V];
}
int main()
{
	scanf("%d %d", &N, &V);
	printf("%d", solve());
	return 0;
}

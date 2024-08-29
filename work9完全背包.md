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
		for (int j = v[i]; j <=V; j++)//跟01背包这里不同顺序将会考虑所有重复的情况，这也是为什么01背包必须逆序的原因
		 ans[j] = max(ans[j], ans[j - v[i]] + w[i]);
		
				return ans[V];
}
int main()
{
	scanf("%d %d", &N, &V);
	printf("%d", solve());
	return 0;
}

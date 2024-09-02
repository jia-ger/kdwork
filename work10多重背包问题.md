//相当于01背包变形，只需要多加一组循环就行

#include<stdio.h>
#include<algorithm>
int N,V;
const int Q=110;
int v[Q],w[Q],s[Q];
int ans[Q];
int solve()
{
    
    for(int i=1;i<=N;i++)
    scanf("%d%d%d",&v[i],&w[i],&s[i]);
    for(int i=1;i<=N;i++)
    for(int j=V  ;j>=0   ;j--)
    for(int k=0 ;k<=s[i]&& k*v[i]<=j    ;k++)
    ans[j]=std::max(ans[j],ans[j-k*v[i]]+k*w[i]);//如果不想输入std::可以在前面声明using namespace std;
    
    return ans[V];
    
}
int main()
{
    scanf("%d%d",&N,&V);
    printf("%d",solve());
    return 0;
}

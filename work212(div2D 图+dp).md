> https://codeforces.com/contest/2176/problem/D

<details>
<summary>源代码</summary>

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define endl '\n'
typedef pair<int,int> PII;
const int N=2e5+10;
const int INF=1e18;
const int MOD=998244353;
#define ll __int128

map<PII,int>mp;
int n,m;
int a[N],f[N];//a是每个点的权值 f[i]就是以哪条边为开头的方案数 
struct edge{
    int u,v,w;
    bool operator < (const edge &other)const{
        if(u!=other.u)return u<other.u;
        if(w!=other.w)return w<other.w;
        return v<other.v;
    }
};
int dfs(vector<edge> &e,int x){
    if(f[x]!=-1)return f[x];
    int u=e[x].u,v=e[x].v,sum=a[u]+a[v];
    f[x]=1;//他本身 
    if(mp[{v,sum}])return f[x]=(f[x]+mp[{v,sum}])%MOD;//如果计算过后面以v，sum为边的个数直接返回防止重复计算 
    edge tep={v,0,sum};//直接返回以v为起点 u>=sum的情况 
    int pos=lower_bound(e.begin(),e.end(),tep)-e.begin();//核心！ 利用二分迅速找到符合要求的边 使复杂度边为mlogm 
    int res=0;
    for(int i=pos;i<e.size();i++){
        if(e[i].u!=v||e[i].w!=sum)break;
        res=(res+dfs(e,i))%MOD;//第i条边的 v 是符合要求的 所以计算出 第i条边为开头的方案数 
    }
    f[x]=(f[x]+res)%MOD;
    mp[{v,sum}]=res;
    return f[x];
}
void solve()
{
    mp.clear();
    cin>>n>>m;
    for(int i=0;i<=m+5;i++)f[i]=-1;
    for(int i=1;i<=n;i++)cin>>a[i];
    vector<edge> e;
    for(int i=1;i<=m;i++){
        int u,v;
        cin>>u>>v;
        e.push_back({u,v,a[v]});
    }
    sort(e.begin(),e.end());
    int ans=0;
    for(int i=0;i<m;i++)
    ans=(ans+dfs(e,i))%MOD;
    cout<<ans<<endl;
  
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   
  
   while(T--)solve();
   
    return 0;
}
```
</details>

https://www.luogu.com.cn/problem/P2709

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=5e4+10;
const int INF=1e7;
const int MOD=998244353;
//#define ll __int128

//区间分块 分块处理 优雅的暴力算法  复杂度O(n*sqrt(n)) 
//同块之间按照 r从小到大排序 不同块之间 按块先后排序

int block;  
int a[N]; 
itn ans[N];
int vis[N];
struct abd{
	int l,r,id;
}p[N]; 
bool cmp(abd x,abd y){
	if(x.l/block!=y.l/block){
		return x.l/block<y.l/block;
	}
	return x.r<y.r;
}

int anss;
void update(int u,int cnt){
	u=a[u]; 
	if(cnt==1)anss=anss+2*vis[u]+1;
	else anss=anss-2*vis[u]+1;
	vis[u]+=cnt;
	 
} 
void solve() {
  int n,m,k;
  cin>>n>>m>>k;
  block=(int)sqrt(n); 
  for(itn i=1;i<=n;i++)cin>>a[i];
  for(itn i=1;i<=m;i++)cin>>p[i].l>>p[i].r,p[i].id=i;
  
  sort(p+1,p+n+1,cmp);
  int l=1,r=0;
  for(itn i=1;i<=n;i++){
  	while(l>p[i].l)update(--l,1);
  	while(l<p[i].l)update(l++,-1);
  	while(r>p[i].r)update(r--,-1);
  	while(r<p[i].r)update(++r,1);
  	ans[p[i].id]=anss;
  } 
  
  for(itn i=1;i<=m;i++)
  cout<<ans[i]<<endl; 
}



signed main() {

	cin.tie(0)->sync_with_stdio(0);

	int T=1;
//	cin>>T;
//   mt19937 rand(time(nullptr));
	while(T--)solve();

	return 0;
}

```

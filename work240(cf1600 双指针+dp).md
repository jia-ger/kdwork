https://codeforces.com/problemset/problem/1994/C

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=2e5+10;
const int INF=1e18;
const int MOD=998244353;
//#define ll __int128

int n,x,a[N],cnt[N],dp[N];
void solve() {
	
	cin>>n>>x;
	memset(dp,0,sizeof dp);
	for(int i=1;i<=n;i++) cin>>a[i];
	int l=1,r=0,sum=0;
	for(;l<=n;l++){
		while(r<=n&&sum<=x) r++,sum+=a[r];
		cnt[l]=r;//双指针 处理每个l和对应的>x的R
		sum-=a[l];
	}
	sum=0;
	for(int i=n;i>=1;i--){
		if(cnt[i]==n+1) continue;
		else dp[i]=dp[cnt[i]+1]+1;
		sum+=dp[i];//dp[i]以i为起点 i-r和为0的个数
	}
	cout<<n*(n+1)/2-sum<<endl;
}



signed main() {

	cin.tie(0)->sync_with_stdio(0);
	
	int T=1;
	cin>>T;

//   mt19937 rand(time(nullptr));
	while(T--)solve();

	return 0;
}

```

https://atcoder.jp/contests/abc450/tasks/abc450_d


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
const int INF=1e7;
const int MOD=998244353;
//#define ll __int128

void solve() {
   
   itn n,k;cin>>n>>k;
   deque<int>a;
   for(itn i=1;i<=n;i++){
   	int x;
   	cin>>x;
   	a.push_back(x%k);
   }
   sort(a.begin(),a.end());
   int ans=1e18;
   
   for(int i=1;i<=n;i++){
   	int x=a.front();
   	a.pop_front();
   	ans=min(ans,a.back()-x);
   	a.push_back(x+k);
   }
   
   cout<<ans<<endl;
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


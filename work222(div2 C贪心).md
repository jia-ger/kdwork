https://codeforces.com/contest/2208

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
   itn n;
   cin>>n;
   vector<double>c(n+1),p(n+1);
   for(itn i=1;i<=n;i++)cin>>c[i]>>p[i];
   //从后往前选 选或不选 假设刚开始s=1 
   //不选 ans[i]=ans[i+1] 选 ans[i]=ans[i+1]*(1-p[i]/100)+c[i]*s; 
   double s=1,ans=0;
   for(itn i=n;i>=1;i--)
   {
     if(ans*(1-p[i]/100)+c[i]*s>ans)
	 ans=ans*(1-p[i]/100)+c[i];	
   } 
   cout << fixed << setprecision(10)<<ans<<endl;
   
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

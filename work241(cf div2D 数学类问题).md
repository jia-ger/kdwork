https://codeforces.com/contest/2225/problem/D

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



//前缀异或 p[r]^p[l-1]=0 p[r]=p[l-1]=1/0
//1 n+1 0 n 
int cnt(itn N, int rem) {
    if (N < rem) return 0;
    return (N - rem) / 4 + 1;
}


itn cnt0(itn N) {
    if (N < 0) return 0;
    return (1 + cnt(N, 3));
}


int cnt1(itn N) {
    if (N < 0) return 0;
    return cnt(N, 1);
}

void solve() {
    int n, x;
    cin>>n>>x;

   
    
    itn c0_i = cnt0(x - 1) % MOD;
    itn c0_j = (cnt0(n) - cnt0(x - 1) + MOD) % MOD;
    int c1_i = cnt1(x - 1) % MOD;
    int c1_j = (cnt1(n) - cnt1(x - 1) + MOD) % MOD;

    int ans = (c0_i * c0_j % MOD + c1_i * c1_j % MOD) % MOD;
    cout << ans << endl;
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

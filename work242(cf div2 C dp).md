https://codeforces.com/contest/2225/problem/C

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




void solve() {
    int n;
    cin>>n;
    string s1, s2;
    cin >> s1 >> s2;

    // dp[i] 表示匹配完前 i 列所需的最少涂色次数
    vector<int> dp(n + 1, INF);
    dp[0] = 0;
    for (int i = 1; i <= n; i++) {
        // 第 i 列垂直匹配
        dp[i] = min(dp[i], dp[i-1] + (s1[i-1] != s2[i-1] ? 1 : 0));

        //第 i-1 列和第 i 列水平匹配
        if (i >= 2) {
            int cost = (s1[i-2] != s1[i-1] ? 1 : 0) + (s2[i-2] != s2[i-1] ? 1 : 0);
            dp[i] = min(dp[i], dp[i-2] + cost);
        }
    }

    cout << dp[n] << endl;
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

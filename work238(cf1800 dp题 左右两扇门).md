https://codeforces.com/problemset/problem/2078/D

> 解析：https://www.luogu.com.cn/article/acs3hbgl

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=31;
const int INF=1e18;
const int MOD=998244353;
//#define ll __int128


int t, n, a[N][2];
long long f[N + 1][2];
char op[N][2];
	
void solve() {
long long ans = 0;
		cin >> n;
		for (int i = 1; i <= n; i++)
		cin >> op[i][0] >> a[i][0] >> op[i][1] >> a[i][1];
		f[n + 1][0] = f[n + 1][1] = 1;
		for (int i = n; i >= 1; i--)
		{
			for (int j = 0; j <= 1; j++)
				if (op[i][j] == '+')
				{
					f[i][j] = f[i + 1][j];
					ans += a[i][j] * max(f[i + 1][0], f[i + 1][1]);
				}
				else f[i][j] = f[i + 1][j] + (a[i][j] - 1) * max(f[i + 1][0], f[i + 1][1]);
		}
		cout << ans + f[1][0] + f[1][1] << endl;
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

> https://codeforces.com/contest/2176/problem/C

```c++
#include <bits/stdc++.h>
typedef long long ll;
constexpr int N = 2e5 + 10;
using namespace std; 
int n;
ll a[N], b[N], ans[N];
ll sum[N];
ll l, r;
ll s = 0;
void solve() {
	cin >> n;
	s = l = r = 0;
	for (int i = 1; i <= n; ++i) {
		ll x; cin >> x;
		if (x % 2) a[++l] = x;
		else b[++r] = x; 
	}
	sort(a + 1, a + 1 + l, greater<ll>());
	sort(b + 1, b + 1 + r, greater<ll>());
	for (int i = 1; i <= r; ++i) sum[i] = sum[i - 1] + b[i]; 
	if (l == 0) {
		for (int i = 1; i <= n; ++i) cout << "0 ";
		cout << '\n';
		return;
	}
	ans[1] = a[1];
	for (int i = 2; i <= r + 1; ++i) {
		ans[i] = ans[i - 1] + b[i - 1];
	} 
	if (r + 1 < n) {
		int q = r + 2;
		for (int i = q; i <= n; ++i) {
			if ((i - r) % 2 == 0) {
				if (r == 0 || (i - r) >= l) ans[i] = 0;
				else ans[i] = sum[r - 1] + a[1];
			}
			else ans[i] = ans[r + 1];
		}  
	}
	for (int i = 1; i <= n; ++i) cout << ans[i] << ' ';
	cout << '\n';
}
int main() {
	ios::sync_with_stdio(false), cin.tie(0), cout.tie(0);
	int _;
	cin >> _;
	while (_--) solve();
	return 0;
}
```

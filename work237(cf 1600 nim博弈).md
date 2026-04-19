https://codeforces.com/problemset/problem/2181/F

> Alice 和 Bob 花了两回合把一堆石子取光了，先后手不变。我们用同样的方法取光 n−1 堆石子。
> 只剩一堆石子时，Bob 只能选这一堆。注意：Alice 不会再傻乎乎的留一颗石子，让 Bob 拿完。 这已经是最后一堆了，Alice 一定会取光。然而上述策略是基于所有 ai都大于 1 的。
> 如果有 a i =1，相当于交换了先后手。可以用变量 cnt 记录 ai=1 的数量。如果 cnt 是偶数，先手赢；如果 cnt 是奇数，后手赢。
> 如果所有 ai全都等于 1，这时候反而 cnt 是奇数，先手赢；cnt 是偶数，后手赢。这就是 cnt 减要一的原因。

```c++

#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=3e5+10;
const int INF=1e18;
const int MOD=998244353;
//#define ll __int128



	
void solve() {
	int n; cin >> n;
	int f = 0;
	for(int i=1;i<=n;i++){
		int a; cin >> a;
		if (a == 1) f++;
	}
	if (f == n) f--;
	cout << (f & 1 ? "Bob\n" : "Alice\n");
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

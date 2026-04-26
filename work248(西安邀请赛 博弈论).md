https://www.luogu.com.cn/problem/P10558

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=1e5+10;
const int INF=1e18;
const int MOD=998244353;
//#define ll __int128


int k, z;
int x[N];
vector<int> v, u;
void solve() {
  	
	cin >> k >> z;
	for (int i = 0, a; i < k; i++)
	{
		cin >> a;
		if (a == 0)continue;
		else if (a == 1)v.push_back(i);//除了 个数为1的 A一个 B一个 剩下的都要看谁先手
		else
		{
			z += a % 2;
			u.push_back(i);
		}
	}
	reverse(v.begin(), v.end());
	z += v.size();
	for (int i = 0; i < v.size(); i++)
	{
		if (i % 2 == 0)x[v[i]] = 1;
	}
	if (z & 1)for (auto i : u)
	{
		x[i] = 1;
	}
	for (int i = k - 1; i >= 0; i--)
	{
		cout << x[i];
	}
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

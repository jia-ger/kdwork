> https://ac.nowcoder.com/acm/contest/119664/E
```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define endl '\n'
typedef pair<int,int> PII;
const int N=1e5+10;
const int INF=1e18;
const int mod=998244353;
#define ll __int128


void solve()
{
  int n;
  std::cin >> n;
  std::vector<int> P(n + 1);
  for (int i = 1; i <= n; i++) {
    std::cin >> P[i];
  }
  //预处理前后缀 l是区间左半部分 最大匹配值
  //r是区间右半部分 最大匹配值
  //左半部分找前缀 右半部分找后缀 
  std::vector<int> lsz(n + 1), rsz(n + 1);
  for (int i = 2; i < n; i++) {
    int jl = 1, jr = n;
    while (jl < i && i + lsz[i] <= n) {
      if (P[jl] == P[i + lsz[i]]) {
        lsz[i]++;
      }
      jl++;
    }
    while (jr > i && i - rsz[i] >= 1) {
      if (P[jr] == P[i - rsz[i]]) {
        rsz[i]++;
      }
      jr--;
    }
  }
  int ans = 0;
  for (int i = 2; i < n; i++) {
    for (int j = i; j < n; j++) {
      ans += lsz[i] + rsz[j] >= j - i + 1;//说明i到j的区间方案可行 
    }
  }
  std::cout << ans << '\n';
}

	signed main() {
		cin.tie(0)->sync_with_stdio(0);
		int T=1;
//		cin>>T;
		while(T--)solve();

		return 0;
	}
```

https://codeforces.com/contest/2217/problem/D


```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=2e3+10;
const int INF=1e9;
const int MOD=1e9+7;
//#define ll __int128

//通过差分数组将区间翻转操作转化为点对匹配问题
void solve() {
    itn n, k;
    cin>>n>>k;
    vector<int> a(n + 1);
    for (int i = 1; i <= n; i++) cin >> a[i];
    vector<int> p(k);
    for (int i = 0; i < k; i++) cin >> p[i];

    int x = a[p[0]];
    vector<int> b(n + 2, 0);
    for (int i = 1; i <= n; i++) {
        b[i] = a[i] ^ x;//b[i]=0 则与x相等 b[i]=1则与x不相等 需要将b[i]全变成0 
    }

    vector<int> d;//差分数组 d[i]=b[i]^b[i-1]
	//一次区间操作 翻转b[l],b[l+1]..b[r] 等于 翻转 d[l] d[r+1]
	//目标是让所有的d[i]=0 
    for (int i = 1; i <= n + 1; i++) {
        if (b[i] ^ b[i - 1]) {
            d.push_back(i);
        }
    }

    if (d.empty()) {
        cout << 0 << endl;
        return;
    }

    vector<int> cnt(k + 1, 0);//k个特殊索引 划分成k+1个区域 用0-k来表示 
    for (int pos : d) {
    
        auto it = lower_bound(p.begin(), p.end(), pos);
        int idx = distance(p.begin(), it);
        cnt[idx]++;
    }

	//同一个区域 由于没有特殊索引要用2次翻转实现  假设同一个区域数量最多的为 x 
	//  (d.size()-x)*1 + (x-(d.size()-x))/2*2  =   x   
	
	 
	//跨区域1次翻转可实现  d.size()/2 
	
	 
    int maxx = 0;
    int tot= d.size();
    for (int c : cnt) {
        maxx= max(maxx, c);
    }

    cout << max(tot/ 2, maxx) << endl;
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

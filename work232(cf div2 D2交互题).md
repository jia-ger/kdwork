https://codeforces.com/contest/2220/problem/D2


```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
typedef pair<int,int> PII;
const int N=2e3+10;
const int INF=1e9;
const int MOD=1e9+7;
//#define ll __int128


int query(vector<int> s) {
    if (s.empty()) return 0;
    cout << "? " << s.size();
    for (int x : s) cout << " " << x;
    cout << endl;
    int res;
    cin>>res;
    return res;
}

bool has(vector<int> s) {
    if (s.empty()) return false;
    int f = query(s);
    int g = s.size();
    return (g - f) % 2 != 0;// （g-f）重复出现的元素总数 奇数一定是三元组在里面
}

// log2(2001)=11 11*3=33 最多33次查询
void solve() {
    int n;
    cin>>n;
    
    int p3 = 2 * n + 1;//找到最小的R 使得[1,R] 包含三元组
    int l= 1, r = 2 * n + 1;
    while (l<= r) {
        int mid = (l + r) / 2;
        vector<int> s(mid);
        iota(s.begin(), s.end(), 1);
        if (has(s)) {
            p3 = mid;
            r = mid - 1;
        } else {
            l= mid + 1;
        }
    }

 
    int p1 = 1;//找到最大的 L 使得[L，2*n+1] 包含三元组
    l= 1, r= 2 * n + 1;
    while (l <= r) {
        int mid = (l + r) / 2;
        vector<int> s;
        for (int i = mid; i <= 2 * n + 1; i++) s.push_back(i);
        if (has(s)) {
            p1 = mid;
            l = mid + 1;
        } else {
            r = mid - 1;
        }
    }

  
    int p2 = p1 + 1;//确定了 L R  进而可以找 [L,...MID,R]
    l = p1 + 1, r = p3 - 1;
    while (l <= r) {
        int mid = (l+ r) / 2;
        vector<int> s;
        for (int i = p1; i <= mid; i++) s.push_back(i);
        s.push_back(p3);
        if (has(s)) {
            p2 = mid;
            r = mid - 1;
        } else {
            l= mid + 1;
        }
    }

    cout << "! " << p1 << " " << p2 << " " << p3 << endl;
}

signed main() {
  
    int T;
    cin>>T;
    while (T--) {
        solve();
    }
    return 0;
}

```

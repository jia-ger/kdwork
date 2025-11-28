https://ac.nowcoder.com/acm/contest/123787/C

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

// 判断马 (hx, hy) 能否攻击到位置 (tx, ty)
bool can(long long hx, long long hy, long long tx, long long ty) {
    long long dx = abs(hx - tx);
    long long dy = abs(hy - ty);
    return (dx == 1 && dy == 2) || (dx == 2 && dy == 1);
}

void solve()
{
  int x,y,n;
  cin>>x>>y>>n;
   vector<PII> ma(n);
        for (int i = 0; i < n; i++) {
            cin >> ma[i].first >> ma[i].second;
        }
 
        bool check = false;
        for (auto& h : ma) {
            if (can(h.first, h.second, x, y)) {
                check = true;
                break;
            }
        }

        int cnt= 0;
        int dx[] = {-1, -1, -1, 0, 0, 1, 1, 1};
        int dy[] = {-1, 0, 1, -1, 1, -1, 0, 1};

        for (int k = 0; k < 8; k++) {
            int nx = x + dx[k];
            itn ny = y + dy[k];

           
            bool safe = true;
            for (auto& h : ma) {
                if (can(h.first, h.second, nx, ny)) {
                    safe = false;
                    break;
                }
            }
            if (safe) {
                cnt++;
            }
        }

        // 3. 判断局面
        if (check && cnt== 0) {
            cout << "B\n";
        } else if (!check && cnt== 0) {
            cout << "A\n";
        } else {
            cout << "C\n";
        }
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   while(T--)solve();
   
    return 0;
}
```

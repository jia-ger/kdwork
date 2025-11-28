https://ac.nowcoder.com/acm/contest/123787/D

> 分析：x-a 是 x-b的倍数 设x-b=d x-a=x-b+b-a=d+(b-a)
d+(b-a)是d的倍数 说明 d是b-a的一个因数 
所以求出 b-a的所有因数 x=b+因数 只要x在范围内就符合要求

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
    int a,b,l,r;cin>>a>>b>>l>>r;
    int k=b-a;
    set<int>div;
        for (int i = 1; i * i <= k; i++) {
            if (k % i == 0) {
                div.insert(i);
                div.insert(k / i);
            }
        }

        int count = 0;
        for (itn d : div) {
            int x = b + d;
            if (l <= x && x <= r) {
                count++;
            }
        }

        cout << count << "\n";
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   while(T--)solve();
   
    return 0;
}
```

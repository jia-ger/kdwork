https://www.luogu.com.cn/problem/P12835


```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=4e5+10;
const int INF=1e7;
const int MOD=998244353;
//#define ll __int128

void solve() {
    itn a=45,b=2,n;// 9个数做开头 每个数对应5个数  9*5^(k-1) 
    cin>>n;
    while(n>a){//确定是个几位数 
        n-=a;
        b++;
        a*=5;
    }
    n--;
    a/=9;
    bool las=(n/a+1)%2;//开头奇偶 
    cout<<n/a+1;//开头的数 
    n%=a;
    for(int i=1;i<b;i++){//b-1位数 
        a/=5;
        cout<<n/a*2+1-las;
        las=!las;
        n%=a;
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

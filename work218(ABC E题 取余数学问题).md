https://atcoder.jp/contests/abc448/tasks/abc448_e

> 分析：n=t(mp)+n%(mp) (n/m)%p=((n%(mp))/m)%p
> l个c[i] 可表示成 c[i]*11111...  1111..=(10^l[i]-1)/9

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
const int INF=1e7;
const int MOD=998244353;
//#define ll __int128


itn ans;
int c[N],l[N];
int qmi(itn a,int b,int p){
	a=a%p;
	int t=1;
	while(b!=0){
		if(b&1)t=t*a%p;
		a=a*a%p;
		b>>=1;
	}
	return t;
} 
void solve() {
  int k,m;
  cin>>k>>m;
  for(int i=1;i<=k;i++)cin>>c[i]>>l[i];
  
  m*=10007;
  for(itn i=1;i<=k;i++)
  ans=(ans*qmi(10,l[i],m)%m+c[i]*((qmi(10,l[i],m*9)-1)/9)%m)%m;
  
  m/=10007;
  ans=(ans/m)%10007;
  cout<<ans;
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

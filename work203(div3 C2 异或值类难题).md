https://codeforces.com/contest/2171/problem/C2

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define endl '\n'
typedef pair<int,int> PII;
const int N=2e5+10;
const int INF=1e18;
const int mod=998244353;
#define ll __int128


void solve()
{
      itn n;
      cin>>n;
      vector<int>a(n),b(n);
      int x=0;
      for(int i=0;i<n;i++)cin>>a[i],x^=a[i];
      for(itn i=0;i<n;i++)cin>>b[i],x^=b[i];
      if(!x)
      {
      	cout<<"Tie"<<endl;return;
	  }
	  int init=0;
	  for(int i=0;i<20;i++)
	  if(x&1<<i)init=i;
	  //x二进制为0 说明a b异或值在这一项相同 为1说明异或值在这一项相反  
	  int index;
	  for(int i=0;i<n;i++)
	  {
	  	if((a[i]^b[i])&1<<init)index=i;//考虑a[i]b[i] 对所有数异或值x的最高位贡献    
	  }
      cout<<(index&1 ? "Mai" : "Ajisai")<<endl; 
}


signed main() {
	cin.tie(0)->sync_with_stdio(0);
	int T=1;
	cin>>T;

	while(T--)solve();

	return 0;
}
```

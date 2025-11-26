https://codeforces.com/contest/2157/problem/B

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
    itn n,x,y;
    cin>>n>>x>>y;
    string s;
    cin>>s;
    x=abs(x);
    y=abs(y);
    for(int i=0;i<s.size();i++)
    {
    	if(s[i]=='4')
		{
		  if(x>y)x=max(x-1,0ll);
		  else y=max(y-1,0ll);	
		} 
		else
		{
			x=max(x-1,0ll);
			y=max(y-1,0ll);
		}
	}
	cout<<(x==0&&y==0 ?"YES":"NO")<<endl;
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   while(T--)solve();
   
    return 0;
}
```

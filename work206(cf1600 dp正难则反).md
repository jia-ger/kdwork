https://codeforces.com/problemset/problem/2167/G

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
  itn n,sum=0;
  cin>>n;
  vector<int>a(n),b(n),f(n);
  for(int i=0;i<n;i++)cin>>a[i];
  for(itn i=0;i<n;i++)cin>>b[i],sum+=b[i];
  //目的是在原数组中找到一条代价最大的单调不下降子序列 那么改变其他数将花费最小 
  for(int i=0;i<n;i++)
   {
   	 f[i]=b[i];
     for(int j=0;j<i;j++) 
     if(a[j]<=a[i])f[i]=max(f[i],f[j]+b[i]);
   
   }
   cout<<sum-*max_element(f.begin(),f.end())<<endl; 
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   while(T--)solve();
   
    return 0;
}
```

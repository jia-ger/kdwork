> https://codeforces.com/problemset/problem/2061/E

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

const int M=15,K=(1ll<<31)-1;
int n,m,k,a[N],b[M],val[N],num[N][M],res[N*M],ans;

void solve()
{  
  cin>>n>>m>>k;
		for(int i=1;i<=n;i++)
		{
			cin>>a[i];
			for(int j=1;j<=m;j++)num[i][j]=1e18;
			num[i][0]=a[i];
		}
		for(int i=1;i<=m;i++)cin>>b[i];
		for(int i=0;i<(1<<m);i++)
		{
			val[i]=K;
			for(int j=1;j<=m;j++)
				if(i&(1<<(j-1)))val[i]&=b[j];
		}
		for(int i=1;i<=n;i++)
			for(int j=0;j<(1<<m);j++)
				num[i][__builtin_popcount(j)]=min(num[i][__builtin_popcount(j)],val[j]&a[i]);
               //存第i个数用了j次魔法后的最小可能 
		for(int i=1;i<=n;i++)
			for(int j=1;j<=m;j++)
				res[(i-1)*m+j]=num[i][j]-num[i][j-1];//减少了多少 肯定都是负数 减少的多的小
				
		//如果选了res[i][j] 则 res[i][j-1]肯定选了 因为 res[i][j]>=res[i][j-1]
		//因为与操作每次会使数字不变或减小 可以看作抹去2进制上的1
		//每次魔法肯定会尽可能抹去最大的1 所以变小趋势趋于平缓		 
		sort(res+1,res+n*m+1);
		ans=0;
		for(int i=1;i<=n;i++)ans+=a[i];
		for(int i=1;i<=k;i++)ans+=res[i];
		cout<<ans<<endl;
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   while(T--)solve();

    return 0;
}
```

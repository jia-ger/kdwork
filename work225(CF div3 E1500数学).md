https://codeforces.com/problemset/problem/2137/E

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=2e5+10;
const int INF=1e7;
const int MOD=1e9+7;
//#define ll __int128

int a[N],c[N];
int n,k,mex;

void bian(){
	memset(c,0,sizeof c);
	mex=0;
	for(int i=1;i<=n;i++)
	c[a[i]]++;
	
	for(int i=0;i<=n;i++){
		if(!c[i]){
			mex=i;break;
		}
	}
	
	for(int i=1;i<=n;i++){
		
	 if(a[i]>mex || c[a[i]]>1)a[i]=mex;
	}
} 
void solve() {
  cin>>n>>k;
  for(itn i=1;i<=n;i++)cin>>a[i];
  bian();
  if(k>1){
  	bian();
  	if(k&1)bian();
  }
  
  int sum=0;
  for(itn i=1;i<=n;i++)sum+=a[i];
  
  cout<<sum<<endl;
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

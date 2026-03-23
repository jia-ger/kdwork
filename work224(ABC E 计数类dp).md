https://atcoder.jp/contests/abc450/tasks/abc450_e


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

string x,y,p[100010];
char c;
int op,cnt[100010][30],len[100010],n,l,r;

int dfs(int op,int k,char c){
	if(k==0)return 0;
	if(op==1||op==2){
		int f=0;
		for(itn i=0;i<k;i++)
		if(p[op][i]==c)f++;
		
		return f;
	}
	
	if(k>=len[op])return cnt[op][c-'a'];
	if(k<=len[op-1])return dfs(op-1,k,c);
	if(k>len[op-1])return cnt[op-1][c-'a']+dfs(op-2,k-len[op-1],c);
	
}

void solve() {
   
   cin>>p[1]>>p[2];
   cin>>n;
   
   len[1]=p[1].size();
   for(itn i=0;i<len[1];i++){
		cnt[1][p[1][i]-'a']++;
	}
	len[2]=p[2].size();
	for(itn i=0;i<len[2];i++){
		cnt[2][p[2][i]-'a']++;
	}

   op=3;
   while(1){
   	len[op]=len[op-1]+len[op-2];
   	for(int i=0;i<26;i++)
   	cnt[op][i]=cnt[op-1][i]+cnt[op-2][i];
   	
   	if(len[op]>1e18)break;
   	op++;
   } 
   for(itn j=1;j<=n;j++){
   	cin>>l>>r>>c;
   	cout<<dfs(op,r,c)-dfs(op,l-1,c)<<endl;
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

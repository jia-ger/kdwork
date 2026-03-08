https://atcoder.jp/contests/abc448/tasks/abc448_f

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=6e4+10;
const int INF=1e7;
const int MOD=998244353;
//#define ll __int128

//区间分块 分块处理 优雅的暴力算法  复杂度O(n*sqrt(n)) 
//蛇形走位 奇数块向上走 偶数块向下走 
//std::rotate 算法的调用，它将序列中的元素进行循环旋转 三个参数为起始中间结尾 旋转后中间的数将放到开头 
int block;  
struct abd{
	int x,y,id;
}p[N]; 
bool cmp(abd q,abd p){
	if(q.x/block!=p.x/block){
		return q.x/block<p.x/block;
	}
	if((q.x/block)%2)return q.y<p.y;
	else return q.y>p.y;
}


void solve() {
  int n;
  cin>>n;
  block=20000000/sqrt(n); 
  for(int i=1;i<=n;i++)
  cin>>p[i].x>>p[i].y,p[i].id=i;
  
  sort(p+1,p+1+n,cmp) ;
  int pos=1;
  while (p[pos].id != 1) pos++;
  rotate(p+1,p+pos,p+1+n); 
  
  for(itn i=1;i<=n;i++)cout<<p[i].id<<" \n"[i==n]; 
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

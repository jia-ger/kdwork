https://codeforces.com/problemset/problem/2185/G

```c++
#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
const int N=2e3+10;
const int INF=1e9;
const int MOD=1e9+7;
//#define ll __int128

int n;
vector<int> a[200010];

int pmex[200010],nd[200010];
int bkt[1000010];

int mexcnt[1000010],ndsum[1000010];

int calcmex(vector<int> v){
    sort(v.begin(),v.end());
    int nowmex=0;
    for(int x:v){
        if(nowmex==x) nowmex++;
        else if(nowmex<x) break;
    }
    return nowmex;
}

void solve() {
     	cin>>n;
        for(int i=1;i<=n;i++){
            int l;cin>>l;
            a[i].resize(l);
            for(int &x:a[i]) cin>>x;
        }
          for(int p=1;p<=n;p++){
            pmex[p]=calcmex(a[p]);//计算每个数组原MEX
            a[p].push_back(pmex[p]);
            nd[p]=calcmex(a[p]);//计算每个数组添加原MEX后的新MEX
            a[p].pop_back();
        }
       
	    itn mexsum=0;//原所有数组MEX之和 
        for(int p=1;p<=n;p++){
            mexsum+=pmex[p];
            mexcnt[pmex[p]]++;//原数组 MEX个数
            ndsum[pmex[p]]+=nd[p];//原mex值一样对应的新mex之和
        } 
        
        //遍历每一个数字 
        itn ans=0;
        for(int p=1;p<=n;p++){
        	
        	//不考虑本数组
            mexcnt[pmex[p]]--;
            ndsum[pmex[p]]-=nd[p];
            
            
            for(int x:a[p]) bkt[x]++;//每个数出现了几次
            
            for(int x:a[p]){
                if(x<pmex[p]&&bkt[x]==1) mexsum-=pmex[p],mexsum+=x;

                ans+=1ll*(n-1)*mexsum;//他能放到其余（n-1）个数组中
                
                ans+=-1ll*mexcnt[x]*x+ndsum[x];//所有MEX=X的数组会发生改变

                if(x<pmex[p]&&bkt[x]==1) mexsum+=pmex[p],mexsum-=x;//复原
            }

			//复原
            mexcnt[pmex[p]]++;
            ndsum[pmex[p]]+=nd[p];
            for(int x:a[p]) bkt[x]--;
        }
        
        cout<<ans<<endl;
        
        //多组样例清空
         for(int p=1;p<=n;p++){
            a[p].clear();
            mexcnt[pmex[p]]--;
            ndsum[pmex[p]]-=nd[p];
            pmex[p]=nd[p]=0;
        }
}

signed main() {
  
  	cin.tie(0)->sync_with_stdio(0);
    int T;
    cin>>T;
    while (T--)solve();
    
    return 0;
}


```

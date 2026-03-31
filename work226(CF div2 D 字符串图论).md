https://codeforces.com/contest/2210/problem/D


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

void solve() {
    int n;
    cin>>n;
    string s,t;
    cin>>s>>t;
    auto count_adjacent_pairs = [](string &s) -> int {//是以正则为单位交换 不会改变小括号的个数 
        int m=s.size();
        int ct=0;
        for(int i=0;i<m-1;i++){
            if(s[i]=='(' and s[i+1]==')')ct++;
        }
        return ct;
    };
    auto count_outer_brackets = [](string &s) -> int {//考虑整体正则 
        int m=s.size();
        vector<int> match(m,-1);
        stack<int> indices;
        for(int i=0;i<m;i++){
            if(s[i]==')'){
                match[indices.top()]=i;
                indices.pop();
            }
            else{
                indices.push(i);
            }
        }
        int ct=0;
        int l=0,r=m-1;
        while(match[l]==r){
            l++;
            r--;
            ct++;
        }
        return ct;
    };
    if(count_adjacent_pairs(s)==count_adjacent_pairs(t) and count_outer_brackets(s)==count_outer_brackets(t)){
        cout<< count_adjacent_pairs(s) <<" "<<count_outer_brackets(s)<<endl;
	    cout<<"YES\n";
        return;
    }
    cout<<"NO\n";
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

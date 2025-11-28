https://ac.nowcoder.com/acm/contest/123787/E
> 赛后代码
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
const int MOD=998244353;
#define ll __int128

 string perms[6] = {"gcd", "gdc", "cgd", "cdg", "dgc", "dcg"};
void solve()
{
      int n;
        cin >> n;
        vector<string> grid(n);
        for (int i = 0; i < n; i++) cin >> grid[i];

        int k = (2 * n - 1) / 3;
        vector<vector<int>> dp(n, vector<int>(64, 0));

        char c = grid[0][0];
        int mask0 = 0;
        for (int idx = 0; idx < 6; idx++) 
            if (perms[idx][0] == c) 
                mask0 |= (1 << idx);
        if (mask0) dp[0][mask0] = 1;

        for (int t = 2; t <= 2*n-1; t++) {
            vector<vector<int>> new_dp(n, vector<int>(64, 0));
            int s = (t <= k) ? 0 : (t <= 2*k) ? 1 : 2;
            for (int i = 0; i < n; i++) {
                int j = t - 1 - i;
                if (j < 0 || j >= n) continue;
                char ch = grid[i][j];
                int char_mask = 0;
                for (int idx = 0; idx < 6; idx++)
                    if (perms[idx][s] == ch)
                        char_mask |= (1 << idx);

                if (j > 0) {
                    for (int m = 0; m < 64; m++) {
                        if (!dp[i][m]) continue;
                        int new_mask = m & char_mask;
                        if (new_mask)
                            new_dp[i][new_mask] = (new_dp[i][new_mask] + dp[i][m]) % MOD;
                    }
                }
        
                if (i > 0) {
                    for (int m = 0; m < 64; m++) {
                        if (!dp[i-1][m]) continue;
                        int new_mask = m & char_mask;
                        if (new_mask)
                            new_dp[i][new_mask] = (new_dp[i][new_mask] + dp[i-1][m]) % MOD;
                    }
                }
            }
            dp = move(new_dp);
        }

        int ans = 0;
        for (int m = 0; m < 64; m++) 
            ans = (ans + dp[n-1][m]) % MOD;
        cout << ans << "\n";
	 
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   
  
   while(T--)solve();
   
    return 0;
}
```
> 赛时代码,超时了 应该是开的dp开的n*n导致超时 但只有n^2复杂度 不知道为什么超时
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
const int MOD=998244353;
#define ll __int128

string perms[6] = {"gcd", "gdc", "cgd", "cdg", "dgc", "dcg"};
void solve()
{
    int n;
        cin >> n;
        vector<string> grid(n);
        for (int i = 0; i < n; i++) {
            cin >> grid[i];
        }

        int k = (2 * n - 1) / 3;

        int ans = 0;
        for (const string& p : perms) {
            char p1 = p[0], p2 = p[1], p3 = p[2];
            vector<vector<int>> dp(n, vector<int>(n, 0));
            if (grid[0][0] == p1) dp[0][0] = 1;
            else continue;
            for (int t = 2; t <= 2*n-1; t++) {
                vector<vector<int>> new_dp(n, vector<int>(n, 0));
                int s = (t <= k) ? 1 : (t <= 2*k) ? 2 : 3;
                char ch = (s == 1) ? p1 : ((s == 2) ? p2 : p3);

                for (int i = 0; i < n&&i<t; i++) {
                    int j = t - 1 - i;
                    if (j < 0 || j >= n) continue;
                    if (grid[i][j] != ch) continue;
                    if (i > 0) new_dp[i][j] = (new_dp[i][j] + dp[i-1][j]) % MOD;
                    if (j > 0) new_dp[i][j] = (new_dp[i][j] + dp[i][j-1]) % MOD;
                }
                dp = new_dp;
            }
            ans = (ans + dp[n-1][n-1]) % MOD;
        }

        cout << ans << "\n";
	 
}



signed main(){
   cin.tie(0)->sync_with_stdio(0);	 
   int T=1; 

   cin>>T;
   while(T--)solve();
   
    return 0;
}
```

https://codeforces.com/contest/2166/problem/D

```c++
#include <bits/stdc++.h>

using namespace std;

const int MAX_N = 5000;
const int MOD = 998244353;
int v[MAX_N + 1];
int f[MAX_N + 1];
int dp[MAX_N + 1];
int prod[MAX_N + 2];

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    
    cin >> t;
    while (t--) {
        int n;

        cin >> n;
        for (int i = 0; i <= n; i++)
            f[i] = 0;
        for (int i = 0; i < n; i++) {
            int a;
            cin >> a;
            f[a]++;
        }

        sort(f + 1, f + 1 + n);

        prod[n + 1] = 1;
        for (int i = n; i >= 1; i--)
            prod[i] = (long long)prod[i + 1] * max(1, f[i]) % MOD;//后缀总方案数 

        dp[0] = 1;
        for (int i = 1; i <= n; i++) 
            dp[i] = 0;

        int sol = 1;
        for (int i = 1; i <= n; i++) 
            sol = (long long)sol * max(1, f[i]) % MOD; //所有数字均出现（出现至少1次）的总方案数 

        int sum = n;//剩余未处理的数字总数 
        for (int i = 1; i <= n; i++) {
            sum -= f[i];
            if (f[i] == 0)
                continue;

            for (int s = n; s >= 0 && s >= f[i] - sum; s--)
                sol = (sol + (long long)prod[i + 1] * dp[s]) % MOD;//计算不用f[i] 
				//dp[s]表示使用前i-1种数（使用包括用0次） 组成长度为s的方案数 

            for (int s = n; s >= f[i]; s--)
                dp[s] = (dp[s] + (long long)dp[s - f[i]] * f[i]) % MOD;

        }

        cout << sol << "\n";
    }

    return 0;
}
```

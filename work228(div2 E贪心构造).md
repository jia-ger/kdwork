https://codeforces.com/contest/2217/problem/E

```c++

#include <bits/stdc++.h>
using namespace std;
#define itn int
#define icn cin
#define int long long
#define unsigned long long ull
#define endl '\n'
typedef pair<int,int> PII;
//const int N=2e3+10;
const int INF=1e9;
const int MOD=1e9+7;
//#define ll __int128

void solve() {
     	int N;
        cin >> N;

        vector<int> P(N + 1), pos(N + 1);
        for (int i = 1; i <= N; i++) {
            cin >> P[i];
            pos[P[i]] = i; // p[i]在哪 
        }

        vector<int> D(N + 1);// 位置i 符合要求的个数 
        for (int i = 1; i <= N; i++) cin >> D[i];

        vector<int> ord(N);// 排好序的下标是多少 

        bool ok = true;

        for (int val = N; val >= 1 && ok; --val) {//从大到小枚举 
            int i = pos[val];// i是数的位置 

            int m = 0;
            for (int idx : ord) if (idx > i) ++m;//最多有m个符合要求 因为前面排好序的数字均大于他 

            if (D[i] > m) {//比最多情况多直接返回-1 
                ok = false;
                break;
            }

            int needBefore = m - D[i];//需要在他前面的数字 
            int cnt = 0;
            int insertPos = 0;

            while (insertPos < (int)ord.size() && cnt < needBefore) {
                if (ord[insertPos] > i) ++cnt;
                ++insertPos;
            }

            ord.insert(ord.begin() + insertPos, i);
        }

        if (!ok) {
            cout << -1 << endl;
            return;
        }

        vector<int> A(N + 1, 0);
        for (int k = 0; k < N; k++) {
            A[ord[k]] = k + 1;
        }

        for (int i = 1; i <= N; i++) {
            cout << A[i] << " \n"[i==N];
        }
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

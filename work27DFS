> 帕秋莉将捡到的n块石头排成一排，并决定将一些石头点为黄金对于第i块石头，如果将其变为黄金，会增加ai的财富，消耗bi的魔法（需要说明的是，就算魔法值不够，也可以操作，操作后魔法值归零）
否则，帕秋莉将会回复ci的魔法，但减少di的财富（财富值同理，可以无限制减少）按照1-n的顺序以此操作每块石头，如何决策，可以使自己最后的收益值最大
只需要输出最大收益 收益值=财富值*魔法值（提示：数值不会变为负数，即任何时候，如果数值小于了0，它会立即变为0）

题解
```
#include <bits/stdc++.h>  
#define int long long  
using namespace std;  
struct node {  
    int a, b, c, d;  
} s[16];

int maxx = 0, n; 

void dfs(int x, int cai, int mo) {  
    if (x > n) { 
        maxx = max(maxx, cai * mo);   
        return;  
    }  
    dfs(x + 1, cai + s[x].a, max(mo - s[x].b, (int)0)); 
    dfs(x + 1, max(cai - s[x].d, (int)0), mo + s[x].c); 
}  //signed是因为int变成long long了但main必须返回一个int型
signed main() {  
    cin >> n;  
    for (int i = 0; i < n; i++) { // 从0开始遍历  
        cin >> s[i].a >> s[i].b >> s[i].c >> s[i].d; // 输入数据  
    }  
    dfs(0, 0, 0); // 从第0个节点开始搜索  
    cout << maxx; // 输出最大值  
    return 0;  
}
```

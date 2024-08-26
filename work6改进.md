快速幂解法
#include <stdio.h>
long long jia(long long a, long long b, long long p) {
    long long t = 1;
    a=a % p;
    while (b> 0) {
        if (b % 2 == 1) {
           t = (t*a) % p;
        }
        b = b / 2;
       a = (a * a) %p;
    }
    return t;
}

int main() {
    int n;
    scanf("%d", &n);
    for (int i = 1; i <=n; i++) {
        long long a, b, p;
        scanf("%lld %lld %lld", &a, &b, &p);
        long long t = jia(a, b, p);
        printf("%lld\n",t);//这里是英文lld代表long long
    }
    return 0;
}

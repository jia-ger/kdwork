# kdwork
super家养了一对刚出生的兔子，兔子出生第3月开始每月都会生一对小兔子，小兔子出生后同样第3月开
始也会每月生一对免子
super想知道 如果兔子不死n月后家里会有多少对兔子
设计一个程序:输入n，输出兔子数量
(2<n<30)
样例输入:7
样例输出:13
样例输入:12
样例输出:144

题解
#define _crt_secure_no_warnings 1
#include <stdio.h>
// 递归函数计算第n个月的兔子对数
 int tutu(int n) {
    if (n <= 2) {
        return 1;  
    }
    else if (n == 3) {
        return 2;  
    }
    else {
       
        return tutu(n - 1) + tutu(n - 2);
    }
}

int main() {
    int n;

    // 输入n的值
    printf("请输入n的值 (2 < n < 30): ");
    scanf_s("%d", &n);

    // 验证输入范围
    if (n <= 2 || n >= 30) {
        printf("输入值不在有效范围内！\n");
        return 1;  // 非正常退出
    }

    // 输出兔子数量
    printf("%d个月后家里会有 %d 对兔子\n", n, tutu(n));

    return 0;  // 正常退出
}

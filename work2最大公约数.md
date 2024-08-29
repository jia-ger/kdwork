输入两个整数a和 b，请你编写一个函数， int gcd(int a,int b),计算并输出a和b的最大公约数
输入格式
共一行，包含两个整数 a 和 b。
输出格式
共一行，包含一个整数，表示a和b的最大公约数。
数据范围
1 ≤ a,b≤ 1000

题解
#include <stdio.h>

// 计算最大公约数的函数
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int main() {
    int a, b;
    // 读取输入的两个整数
    scanf_s("%d %d", &a, &b);
    // 计算并输出最大公约数
    if (a >= 1&& b <= 1000)
    printf("%d\n", gcd(a, b));
    else
    printf("输入范围不符合要求\n")
    return 0;}

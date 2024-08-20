#include <stdio.h>

void printYangHuiTriangle(int n) {
    int triangle[4][4]; // 创建一个二维数组存储杨辉三角

    // 初始化杨辉三角的每一行
    for (int line = 0; line < n; line++) {
        // 每行的第一个和最后一个元素都是 1
        triangle[line][0] = 1;
        triangle[line][line] = 1;

        // 计算当前行中间的元素
        for (int j = 1; j < line; j++) {
            triangle[line][j] = triangle[line - 1][j - 1] + triangle[line - 1][j];
        }
    }

    // 打印杨辉三角
    for (int line = 0; line < n; line++) {
        // 打印空格以使三角形居中
        for (int space = 0; space < n - line - 1; space++) {
            printf(" ");
        }
        for (int j = 0; j <= line; j++) {
            printf("%d ", triangle[line][j]); // 打印当前行的元素
        }
        printf("\n"); // 换行
    }
}

int main() {
    int n;

    printf("请输入杨辉三角的行数: ");
    scanf_s("%d", &n);

    printYangHuiTriangle(n); // 调用函数生成并打印杨辉三角

    return 0;
}

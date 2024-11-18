# P1143 进制转换

正整数的通用进制转换方法如下：

1. 十转 X 进制

* 将十进制数一直除到0，余数从**低到高排列**即为所求进制数字。

2. X 转十进制

$$
\text{num} = x_1^0 + x_2^1 + x_3^2 + \cdots + x_{n-1}^n
$$

* 其中x的下标代表X进制数字的第n位数字。

----------

# P1469 找筷子

异或和的两个性质：
1. 相同的两个数异或得 0。
2. 任何数异或 0 结果是本身。

----------

# P3383 【模板】线性筛素数

欧拉筛求质数（素数）的模版如下：
```c++
bool jud[MAX + 3]; // 判断是否是质数
int arr[MAX + 3]; // 存储质数

void fun(int num) { // 求1到n范围的质数
    memset(jud, 1, sizeof(jud));
    jud[1] = 0;

    for(int i = 2; i <= num; i ++) {
        if(jud[i])  arr[++ cnt] = i;

        for(int j = 1; j <= cnt && i * arr[j] <= num; j ++) {
            jud[i * arr[j]] = 0;

            if(i % arr[j] == 0) break;
        }
    }
}
```

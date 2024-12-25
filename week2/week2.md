# P1020 导弹拦截

Q1:

求出最长不上升子序列(严格单调**不增**)

根据定义，可以通过dp来解决该问题，状态转移方程如下：

$$
dp_i = \max \{1, \max_{j < i, h(j) \geq h(i)} \{ dp_j + 1 \} \}
$$

该dp复杂度显然为$O(n^2)$, 可使用二分方法优化至$O(n \log n)$。 参考[题解](https://www.luogu.com.cn/article/yc19s69p)

Q2:

问题等价于求出总序列中不上升子序列的最小个数，可以使用贪心的思想，设当前枚举序列的第i枚导弹，当前不上升子序列的最后一位的最小值为 $g_x$，可发现若有 $g_x$ >= $h_i$ (x < i)，则 $h_i$ 可以放到当前不上升子序列中，反之则多添加一个新的不上升子序列。

----------

# P1106 删数问题

### 法一：

题目原意是n个数字中去掉k个数字，求剩下数字(**保持原来顺序**)的最小值。可以使用贪心的方法反向考虑问题：

去掉k个数字即总共保留n-k个数字，可以假设一个滑动窗口，窗口大小是剩余保留数字 $n$ ,逐位保留当前最高位的最小值，即当前窗口内的最小值。若窗口末尾滑动到数字末尾或窗口值变为0/1，结束滑动。保留下来的值即为所求。

### 法二：

正向思路的AC代码：

```c++
#include<bits/stdc++.h>
#define MAX 250
#define ll long long

using namespace std;

string s;
int k;

int main() {
    ios::sync_with_stdio(false);
    cin >> s >> k;

    while (k) {
        int p = 0;
        while (s[p] <= s[p + 1] && p < s.length()) p ++;
        s.erase(p, 1);

        k --;
    }

    while (s[0] == '0' && s.size() > 1) s.erase(0, 1);
    
    cout << s << endl;
    
    return 0;
}

```

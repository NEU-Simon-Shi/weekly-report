# P1048 采药

### 01背包板子

转移方程（滚动数组）：

$$
f_j = \max(f_j, f_{j-w_i} + v_i)
$$

```c++
#include <iostream>
using namespace std;
const int maxn = 1e4 + 5;
const int maxW = 1e7 + 5;
int n, W, w[maxn], v[maxn];
long long f[maxW];

int main() {
    cin >> W >> n;
    for (int i = 1; i <= n; i++) cin >> w[i] >> v[i];
    for (int i = 1; i <= n; i++)
    for (int l = w[i]; l <= W; l++)
    if (f[l - w[i]] + v[i] > f[l]) f[l] = f[l - w[i]] + v[i]; ∕∕核心状态方程
    cout << f[W];

    return 0;
}
```

**补充**：

### 完全背包板子

转移方程：

$$
f_{i,j} = \max(f_{i-1,j}, f_{i,j-w_i} + v_i)
$$

### 多重背包板子

转移方程：

$$
f_{i,j} = \max_{k=0}^{k_i} \left( f_{i-1, j-k \times w_i} + v_i \times k \right)
$$

----------

# P1833 樱花

### 混合背包板子

伪代码：
```
for (循环物品种类) {
    if (01背包) 套用01背包代码;

    else if (完全背包) 套用完全背包代码;
    
    else if (多重背包) 套用多重背包代码;
}
```

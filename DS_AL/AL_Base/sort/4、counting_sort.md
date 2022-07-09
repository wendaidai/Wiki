# 计数排序
## 简介
算法原理：
- 使用一个额外的数组 $C$，其中第 $i$ 个元素是待排序数组 $A$ 中值等于 $i$ 的元素个数，然后根据数组 $C$ 来将 $A$ 排序。
- 算法分为三个步骤
  - 计算每个数出现了几次
  - 求出每个数出现次数的前缀和
  - 利用出现次数的前缀和，从右至左计算每个数的排名。

稳定性：
- 计数排序是一种稳定算法

时间复杂度
- 计数排序时间复杂度为 $O(n+)$，其中 $w$ 代表待排序数组的值域大小

伪代码：
![](\images/4.png)

## 代码实现
c++
```cpp
const int N = 1010;
const int W = 1010;

int* counting_sort(int q[], int n){
    int cnt[W];
    int* res = new int[N];
    memset(cnt, 0, sizeof(cnt));
    for (int i = 0; i < n; i++)
        cnt[q[i]]++;
    for (int i = 1; i < W; i++)
        cnt[i] += cnt[i - 1];
    for (int i = n - 1; i >= 0; i--)
        res[--cnt[q[i]]] = q[i];
    return res;
}
```

python
```python
N = W = 1010
def counting_sort(q):
    res = [0] * N
    cnt = [0] * W
    for i in range(len(q)):
        cnt[q[i]] += 1
    for i in range(0, W):
        cnt[i] += cnt[i - 1]
    for i in range(len(q) - 1, -1, -1):
        res[cnt[q[i]] - 1] = q[i]
        cnt[q[i]] -= 1
    return res
```
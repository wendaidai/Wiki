# 快速排序
## 简介
算法原理;
- 通过 **分治** 的方法进行排序
- 算法步骤
  - 将数列划分成两部分（要求保证大小相对关系）
  - 递归到两个子序列中分别进行快速排序
  - 不用合并，此时数组完全有序

稳定性：
- 由于 `swap` 操作的存在，快速排序算法不稳定

时间复杂度
- 快排最优时间复杂度和平均时间复杂度为 $O(n\log n)$，最坏时间复杂度为 $O(n^{2})$

## 代码实现
c++
```cpp
void quick_sort(int q[], int l, int r){
    if (l >= r) return;

    int i = l-1, j = r+1;
    int temp = q[l+r >> 1];

    while (i < j){
        do i++; while(q[i] < temp);
        do j--; while(q[j] > temp);
        if(i < j) swap(q[i], q[j]);
    }

    quick_sort(q,l,j);
    quick_sort(q,j+1,r);
}
```

python
```python
def quick_sort(q, l, r):
    if l >= r :
        return
    i = l - 1
    j = r + 1
    temp = q[l+r >> 1]
    while (i < j):
        i += 1
        while (q[i] < temp):
            i += 1
        j -= 1
        while (q[j] > temp):
            j -= 1
        if (i < j):
            q[i], q[j] = q[j], q[i]
    quick_sort(q, l, j)
    quick_sort(q, j + 1, r)
```

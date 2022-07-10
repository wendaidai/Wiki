# 归并排序
## 简介
算法原理：
- 归并排序采用 **分治** 的思想对数组进行排序
- 算法步骤：
  - 将数组划分成两个部分
  - 递归地分别对两个子序列进行归并排序
  - 合并两个子序列

稳定性：
- 归并排序是稳定的

时间复杂度：
- 最优、最坏和平均时间复杂度均为 $O(n\log n)$

空间复杂度为 $O(n)$

伪代码：
![](\images/6.png)

## 代码实现
c++
```cpp
void merge_sort(int q[], int l, int r){
    int tmp[N];
    if (l >= r) return;
    int mid = l+r >> 1;
    
    merge_sort(q, l, mid);
    merge_sort(q, mid+1, r);

    int i = l, j = mid+1, k = l;
    while (i <= mid && j <= r){
        if (q[i] < q[j]) 
            tmp[k++] = q[i++];
        else 
            tmp[k++] = q[j++];
    }

    while (i <= mid) tmp[k++] = q[i++];
    while (j <= r) tmp[k++] = q[j++];

    for (i = l; i <= r; i++) q[i] = tmp[i];
}
```

python
```python
def merge_sort(q, l, r):
    tmp = []
    if l >= r:
        return
    mid = (l + r) >> 1
    merge_sort(q, l, mid)
    merge_sort(q, mid + 1, r)

    i = l
    j = mid + 1
    while i <= mid and j <= r:
        if q[i] < q[j]:
            tmp.append(q[i])
            i += 1
        else:
            tmp.append(q[j])
            j += 1
    
    while i <= mid:
        tmp.append(q[i])
        i += 1
    while j <= r:
        tmp.append(q[j])
        j += 1

    for i in range(l, r + 1):
        q[i] = tmp[i - l]
```

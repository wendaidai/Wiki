# 选择排序
## 简介
算法原理：
- 每次找出第 $i$ 小的元素（即 $A_{i,\cdots ,n}$ 中最小元素），然后将这个元素与数组中第 $i$ 个位置上的元素交换位置

稳定性：
- 由于 swap 操作的存在，选择排序是一种不稳定的排序算法

时间复杂度：
- 最优、平均、最坏时间复杂度均为 $O(n^{2})$

伪代码
![](\images/1.png)

## 代码实现
C++
```cpp
void select_sort(int q[],int n){
    int k,i,j;
    for(i = 0; i < n-1; i++){
        //再[i,n-1]中选取最小元素
        for(k = i, j = i + 1; j < n; j++)
            if(q[k] > q[j]) k = j;
        if(k != i) swap(q[k],q[i]);
    }
}
```

python
```python
def selection_sort(q):
    q.copy();
    for i in range(len(q)):
        min_index = i
        for j in range(i+1, len(q)):
            if q[j] < q[min_index]:
                min_index = j
        q[i], q[min_index] = q[min_index], q[i]
    return q
```
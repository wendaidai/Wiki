# 插入排序
## 简介
算法原理：
- 将待排列元素划分为“已排序”和“未排序”两部分，每次从“未排序的”元素中选择一个插入到“已排序的”元素中的正确位置。

稳定性
- 插入排序是一种稳定的算法

时间复杂度
- 最优时间复杂度为 $O(n)$，在数列几乎有序时效率很高
- 最坏和平均时间复杂度均为 $O(n^{2})$

伪代码;
![](\images/3.png)

## 代码实现
c++
```cpp
void insertion_sort(int q[], int n){
    int temp;
    for (int i = 1; i < n; i++) {
        temp = q[i];
        int j = i-1;
        while (temp < q[j] && j >= 0) {
            q[j+1] = q[j];
            j--;
        }
        q[j+1] = temp; 
    }
}
```

python
```python
def selection_sort(q):
    for i in range(1, len(q)):
        temp = q[i]
        j = i - 1
        while j >= 0 and q[j] > temp:
            q[j + 1] = q[j]
            j -= 1
        q[j + 1] = temp
    return q
```

## 改进
在寻找插入位置时使用二分查找
c++
```cpp
// 注意边界问题
void binary_insert_sort(int q[],int n){
    int left, right, mid;
    int temp;
    for(int i = 1; i < n; i++){
        temp = q[i];
        left = 0; right = i-1;
        while(left <= right){
            mid = left+right >> 1;
            if(temp < q[mid]) right = mid - 1;
            else left = mid + 1;
        }
        // 后移
        for(int k = i-1; k >= left; k--)
            q[k+1] = q[k];
        q[left] = temp; //插入
    }
}
```

python
```python
def binary_selection_sort(q):
    for i in range(1, len(q)):
        temp = q[i]
        left = 0
        right = i - 1
        while left <= right:
            mid = (left + right) // 2
            if q[mid] > temp:
                right = mid - 1
            else:
                left = mid + 1
        for j in range(i, left, -1):
            q[j] = q[j - 1]
        q[left] = temp
    return q
```
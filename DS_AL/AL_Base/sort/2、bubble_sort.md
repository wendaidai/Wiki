# 冒泡排序
## 简介
算法原理:
- 每次检查相邻两个元素，如果前面的元素与后面的元素满足给定的排序条件，就将相邻两个元素交换。当没有相邻的元素需要交换时，排序就完成了。
- 经过 $i$ 次扫描后，数列的末尾 $i$ 项必然是最大的 $i$ 项，因此冒泡排序最多需要扫描 $n-1$ 遍数组就能完成排序。

稳定性：
- 冒泡排序是一种稳定的算法

时间复杂度:
- 原序列完全有序时，只需进行一次遍历，不用进行任何交换操作，时间复杂度为 $O(n)$
- 最坏情况下，冒泡排序需进行 $\displaystyle \frac{n(n-1)}{2}$ 次交换操作，时间复杂度为 $O(n^{2})$
- 平均时间复杂度为 $O(n^{2})$

伪代码：
![](\images/2.png)

## 代码实现;
C++
```cpp
void bubble_sort(int q[], int n){
    int flag = 1;
    while (flag) {
        flag = 0;
        for (int i = 0; i < n - 1; i++) {
            if (q[i] > q[i + 1]) {
                swap(q[i], q[i + 1]);
                flag = 1;
            }
        }
    }
}
```
其中 `flag` 的作用是在每次交换操作后，判断是否需要进行下一轮的交换操作。避免之后不必要的循环。

python
```python
def bubble_sort(q):
    flag = True
    while flag:
        flag = False
        for i in range(len(q) - 1):
            if q[i] > q[i + 1]:
                q[i], q[i + 1] = q[i + 1], q[i]
                flag = True
    return 
```
# 前缀和、差分
## 前缀和
简单理解为 “数组前 $n$ 项的和”
一维数组前缀和：
c++
```cpp
int* partial_sum(int q[], int n){
    int* sum = new int[n];
    memset(sum, 0, sizeof(int)*n);
    sum[0] = q[0];
    for (int i = 1; i < n; i++)
        sum[i] = sum[i-1] + q[i];
    return sum;
}
```
python
```python
def partial_sum(q):
    """
    :param q: list of numbers
    :return: list of partial sums
    """
    p = [0]
    p[0] = q[0]
    for i in range(1, len(q)):
        p.append(q[i] + p[i-1])
    return p
```

二维前缀和：基于容斥原理求解
c++
```cpp
int** twoD_PartialSum(int** q, int n, int m){
    int** sum = new int*[n];
    for (int i = 1; i <= n; i++){
        sum[i] = new int[m];
        memset(sum[i], 0, sizeof(int)*m);
    }

    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++)
            sum[i][j] = sum[i - 1][j] + sum[i][j-1] - sum[i-1][j-1] + q[i][j];
    
    return sum;
}
```
python
```python
def twoD_PartialSum(q):
    """
    :param q: list of lists of numbers
    :return: list of lists of partial sums
    """
    p = [[0] * len(q[0]) for _ in range(len(q))]
    p[0][0] = q[0][0]
    for i in range(1, len(q)):
        p[i][0] = p[i-1][0] + q[i][0]
    for j in range(1, len(q[0])):
        p[0][j] = p[0][j-1] + q[0][j]
    for i in range(1, len(q)):
        for j in range(1, len(q[0])):
            p[i][j] = p[i-1][j] + p[i][j-1] - p[i-1][j-1] + q[i][j]
    return p
```
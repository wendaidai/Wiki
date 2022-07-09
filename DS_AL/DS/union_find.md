# 并查集

并查集主要用于解决 **元素分组** 的问题，管理一系列 **不相交的集合**，并支持两种操作：

- **合并（union）**：把两个不相交的集合合并成一个集合
- **查找（find）**：查询两个元素是否在同一个集合中

## 初始化

规定当数组 `fa[i] = i` 时表示该元素为祖先

c++

```cpp
void initSet(int size) {
    for (int i = 0; i < size; i++)
        fa[i] = i;
    return;
}
```

Python

```python
def initSet(size):
    for i in range(0, size):
        fa[i] = i
    return
```

## 查找

查找一个元素的祖先

c++

```cpp
int fa[MAXN];

// 递归版本
int find(int x) {
    if (fa[x] == x)
        return x;
    else
        return find(fa[x]);
}

// 非递归版本
int find(int x) {
    while (x != fa[x])
        x = fa[x];
    return x;
}
```

Python

```python
fa = [0] * MAXN

# 递归
def find(x):
    if fa[x] == x:
        return x
    else:
        return find(fa[x])
    
# 非递归
def find(x):
    while x != fa[x]:
        x = fa[x]
    return x
```

### 路径压缩

查找时一层一层寻找效率较低，可以 **将路径上的每个节点都直接连接到根上**，这样在之后的每次查找都只要查找一次即可

![image-20220702215355742](https://s2.loli.net/2022/07/02/yBk5opF3w2cIJtD.png)

c++

```cpp
int find(int x){
    if (x != fa[x])
        fa[x] = find(fa[x]);
    return fa[x];
}
```

Python

```python
def find(x):
    if x != fa[x]:
        fa[x] = find(fa[x])
    return fa[x]
```

## 合并

在进行合并操作时，不用在意合并之后的祖先是谁，只要其中一个祖先变成另一个祖先的儿子就行

![image-20220702215814249](https://s2.loli.net/2022/07/02/UVqAp8rk7oH2jXv.png)

c++

```cpp
void union(int x, int y) {
    x = find(x);
    y = find(y);
    fa[x] = y;
}
```

Python

```python
def union(x, y):
    x = find(x)
    y = find(y)
    fa[x] 
```


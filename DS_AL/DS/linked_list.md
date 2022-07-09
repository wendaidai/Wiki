# 链表

链表是一种存储数据的线性数据结构，一般通过指针来连接元素。

该数据结构便于数据的插入和删除操作，但寻找与读取数据效果性能较差

## 与数组的区别

两者因不同的存储结构各有优势

- 链表因其链状的结构，对于插入和删除操作的时间复杂度为 $O(1)$。但寻找和读取元素的操作效率较差，随访问元素的复杂度为 $O(n)$.
- 数组对于随机访问元素效果较好，复杂度为 $O(1)$。但删除和插入的复杂度为 $O(n)$。

## 构建链表

### 单向链表

如下图所示，单向链表的每个节点包含数据域和指针域，数据域用于存放数据，指针域通过指向下一节点来连接两个节点

![image-20220702172648580](https://s2.loli.net/2022/07/02/PXe5pjnRVcDxCrF.png)

c++

```cpp
struct Node {
    int value;
    Node *next;
};
```

Python

```python
class Node:
    def __init__(self, value = None, next = None): 
        self.value = value
        self.next = next
```

### 双向链表

如下图所示，双向链表也有数据域和指针域，但指针域有两个，由于连接上一个节点和下一个节点

![image-20220702174409664](https://s2.loli.net/2022/07/02/wnA1ECN9kaQMI3t.png)

c++

```cpp
struct Node {
    int value;
    Node *left;
    Node *right;
};
```

Python

```python
class Node:
    def __init__(self, value = None, left = None, right = None): 
        self.value = value
        self.left = left
        self.right = right
```

## 向链表中插入数据

### 单向链表

向原节点 `p` 插入新节点 ，流程大致如下：

1. 初始化待插入数据的节点 `node`
2. 将 `node` 的 `next` 指针指向 `p` 的下一个节点
3. 将 `p` 的 `next` 指针指向 `node`

c++

```cpp
void insertNode(int i, Node *p) {
    Node *node = new Node;
    node->value = i;
    node->next = p->next;
    p->next = node;
}
```

Python

```python
def insertNode(i, p):
    node = Node()
    node.value = i
    node.next = p.next
    p.next = node
```

### 单向循环链表

单向循环链表：将链表的头和尾连接起来就是循环链表，对于循环链表，在插入数据时需要判断原链表是否为空：为空则自身循环，不为空则正常插入。

1. 初始化待插入数据的节点 `node`

2. 判断给定链表 `p` 是否为空
   1. 若为空，则将 `node` 的 `next` 指针和 `p` 都指向自己
   2. 否则，将 `node` 的 `next` 指针指向 `p` 的下一个节点

3. 将 `p` 的 `next` 指针指向 `node`

c++

```cpp
void insertNode(int i, Node *p) {
    Node *node = new Node;
    node->value = i;
    node->next = NULL;
    if (p == NULL) {
        p = node;
        node->next = node;
    } else {
        node->next = p->next;
        p->next = node;
    }
}
```

Python

```python
def insertNode(i, p):
    node = Node();
    node.value = i;
    node.next = null;
    if p == None:
        p = node
        node.next = node
    else:
        node.next = p.next
        p.next = node
```

### 双向循环链表

在向双向循环链表中插入数据时，除了要判断给定链表是否为空外，还要同时修改左、右两个指针

1. 初始化待插入数据的节点 `node`
2. 判断给定链表 `p` 是否为空
   1. 若为空，则将 `node` 的 `left` 和 `right` 指针、以及 `p` 指针都指向自己
   2. 否则，将 `node` 的 `left` 指针指向 `p`

3. 将 `node` 的 `right` 指针指向 `p` 的右节点
4. 将 `p` 的右节点的 `left` 指针指向 `node`
5. 将 `p` 的 `right` 指针指向 `node`

c++

```cpp
void insertNode(int i, Node *p) {
    Node *node = new Node;
    node->value = i;
    if (p == NULL) {
        p = node;
        node->left = node;
        node->right = node;
    } else {
        node->left = p;
        node->right = p->right;
        p->right->left = node;
        p->right = node;
    }
}
```

Python

```python
def insertNode(i, p):
    node = Node()
    node.value = i
    if p == None:
        p = node
        node.left = node
        node.right = node
    else:
        node.left = p
        node.right = p.right
        p.right.left = node
        p.right = node
```

## 从链表中删除数据

### 单向（循环）链表

设待删除的节点为 `p`，从链表删除 `p` 时，将 `p` 的下一个节点 `p->next` 覆盖给 `p` 后即可，同时更新 `p` 的下下个节点

1. 将 `p` 下一个结点的值赋给 `p`，以抹掉 `p->value`；
2. 新建一个临时结点 `t` 存放 `p->next` 的地址；
3. 将 `p` 的 `next` 指针指向 `p` 的下下个结点，以抹掉 `p->next`；
4. 删除 `t`。此时虽然原结点 `p` 的地址还在使用，删除的是原结点 `p->next` 的地址，但 `p` 的数据被 `p->next` 覆盖，`p` 名存实亡。

c++

```cpp
void deleteNode(Node *p) {
    p->value = p->next->value;
    Node *t = p->next;
    p->next = p->next->next;
    delete t;
}
```

Python

```python
def deleteNode(p):
    p.value = p.next.value
    p.next = p.next.next
```

### 双向循环链表

1. 将 `p` 左结点的右指针指向 `p` 的右节点；
2. 将 `p` 右结点的左指针指向 `p` 的左节点；
3. 新建一个临时结点 `t` 存放 `p` 的地址；
4. 将 `p` 的右节点地址赋给 `p`，以避免 `p` 变成悬垂指针；
5. 删除 `t`。

c++

```cpp
void deleteNode(Node *&p) {
    p->left->right = p->right;
    p->right->left = p->left;
    Node *t = p;
    p = p->right;
    delete t;
}
```

Python

```python
def deleteNode(p):
    p.left.right = p.right
    p.right.left = p.left
    p = p.right
```
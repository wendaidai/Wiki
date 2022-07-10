# 栈
栈为一个后进先出的线性数据结构，为 *LIFO* 表

## C++
`c++` 中的 `STL` 提供了容器 `std:stack` ，使用前引入头文件 `<stack>`.
常用操作：
- 访问元素：
  - `top()`：返回栈顶元素
- 修改：
  - `push()`：将传入的参数插入栈顶
  - `pop()`：弹出栈顶元素
- 容量：
  - `empty()`：判断栈是否为空
  - `size()`：返回元素数量

# python
`Python` 中可以使用列表模拟栈
```python
st = [2,4,9]

# append() 模拟入栈操作
st.append(1)
st.append(2)
# st
# [2, 4, 9, 1, 2]

# pop() 模拟出栈操作
st.pop()
# st
# [2, 4, 9, 1]

# clear() 清空栈
st.clear()
```

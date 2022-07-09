

# 哈希表

哈希表又称散列表，是一种以 *key-value* 形式存储的数据结构

## 哈希函数

一个根据键值计算索引的函数，需要根据具体情况设计合适的哈希函数，哈希函数应当易于计算，并且使得计算出来的索引均匀分布

在 *OI* 中最常见的情况是键值为整数的情况，当键值范围较大时，一般把键值 **模** 一个较大的 **质数** 作为索引，即取 $f(x) = x\ mod\ M$ 作为哈希函数。另一种比较常见的情况是 *key* 为字符串的情况，一般不把字符串作为键值，而是先计算出字符串的哈希值，再把其哈希值作为键值插入到哈希表里

## 冲突

在实际计算时候，往往会出现两个不同的键值通过哈希函数计算出来的索引是相同的，这时候需要使用一些方法来处理冲突，可以使用拉链法和闭散列法处理冲突

## 拉链法

拉链法也称开散列法（*open hashing*）

拉链法是在每个存放数据的地方开一个链表，如果有多个键值索引到同一个地方，只用把他们都放到那个位置的链表里就行了。查询的时候需要把对应位置的链表整个扫一遍，对其中的每个数据比较其键值与查询的键值是否一致。如果索引的范围是 $1 \cdots M$，哈希表的大小为 $N$，那么一次插入/查询需要进行期望 $O(\frac{N}{M})$ 次比较。

以下模板中，*hash* 函数是针对键值的类型设计的，并且返回一个链表头指针用于查询。在这个模板中我们写了一个键值对类型为 `(long long, int)` 的 hash 表，并且在查询不存在的键值时返回 -1。函数 `hash_map()` 用于在定义时初始化。

```cpp
struct hash_map {  // 哈希表模板

    struct data {
        long long u;
        int v, nex;
    };  // 前向星结构

    data e[SZ << 1];  // SZ 是 const int 表示大小
    int h[SZ], cnt;

    int hash(long long u) { return u % SZ; }

    int& operator[](long long u) {
        int hu = hash(u);  // 获取头指针
        for (int i = h[hu]; i; i = e[i].nex)
            if (e[i].u == u) return e[i].v;
        return e[++cnt] = (data){u, -1, h[hu]}, h[hu] = cnt, e[cnt].v;
    }

    hash_map() {
        cnt = 0;
        memset(h, 0, sizeof(h));
    }
};
```

## 闭散列法

闭散列法是将所有记录直接存储在散列表中，如果发生冲突，就根据某种方法继续进行探查。比如线性探查法：如果在 `d` 处发生冲突，就依次检查 `d + 1`，`d + 2`……

```cpp
const int N = 360007;  // N 是最大可以存储的元素数量

class Hash {
    private:
    int keys[N];
    int values[N];

    public:
    Hash() { memset(values, 0, sizeof(values)); }

    int& operator[](int n) {
        // 返回一个指向对应 Hash[Key] 的引用
        // 修改成不为 0 的值 0 时候视为空
        int idx = (n % N + N) % N, cnt = 1;
        while (keys[idx] != n && values[idx] != 0) {
            idx = (idx + cnt * cnt) % N;
            cnt += 1;
        }
        keys[idx] = n;
        return values[idx];
    }
};
```


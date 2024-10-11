# 问题描述

众所周知，每两周的周三是字节跳动的活动日。作为活动组织者的小 A，在这次活动日上布置了一棵 Bytedance Tree。

Bytedance Tree 由 n 个结点构成，每个结点的编号分别为 1，2，3......n，有 n - 1 条边将它们连接起来，根结点为 1。而且为了观赏性，小 A 给 M 个结点挂上了 K 种礼物（0 ≤  K ≤  M  ≤  N， 且保证一个结点只有一个礼物)。

现在小 A 希望将 Bytedance Tree 划分为 K 个 Special 连通分块，送给参加活动日活动的同学们，请问热心肠的你能帮帮他，告诉小 A 一共有多少种划分方式吗？

一个 Special 连通分块应该具有以下特性：
- Special 连通分块里只有一种礼物（该种类礼物的数量不限）
- Special 连通分块可以包含任意数量的未挂上礼物的结点

由于方案数可能过大，对结果取模 998244353

## 输入格式

第一行输入两个整数 n 和 k，分别表示 n 个结点和 k 种装饰品。

接下来一行，输入 n 个整数 a0, a1,...an，表示第 i 个结点挂着的礼物种类为 ai（0 表示没有挂礼物）

接下来 n - 1 行，输入两个整数 u 和 v，分别表示结点 u 和结点 v 之间有一条边。

## 输出格式

一行

输出方案数即可

## 数据范围

2 ≤ n ≤ 1000000（1e6）

2 ≤ k ≤ n

**样例 1**

**INPUT**

7 3

1 0 0 0 0 2 3 

1 7

3 7

2 1

3 5

5 6

6 4

**OUTPUT**

3

**样例 2**

**INPUT**

5 2

1 0 1 0 2

1 2

1 5

2 4

3 5

**OUTPUT**

0

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <vector>

int solution(int nodes, int decorations, std::vector<std::vector<int>> tree) {
    // Please write your code here
    return -2;
}

int main() {
    //  You can add more test cases here
    std::vector<std::vector<int>> testTree1 = {{1,0,0,0,2,3}, {1,7}, {3,7}, {2,1}, {3,5}, {5,6}, {6,4}};
    std::vector<std::vector<int>> testTree2 = {{1,0,1,0,2}, {1,2}, {1,5}, {2,4}, {3,5}};

    std::cout << (solution(7, 3, testTree1) == 3) << std::endl;
    std::cout << (solution(5, 2, testTree2) == 0) << std::endl;
    return 0;
}
```

```js
function solution(nodes, decorations, tree) {
  // Please write your code here
  return -2;
}

function main() {
  //  You can add more test cases here
  const testTree1 = [[1,0,0,0,2,3],[1,7],[3,7],[2,1],[3,5],[5,6],[6,4]];
  const testTree2 = [[1,0,1,0,2],[1,2],[1,5],[2,4],[3,5]];

  console.log(solution(7, 3, testTree1) === 3);
  console.log(solution(5, 2, testTree2) === 0);
}

main();
```
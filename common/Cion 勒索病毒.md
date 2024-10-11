# 问题描述

Cion 病毒入侵了 X 公司的数据库，将硬盘数据全部加密了，而解锁这些数据需要花费 Cion 币，因此你需要尽可能多地获取 Cion 币。每次加密完一份数据，Cion 病毒会留下一个 01 组成的字符串，你可以对这些字符串 s 进行任意次数以下三种操作：
1. 使用 0 替换子串 00 并获得 a 枚 Cion 币。
2. 使用 1 替换子串 11 并获得 b 枚 Cion 币。
3. 从任意位置删除 0 并支付 c 枚 Cion 币。

Cion 为了加大解锁难度，要求连续两次操作的编号奇偶性不能相同。

为了赶紧修复数据，公司同意你向银行暂时借用任意枚 Cion 币，但结束时必须归还。操作按上面给出的顺序用整数 1 - 3 编号。请计算出你可以获得的最大 Cion 币是多少。

## 输入格式

第一行输入 4 个整数 n, a, b, c (1 ≤n≤ 10^5, 1≤ a,b,c ≤10^5).

第二行输入一个长度为 n，由 01 组成的字符串 s

保证所有测试用例的 n 的总和不超过 2*10^5

## 输出格式

每个测试用例输出一个整数表示你可以获得的最大 Cion 币是多少

**输入样例 1**

5 2 2 1

01101

**输出样例 1**

3

**输入样例 2**

6 4 3 5

110001

**输出样例 2**

11

**输入样例 3**

6 3 2 1

011110

**输出样例 3**

4

在第一个 Case 中，操作的最佳序列是 01101 -> 0101 -> 011 -> 01，操作顺序为 2, 3, 2，利润为 3。

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <string>

int solution(int n, int a, int b, int c, std::string s) {
    // Please write your code here
    return -2;
}

int main() {
    //  You can add more test cases here
    std::cout << (solution(5, 2, 2, 1, "01101") == 3) << std::endl;
    std::cout << (solution(6, 4, 3, 5, "110001") == 11) << std::endl;
    std::cout << (solution(6, 3, 2, 1, "011110") == 4) << std::endl;
    return 0;
}
```

```js
function solution(n, a, b, c, s) {
  // Please write your code here
  return -2;
}

function main() {
  //  You can add more test cases here
  console.log(solution(5, 2, 2, 1, "01101") === 3);
  console.log(solution(6, 4, 3, 5, "110001") === 11);
  console.log(solution(6, 3, 2, 1, "011110") === 4);
}

main();
```
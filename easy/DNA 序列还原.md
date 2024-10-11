# 问题描述

给定一段受损的 DNA 碱基序列 dna1，在每次只操作一个碱基的情况下，将其以最少的操作步骤将其还原到未受损的 DNA 碱基序列 dna2。

只可以对 DNA 碱基序列中的一个碱基进行三种操作：
1. 增加一个碱基
2. 去除一个碱基
3. 替换一个碱基

## 输入描述:

输入两段 DNA 碱基序列，每段分一行输入

第一行为第一段受损的 DNA 碱基序列 dna1

第二行为第二段未受损的 DNA 碱基序列 dna2

## 输出描述:

最小操作步骤数

**备注**:

0 <= dna1.length, dna2.length <= 500

dna1 和 dna2 由大写英文字母 A、G、C、T 组成

**示例 1**

**输入**

AGCTTAGC

AGCTAGCT

**输出**

2

**说明**

AGCTTAGC -> AGCTAGC（删除 T）

AGCTAGC -> AGCTAGCT（增加 T）


**示例 2**

**输入**

AGCCGAGC

GCTAGCT

**输出**

4

**说明**

AGCCGAGC -> GCCGAGC（删除 A）

GCCGAGC -> GCTGAGC（将 C 替换为 T）

GCTGAGC -> GCTAGC（删除 G）

GCTAGC -> GCTAGCT（增加 T）

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <string>

int solution(std::string dna1, std::string dna2) {
    // Please write your code here
    return -2;
}

int main() {
    //  You can add more test cases here
    std::cout << (solution("AGCTTAGC", "AGCTAGCT") == 2) << std::endl;
    std::cout << (solution("AGCCGAGC", "GCTAGCT") == 4) << std::endl;
    return 0;
}
```

```js
function solution(dna1, dna2) {
  // Please write your code here
  return -2;
}

function main() {
  //  You can add more test cases here
  console.log(solution("AGCTTAGC", "AGCTAGCT") === 2);
  console.log(solution("AGCCGAGC", "GCTAGCT") === 4);
}

main();
```
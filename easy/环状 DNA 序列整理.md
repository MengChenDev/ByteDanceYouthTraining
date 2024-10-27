# 问题描述

环状 DNA 又称超螺旋，即一段碱基序列呈现环状，在分析时，需要将相同序列的环状 DNA 分到相同组内，现需将环状碱基序列按照最小表示法进行排序。

一段长度为 `n` 的碱基序列，按照顺时针方向，碱基序列可以从任意位置起开始该序列顺序，因此长度为 `n` 的碱基序列有 `n` 种表示法。例如：长度为 6 的碱基序列 `CGAGTC`，有 `CGAGTC`、`GAGTCC`、`AGTCCG` 等表示法。在这些表示法中，字典序最小的称为“最小表示”。

输入一个长度为 `n`（`n <= 100`）的环状碱基序列（只包含 `A`、`C`、`G`、`T` 这 4 种碱基）的一种表示法，输出该环状碱基序列的最小表示。

例如：
`ATCA` 的最小表示是 `AATC`
`CGAGTC` 的最小表示是 `AGTCCG`

## 输入描述

一段 DNA 碱基序列

## 输出描述

DNA 碱基序列的最小表示

**备注**：
`n <= 100`
DNA 由大写英文字母 `A`、`G`、`C`、`T` 组成

**示例 1**
输入：`ATCA`
输出：`AATC`

**示例 2**
输入：`CGAGTC`
输出：`AGTCCG`

# 解答

 ## 思路

对于这个问题，我们的目标是找到给定环状碱基序列的最小表示。

首先，理解问题就是要明确我们需要从给定序列的各种旋转表示中找出字典序最小的那个。

数据结构方面，我们主要就是利用字符串来处理碱基序列。

算法步骤如下：
1. 先获取给定序列的长度 `n` 。
2. 初始化一个变量 `minDNA` 为原始序列，用于存储最小表示。
3. 然后通过一个循环，从位置 1 到 `n - 1` ，生成每个位置的旋转表示。
4. 在每次生成新的旋转表示后，与当前的 `minDNA` 进行比较，如果新的表示字典序更小，就更新 `minDNA` 。
5. 最后返回 `minDNA` 作为结果。

在您提供的代码中，已经很好地实现了通过循环生成旋转表示并比较的核心思路。接下来您可以思考如何优化比较的过程，或者添加一些错误处理的代码，以应对可能的异常输入。您觉得怎么样？ 

## 代码

```cpp
#include <iostream>
#include <string>

std::string solution(std::string dna_sequence) {
   int  n = dna_sequence.size();
    std::string s;
    s = dna_sequence;
    std::string t;
    t = dna_sequence;
    for (int i = 0;i < n;i++)
    {
        char r = t[0];
        t = t.substr(1, n - 1);
        
        t = t + r;
        //std::cout << t << ' ';
        if (s.compare(t) > 0)
        {
            s = t;
        }

    }
    //std::cout << s << std::endl;
    return s;
}

int main() {
    // You can add more test cases here
    std::cout << (solution("ATCA") == "AATC") << std::endl;
    std::cout << (solution("CGAGTC") == "AGTCCG") << std::endl;
    std::cout << (solution("TCATGGAGTGCTCCTGGAGGCTGAGTCCATCTCCAGTAG") == "AGGCTGAGTCCATCTCCAGTAGTCATGGAGTGCTCCTGG") << std::endl;
    return 0;
}
```

```js
function solution(dna) {
  // Please write your code here
  const n = dna.length;
  let minDNA = dna;

  // 生成所有旋转表示并比较
  for (let i = 1; i < n; i++) {
    const current = dna.slice(i) + dna.slice(0, i);
    if (current < minDNA) {
      minDNA = current;
    }
  }

  return minDNA;
}

function main() {
  // You can add more test cases here
  console.log(solution("A") === "A");
  console.log(solution("ATCA") === "AATC");
  console.log(solution("AAAA") === "AAAA");
  console.log(solution("CGAGTC") === "AGTCCG");
  console.log(solution("TCATGGAGTGCTCCTGGAGGCTGAGTCCATCTCCAGTAG") === "AGGCTGAGTCCATCTCCAGTAGTCATGGAGTGCTCCTGG");
}

main();
```

```python
def solution(dna):
    n = len(dna)
    minDNA = dna

    # 生成所有旋转表示并比较
    for i in range(1, n):
        current = dna[i:] + dna[:i]
        if current < minDNA:
            minDNA = current

    return minDNA
```


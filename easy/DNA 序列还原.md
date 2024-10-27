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
#include <bits/stdc++.h>
using namespace std;

int solution(std::string dna1, std::string dna2) {
    // Please write your code here
    int n = (int)dna1.size(),m = (int)dna2.size();
    vector<vector<int>>dp(n+1,vector<int>(m+1,0));
    dp[0][0] = 0;//dp[x][y]代表将a字符串前x个字符修改成b字符串前y个字符
    for (int i=1; i<=m; ++i) dp[0][i] = i;
    for (int i=1; i<=n; ++i) dp[i][0] = i;
    for (int i=1; i<=n; ++i) {
        for (int j=1; j<=m; ++j) {
             int one = dp[i-1][j] +1,two = dp[i][j-1]+1,three = dp[i-1][j-1];
             if(dna1[i-1]!=dna2[j-1]) three+=1;
             dp[i][j] = min(min(one,two),three);
         }
    }
    return dp[n][m];
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

```python
def solution(dna1, dna2):
    n = len(dna1)
    m = len(dna2)
    dp = [[0] * (m + 1) for _ in range(n + 1)]
    
    # dp[x][y] 代表将 dna1 的前 x 个字符修改成 dna2 的前 y 个字符所需的最小操作数
    for i in range(1, m + 1):
        dp[0][i] = i
    for i in range(1, n + 1):
        dp[i][0] = i
    
    for i in range(1, n + 1):
        for j in range(1, m + 1):
            one = dp[i-1][j] + 1
            two = dp[i][j-1] + 1
            three = dp[i-1][j-1]
            if dna1[i-1] != dna2[j-1]:
                three += 1
            dp[i][j] = min(one, two, three)
    
    return dp[n][m]
```


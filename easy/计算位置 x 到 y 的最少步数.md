# 问题描述

AB 实验同学每天都很苦恼如何可以更好地进行 AB 实验，每一步的流程很重要，我们目标为了缩短所需的步数。

我们假设每一步对应到每一个位置。从一个整数位置 `x` 走到另外一个整数位置 `y`，每一步的长度是正整数，每步的值等于上一步的值 `-1`， `+0`，`+1`。求 `x` 到 `y` 最少走几步。并且第一步必须是 `1`，最后一步必须是 `1`，从 `x` 到 `y` 最少需要多少步。

## 样例说明

- 整数位置 `x` 为 `12`，另外一个整数位置 `y` 为 `6`，我们需要从 `x` 走到 `y`，最小的步数为：`1`，`2`，`2`，`1`，所以我们需要走 `4` 步。
- 整数位置 `x` 为 `34`，另外一个整数位置 `y` 为 `45`，我们需要从 `x` 走到 `y`，最小的步数为：`1`，`2`，`3`，`2`，`2`，`1`，所以我们需要走 `6` 步。
- 整数位置 `x` 为 `50`，另外一个整数位置 `y` 为 `30`，我们需要从 `x` 走到 `y`，最小的步数为：`1`，`2`，`3`，`4`，`4`，`3`，`2`，`1`，所以我们需要走 `8` 步。

## 输入格式

输入包含 `2` 个整数 `x`，`y`。（`0<=x<=y<2^31`）

## 输出格式

对于每一组数据，输出一行，仅包含一个整数，从 `x` 到 `y` 所需最小步数。

## 输入样例

```
12 6
34 45
50 30
```

## 输出样例

```
4
6
8
```

# 解答

## 思路

对于这道题，要使步数最小，易知当最大步长尽可能大时可得到最小步数，又由于第一步和最后一步都为 1 ，且每步长度变化为-1~1，此时可视为步长为对称的，故可得以下解题步骤：

1. 计算`distance = y - x`
2. 对距离除以二得到一半距离
3. 由于前半部分步长依次+1，故可再除以2再向上取整得到一半步数最后再乘二返回答案

## 代码

### 解法一
```cpp
#include <bits/stdc++.h>
using namespace std;
int main()
{
	int x,y;
	 while(cin>>x>>y)
	 {
	 	if(x>y)swap(x,y);
	 	int ans=0,diff,f=1;
	 	diff=y-x-1;
	 	while(diff>f*f)
	 	f++;
	 	f-=1;
	 	ans=f*2-1;
	 	if(diff>f*f+f)ans+=2;
	 	if(f*f<diff<=f*f+f)ans+=1;
	 	cout<<ans<<endl;
	} 
	return 0;
}     
```

```js
function solution(xPosition, yPosition) {
  // Please write your code here
  return -2;
}

function main() {
    // You can add more test cases here
    console.log(solution(12, 6) === 4);
    console.log(solution(34, 45) === 6);
    console.log(solution(50, 30) === 8);
}

main();
```

### 解法二

```cpp
int solution(int xPosition, int yPosition) {
    // Please write your code here
    long d=abs(xPosition-yPosition);
    long tmp=0;
    long i=1;
    long flag=1;
    while(d>tmp){
        tmp+=i;
//        printf("flag%d  tmp%d    ",flag,tmp); 
        if(d<=tmp) break;
        flag++;        
        tmp+=i;
//        printf("flag%d  tmp%d    ",flag,tmp); 
        if(d<=tmp) break;
        flag++;
        i++;
    }
    return flag;
}

int main() {
    //  You can add more test cases here
    std::cout << (solution(12, 6) == 4) << std::endl;
    std::cout << (solution(34, 45) == 6) << std::endl;
    std::cout << (solution(50, 30) == 8) << std::endl;
    return 0;
}
```
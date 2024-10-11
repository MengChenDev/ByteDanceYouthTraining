# 问题描述

实现一个函数，输入为长度为三的 rgb 字符串，返回为十六进制 HEX 格式字符串

## 输入格式

字符串

## 输出格式

数字

**输入样例**

"rgb(192, 192, 192)"

**输出样例**

12632256

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <string>

int solution(std::string rgb) {
    // Please write your code here
    return -2;
}

int main() {
    //  You can add more test cases here
    std::cout << (solution("rgb(192, 192, 192)") == 12632256) << std::endl;
    std::cout << (solution("rgb(100, 0, 252)") == 6553852) << std::endl;
    std::cout << (solution("rgb(33, 44, 55)") == 2174007) << std::endl;
    return 0;
}
```

```js
function solution(rgb) {
  // Please write your code here
  return -2;
}

function main() {
  //  You can add more test cases here
  console.log(solution("rgb(192, 192, 192)") === 12632256);
  console.log(solution("rgb(100, 0, 252)") === 6553852);
  console.log(solution("rgb(33, 44, 55)") === 2174007);
}

main();
```
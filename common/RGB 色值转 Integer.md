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

rgb分别对应HEX中的第12、34、56位字符，例如255，254，253即为FF FE FA

了解HEX格式字符串组成后题目就变得很简单了

	1. 将输入的rgb分别转换为16进制
	1. 将三个字符串拼接
	1. 将得到的HEX转换为数值

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

  // 使用正则表达式提取RGB值
  let match = rgb.match(/\((\d+),\s*(\d+),\s*(\d+)\)/);

  // 提取颜色分量并转换为整数
  const r = parseInt(match[1], 10);
  const g = parseInt(match[2], 10);
  const b = parseInt(match[3], 10);

  function rgbToHex(r, g, b) {
    // 使用toString(16)将每个颜色分量转换为十六进制，并使用padStart确保每个分量至少有两位
    const hexR = r.toString(16).padStart(2, '0');
    const hexG = g.toString(16).padStart(2, '0');
    const hexB = b.toString(16).padStart(2, '0');

    // 将三个十六进制颜色合并成一个字符串
    const hexColor = `${hexR}${hexG}${hexB}`;

    return hexColor;
  }

  //返回10进制颜色值
  return parseInt(rgbToHex(r, g, b), 16);
}

function main() {
  //  You can add more test cases here
  console.log(solution("rgb(192, 192, 192)") === 12632256);
  console.log(solution("rgb(100, 0, 252)") === 6553852);
  console.log(solution("rgb(33, 44, 55)") === 2174007);
}

main();
```
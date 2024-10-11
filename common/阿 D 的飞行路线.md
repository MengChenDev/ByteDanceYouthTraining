# 问题描述

阿D驾驶一架飞机需要从出发点抵达目的地，但是由于特殊的航空管制，对飞机的飞行路线有严格要求：飞机只能飞向当前机场的前后相邻机场或者相同航空公司管理的机场。现在阿D的leader要求阿D设计最佳的飞行路线，使得起飞次数最少。为此，阿D将所有的机场用一个数组`arr`表示，其中：

- 数组中每个元素表示不同的机场，元素的值表示不同的航空公司。
- `arr[0]`表示出发点，`arr[arr.length - 1]`表示目的地。
- 假设当前在机场`i`（数组下标为`i`），则`i - 1`（`i - 1 >= 0`）和`i + 1`（`i + 1 < arr.length`）表示当前机场的前后机场，则飞机可以飞向编号为`i - 1`和`i + 1`的机场。
- 假设当前在机场`i`，且数组中存在`arr[i] == arr[j]`，则表示机场`i`和机场`j`为相同航空公司管理，则飞机可以飞向编号为`j`的机场。

## 输入格式

用数组表示所有机场

数据范围：

- `1 <= arr.length <= 5 * 10^4`
- `-10^8 <= arr[i] <= 10^8`

## 输出格式

最少起飞次数

**示例 1**：

输入：`arr = [10,12,13,12,14]`

输出：`3`

最佳飞行路线：机场编号 0（出发点） -> 机场编号 1 -> 机场编号 3 -> 机场编号 4（目的地）

说明：`arr[1]`和`arr[3]`等于 12，为相同航空公司管理，机场编号 1 可以直接飞到机场编号 3

**示例 2**：

输入：`arr = [10,11,12,13,14]`

输出：`4`

最佳飞行路线：机场编号 0（出发点） -> 机场编号 1 -> 机场编号 2 -> 机场编号 3 -> 机场编号 4（目的地）

说明：数组中均为不同机场，只能逐一向前飞行

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <vector>

int solution(std::vector<int> airports) {
    // Please write your code here
    return -2;
}

int main() {
    //  You can add more test cases here
    std::vector<int> airports1 = {10, 12, 13, 12, 14};
    std::vector<int> airports2 = {10, 11, 12, 13, 14};

    std::cout << (solution(airports1) == 3) << std::endl;
    std::cout << (solution(airports2) == 4) << std::endl;
    return 0;
}
```

```js
function solution(airports) {
  // Please write your code here
  return -2;
}

function main() {
  //  You can add more test cases here
  console.log(solution([10, 12, 13, 12, 14]) === 3);
  console.log(solution([10, 11, 12, 13, 14]) === 4);
}

main();
```
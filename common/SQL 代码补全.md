# 问题描述

在一个 SQL 编辑器中，需要提供 SQL 代码自动补全的功能，自动补全的候选内容包含两方面：

1. SQL 语法关键字，如 select、where、limit 等，数量约 80 个

2. 数据库名、表名和字段名，如 origin_log_db、event_log_table、user_id，from_mobile，数量 <= 10000 个

例如：用户输入 `s`，此时给出补全提示 `select`；输入 `fr`，给出补全提示 `from` 和 `from_mobile` 让用户选择，输入至 `from_` 时，给出补全提示 `from_mobile`

## 输入格式

1. 第一行是一个整数数字 N，用来表示接下来有几行是代码补全的候选内容

2. 第二到 N + 1 行的每一行是一条候选内容，包括 SQL 关键字，或者数据库名、表名、字段名，所有字符均为小写

3. 最后一行是模拟用户在写 SQL 时输入的字符片段（空格或者回车之后的内容），例如 `sel`

## 输出格式

最后一行用户输入字符片段的补全提示列表，列表按字母序排序

无补全提示时输出 -1

**输入样例**

8

select

from

where

limit

origin_log_db

event_log_table

user_id

from_mobile

f

**输出样例**

from

from_mobile

**数据范围**

数据库名、表名和字段名总数 <= 10000

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <vector>
#include <string>

std::string solution(int num, std::vector<std::string> data, std::string input) {
    // Please write your code here
    return "-2";
}

int main() {
    //  You can add more test cases here
    std::vector<std::string> testData1 = {"select", "from", "where", "limit", "origin_log_db", "event_log_table", "user_id", "from_mobile"};
    std::vector<std::string> testData2 = {"select", "from", "where", "limit", "group", "having", "in", "index", "inner", "insert", "like", "log_db", "log_table", "user_id", "group_name", "group_id"};

    std::cout << (solution(8, testData1, "f") == "from,from_mobile") << std::endl;
    std::cout << (solution(16, testData2, "g") == "group,group_name,group_id") << std::endl;
    std::cout << (solution(16, testData2, "m") == "-1") << std::endl;

    return 0;
}
```

```js
function solution(num, data, input) {
  // Please write your code here
  return -2;
}

function main() {
  //  You can add more test cases here
  const testData1 = ["select", "from", "where", "limit", "origin_log_db", "event_log_table", "user_id", "from_mobile"];
  const testData2 = ["select", "from", "where", "limit", "group", "having", "in", "index", "inner", "insert", "like", "log_db", "log_table", "user_id", "group_name", "group_id"];

  console.log(solution(8, testData1, "f") === "from,from_mobile");
  console.log(solution(16, testData2, "g") === "group,group_name,group_id");
  console.log(solution(16, testData2, "m") === "-1");
}

main();
```
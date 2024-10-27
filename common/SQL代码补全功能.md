## SQL代码补全功能

### 问题描述

在开发SQL编辑器时，实现自动补全功能是提高用户体验的重要一环。小C需要实现一个功能，根据用户输入的字符片段，快速从已知的SQL关键字和数据库相关名称中找到所有以该片段开头的候选词，并按字典序输出。

例如，当用户输入 `s` 时，编辑器需要自动提示以 `s` 开头的所有可能选项，如 `select`。如果用户输入 `fr`，则需要提示 `from` 和 `from_mobile`。如果在提示中只有一个选项符合，如输入 `from_` 时只提示 `from_mobile`。

------

### 测试样例

***样例1：***

> 输入：`num = 8,data = ["select", "from", "where", "limit", "origin_log_db", "event_log_table", "user_id", "from_mobile"], input = "f"`
> 输出：`'from,from_mobile'`

***样例2：***

> 输入：`num = 8,data = ["select", "from", "where", "limit", "origin_log_db", "event_log_table", "user_id", "from_mobile"], input = "wh"`
> 输出：`'where'`

***样例3：***

> 输入：`num = 8,data = ["select", "from", "where", "limit", "origin_log_db", "event_log_table", "user_id", "from_mobile"], input = "z"`
> 输出：`'-1'`

***样例4：***

> 输入：`num = 8,data = ["select", "from", "where", "limit", "origin_log_db", "event_log_table", "user_id", "from_mobile"], input = "origin"`
> 输出：`'origin_log_db'`

```python
def solution(num, data, input):
    filtered_words = list({word for word in data if word.startswith(input)})

    filtered_words.sort()

    return ','.join(filtered_words) if filtered_words else '-1'
```


# 问题描述

你需要实现一个 Base32 的编码和解码函数。

相比于 Base32，你可能更熟悉 Base64，Base64 是非常常见的用字符串形式表示二进制数据的方式，在邮件附件、Web 中的图片中都有广泛的应用。

Base32 是 Base64 的变种，与 Base64 不同的地方在于 Base64 以 6 bit 为一组作为索引，而 Base32 以 5 bit 为一组作为索引，每一组用一个 ASCII 字符表示。Base 64 总共需要 64 个字符表示，而 Base32 则只需要 32 个字符表示。

Base32 的编码流程如下：
- 对二进制数据进行预处理：如果二进制数据的 bit 数目不不是 5 的倍数的话，在末尾补 0 直至为 5 的倍数
- 以 5 bit 为一组进行分组
- 将每一组的 5 bit 二进制转换为索引（0 - 31）
- 在索引 - 字符转换表中查询索引对应的字符
- 根据原始二进制数据的 bit 数目除以 40 后的余数，确定末尾需要补 0 的数目
  - 如果原始二进制数据 bit 数目除以 40 后的余数是 0 的话，不需要补 +
  - 如果原始二进制数据 bit 数目除以 40 后的余数是 8 的话，补 6 个 +
  - 如果原始二进制数据 bit 数目除以 40 后的余数是 16 的话，补 4 个 +
  - 如果原始二进制数据 bit 数目除以 40 后的余数是 24 的话，补 3 个 +
  - 如果原始二进制数据 bit 数目除以 40 后的余数是 32 的话，补 1 个 +

Base32 的索引 - 字符转换表见下方。

索引：0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31

字符：9 8 7 6 5 4 3 2 1 0 m  n  b  v  c  x  z  a  s  d  f  g  h  j  k  l  p  o  i  u  y  t

**示例**

**编码**

- 输入：字符串 `foo`
- 字符 `f` 的 ASCII 编号为 102，字符 `o` 的 ASCII 编号为 111
- 将字符串 `foo` 以 ASCII 编号形式表达为 102 111 111 的序列
- 将 102 111 111 的序列转换为二进制表示，即 01100110 01101111 01101111，将二进制字符串以 40 个为一组进行分割
- 最后一组的二进制字符串长度为 24，不是 5 的倍数，因此在最后补 0，直至其能被 5 整除（在此例子中，补 1 个即可），二进制字符串表示为： 01100110 01101111 01101111 0
- 每 5 bit 为一组，表示为：01100 11001 10111 10110 11110
- 将每一组转换为十进制的索引，表示为：12 25 23 22 30，对应字符 `b` `l` `j` `h` `y`
- 由于最终输出字符串长度不是 8 的倍数，在输出最后补充 3 个 `+`
- 查询索引 - 字符转换表后，可以得出最终的输出为：`bljhy+++`

`Input data: foo`
`Input in Unicode: 102 111 111`
`Unicode in binary (8-bit): 01100110 01101111 01101111 0`
`Unicode in binary (5-bit): 01100 11001 10111 10110 11110`
`Decimal: 12 25 23 22 30`
`Pad: + + +`
`Output: b l j h y + + +`

**解码**

- 输入：`bljhy+++`
- 查询索引 - 字符转换表后，可知原始的二进制数据组为：01100 11001 10111 10110 11110
- 由末尾 3 个 `+` 可知在编码时原始二进制数据最后一组的个数为 24 个，由此可知最后一组数据为：01100110 01101111 01101111
- 将二进制数据转换为 ASCII 编号后可知，原始字符串的 Unicode 序列为：102 111 111
- 将 Unicode 序列转换为字符串，即可得出原始字符串，为：`foo`

**输入示例**

`foo`
`b0zj5+++`

- 第一行为需要编码的原始字符串：`rawStr`
- 第二行为需要解码的 Base32 字符串：`encodedStr`

**输出示例**

`bljhy+++`
`bar`

**解释**：
- 第一行编码后的输出为 `bljhy+++`
- 第二行解码后的输出为 `bar`

**数据范围**

`rawStr[n]` 为 ASCII 的可显示字符，`rawStr.length < 2048`
`encodedStr` 为使用此算法编码后的 Base32 字符序列，`encodedStr.length < 4096`

# 解答

## 思路

## 代码

```cpp
#include <iostream>
#include <string>

std::string solution(std::string rawStr, std::string encodedStr) {
    // Please write your code here
    return "result1:result2";
}

int main() {
    // You can add more test cases here
    std::cout << (solution("foo", "b0zj5+++") == "bljhy+++:bar") << std::endl;
    std::cout << (solution("The encoding process represents 40-bit groups of input bits as output strings of 8 encoded characters.  Proceeding from left to right, a 40-bit input group is formed by concatenating 5 8bit input groups. These 40 bits are then treated as 8 concatenated 5-bit groups, each of which is translated into a single character in the base 32 alphabet.  When a bit stream is encoded via the base 32 encoding, the bit stream must be presumed to be ordered with the most-significant- bit first. That is, the first bit in the stream will be the high- order bit in the first 8bit byte, the eighth bit will be the low- order bit in the first 8bit byte, and so on.", "bljhy+++b0zj5+++") == "maf3m164vlahyl60vlds9i6svuahmiod58l3mi6sbglhmodfcbz61b8vb0fj1162c0jjmi6d58jhb160vlk2mu89b0fj1il9b4ls9oogcak2mu89cvp25pncbuls9oo359i79lncbvjh1ln558ahzknsb4aj1lnscbj7917zc0jh3ln4bafhill9bll3yo09vashbu89cajs9id0buf21n89b5z61b8vb0fj1160vlk2mu89bul3yunz58fj3163vul3pln558a2s166vuj33knfbgj37u60vlds9v0928a3su89v4j29unf58dj5oogc8lsi17fv8sj3l093zk79kd0cals9knsbfz21p64vkz21id4b4p3ml89b4ls9c89bvjhiko8cashiknfbgs79v0vb0fj1162c0jjmi6d4zz3mkn6v9z3yla9cuf3sko158fj316fc0zhiiobb4p3ml89v4j21ol9b5z23pncbuh3m166v8zj5kn6casj5160vkz21p6458a37io459ld5168vak3zkn7bgp7i189muf3moa9b5z35pnf58lj1id4b4hs9pnd58shikoxbash116hv4zs9u61bfz35kndbfz63ba9bgj33oo5v4j3cn89caf3m167v4p79iofc0sh7o09vgpj3u89b0ss9i6sbgljmon4bzz21ol9b0ss9oosbasj5ln558ohsu6158p3zl09vgjj3u8vcvfhcod0blfh3kncczhs9kd0czz3bpnscvp7i17fv8zj1160cbh79u61bfz3bpnscvp79kd0czz3soa9caf3m16dcal3mknv58ohso6b58a3m16fv8ss9p60buf7p16xc0s3mia9b0fj1160vkz21p6458d3siddczz6zkd0czz35ynfbfh79u61bfz3mpn2v8p3z167v4p79uo0vah79kd458p3zl09vajjcn09vul31lns58a3su89v4j79u61bfz3bpnscvp79c67v4p79kdlcassk168vls79iox58jhinz+:foobar") << std::endl;
    return 0;
}
```

```js
function solution(rawStr, encodedStr) {
  // Please write your code here
  return "result1:result2";
}

function main() {
  // You can add more test cases here
  console.log(solution("foo", "b0zj5+++") === "bljhy+++:bar");
  console.log(solution("The encoding process represents 40-bit groups of input bits as output strings of 8 encoded characters.  Proceeding from left to right, a 40-bit input group is formed by concatenating 5 8bit input groups. These 40 bits are then treated as 8 concatenated 5-bit groups, each of which is translated into a single character in the base 32 alphabet.  When a bit stream is encoded via the base 32 encoding, the bit stream must be presumed to be ordered with the most-significant- bit first. That is, the first bit in the stream will be the high- order bit in the first 8bit byte, the eighth bit will be the low- order bit in the first 8bit byte, and so on.", "bljhy+++b0zj5+++") === "maf3m164vlahyl60vlds9i6svuahmiod58l3mi6sbglhmodfcbz61b8vb0fj1162c0jjmi6d58jhb160vlk2mu89b0fj1il9b4ls9oogcak2mu89cvp25pncbuls9oo359i79lncbvjh1ln558ahzknsb4aj1lnscbj7917zc0jh3ln4bafhill9bll3yo09vashbu89cajs9id0buf21n89b5z61b8vb0fj1160vlk2mu89bul3yunz58fj3163vul3pln558a2s166vuj33knfbgj37u60vlds9v0928a3su89v4j29unf58dj5oogc8lsi17fv8sj3l093zk79kd0cals9knsbfz21p64vkz21id4b4p3ml89b4ls9c89bvjhiko8cashiknfbgs79v0vb0fj1162c0jjmi6d4zz3mkn6v9z3yla9cuf3sko158fj316fc0zhiiobb4p3ml89v4j21ol9b5z23pncbuh3m166v8zj5kn6casj5160vkz21p6458a37io459ld5168vak3zkn7bgp7i189muf3moa9b5z35pnf58lj1id4b4hs9pnd58shikoxbash116hv4zs9u61bfz35kndbfz63ba9bgj33oo5v4j3cn89caf3m167v4p79iofc0sh7o09vgpj3u89b0ss9i6sbgljmon4bzz21ol9b0ss9oosbasj5ln558ohsu6158p3zl09vgjj3u8vcvfhcod0blfh3kncczhs9kd0czz3bpnscvp7i17fv8zj1160cbh79u61bfz3bpnscvp79kd0czz3soa9caf3m16dcal3mknv58ohso6b58a3m16fv8ss9p60buf7p16xc0s3mia9b0fj1160vkz21p6458d3siddczz6zkd0czz35ynfbfh79u61bfz3mpn2v8p3z167v4p79uo0vah79kd458p3zl09vajjcn09vul31lns58a3su89v4j79u61bfz3bpnscvp79c67v4p79kdlcassk168vls79iox58jhinz+:foobar");
}

main();
```
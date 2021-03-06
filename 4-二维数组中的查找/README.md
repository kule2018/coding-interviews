# 二维数组中的查找

有这样一个二维数组，每一行从左到右和每一列从上到下都是越来越大，如下为一个示例：

```
1 3 6 9
3 4 7 11
4 7 8 12
6 8 9 14
```

请判断这个二维数组中是否存在某个数字。

## 解法

比如判断数字 4 是否存在于数组中。

我们从右上角开始，9 大于 4，所以 9 那一列不用再判断。 6 大于 4，所以 6 那一列也不用继续判断。 3 小于 4，3 这一行不用继续判断。再下一个数字刚好是 4，说明存在这个数字。

代码如下：

```js
const isNumberExistInArray = (numbers, num) => {
  const rowLength = numbers.length
  const columnLength = (numbers[0] || []).length
  let i = 0
  let j = columnLength - 1
  let exist = false
  while (i <= rowLength - 1 && j >= 0 && !exist) {
    if (numbers[i][j] === num) {
      exist = true
    } else if (numbers[i][j] > num) {
      j--
    } else {
      i++
    }
  }
  return exist
}
```

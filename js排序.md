#### 冒泡排序

```
function bubbleSort (arr) {
    // 不循环最后一个元素
    for (var i=0;i<arr.length-1;i++) {
        // 第二次循环 从数组第二个元素开始
        for (var j=i+1;j<arr.length;j++) {
            // 大小互换位置
            if (arr[i]>arr[j]) {
                var temp = arr[i]
                arr[i] = arr[j]
                arr[j] = temp
            }
        }
    }
    return arr
}
```

#### 冒泡排序

```
function quickSort(arr) {
    // 终止递归
    if (arr.length<=1) {
        return arr
    }
    // 数组中间值的索引
    var midIndex = Math.floor(arr.length/2)
    // 使用splice 截取中间值
    var midIndexVal = arr.splice(midIndex, 1)
    let left = []
    let right = []
    for (var i = 0;i <arr.length;i++) {
        if (arr[i]<midIndexVal) {
            left.push(arr[i])
        } else {
            right.push(arr[i])
        }
    }
    // 不断分割左右数组传入 quickSort,把每层分割的数组用concat链接起来
    return quickSort(left).concat(midIndexVal, quickSort(right))
}
console.log(quickSort(arr))
```




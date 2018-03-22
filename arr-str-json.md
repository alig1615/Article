# arr  str json
#### 1、arr
    arr.join()
>     转换为字符串
>     arr.join(',') 把数组元素用 ‘,’分割为字符串  默认不传会自动已‘,’分割
>     arr.joi('') 把数组元素用 ‘’分割为字符串  [1,3,4,56,7].join('')  // '134567'

    arr.pop()   
>     删除最后一个元素 

    arr.shift() 
>   删除最前一个元素 

    arr.splice(startInd,length) 
>   删除从指定位置startInd开始的指定数量length的元素，数组形式返回所移除的元素
    
    arr.slice(start[,end]) 
>   截取数组， 
>   start 从0 开始
>   end 不包含end 
   
    arr.concat(arr1[,arr2...])
>     连接多个数组，返回新数组
>     合并数组

    arr.slice(0)     拷贝数组
>   返回数组的拷贝数组，注意，返回新数组，不是指向原数组
    arr.concat()
>   返回数组的拷贝数组，注意，返回新数组，不是指向原数组
    
    arr.reverse()  // 排序
>   反转元素（最前的排到最后、最后的排到最前）

    arr.sort()
>   按照元素的第一位排序，如果第一位

#### 2、str
    str.charAt(index) 
>     返回指定索引位置处的字符

    str.slice(start[,end])
>     返回字符串的片段 
>     start 从0 开始，包含start索引 为负值 取length+start
>     end 从0 开始，不包含end索引 为负值 取length+start
    str.replace(/(^\s+)|(\s+$)/g,"")
>     清除字符串前后空格

    str.replace(/\s/g, '')
>     清除字符串所有空格

    str.substring(start,end)
>     返回str指定位置的子字符串
>     start && end 同上
>     使用start和end两者中的较小值作为子字符串的起始点。如果start或end为NaN或者为负数，那么将其替换为0。

    str.substr(start[,length])
>     返回一个指定位置开始的指定长度的子字符串
>     start 从0 开始，包含start索引    
>     length 为空，返回从start之后的所有字符

    str.indexOf(substr[,startIndex])
>     返回str内第一次出现的字符串位置，没找到，返回 -1
>     substr 要在str中查找的子字符串
>     startIndex 该整数值 指出在str内开始查找的索引，省略，从字符串开始出查找

    str.lastIndexOf(substr[,startIndex])
>     返回str中字符串最后出现的位置。如果没有匹配到子字符串，则返回-1
>     substr 要在str中查找的子字符串
>     startIndex 该整数值 指出在str内开始查找的索引，省略，从字符串末尾查找
    
    str.lastIndexOf("CD",6);
>     由6位置从右向左查找 ...456

    str.search(reExp)
>     返回与正则表达式查找内容匹配的第一个字符串的位置
>     var str = "ABCDECDF"; 
>     str.search("CD"); // 或 str.search(/CD/i); 
>     结果：2 

    str.concat(str1[,str2...])
>     连接str和str1,str2
>     var str = "ABCDEF"; 
>     str.concat("111","234"); 
>     结果：ABCDEF111234 
    
    str.split(separator[,limit])
>     separator字符串或 正则表达式 对象, limit该值用来限制返回数组中的元素个数。 字符串转数组 

    var str = "AA,BB,CC,DD,EE,FF"; 
    str.split(","); 
>     ["AA", "BB", "CC", "DD", "FF"]

    str.split(",",3); 
>     ["AA", "BB", "CC"]

    str.toLowerCase()
>     字符串中的字母转换为小写
    
    str.toUpperCase()
>     字符串中的字母转换为大写

#### 3、json
    JSON.stringify(date)
    
>     json 转 json字符串
>     var date = {myArr : ["a" , "b" , "c" , "d"] , count : 4}
>     JSON.stringify(date)
>     "{'myArr':['a','b','c','d'],'count':4}"
    
    JSON.parse(str)
    
>     json字符串 转 json
>     var str = "{"myArr":["a","b","c","d"],"count":4}"
>     JSON.parse(str) 
>         {myArr : ["a" , "b" , "c" , "d"] , count : 4}

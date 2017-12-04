## 正则表达式
>  match、exec、test、search、replace、split 方法

#### 1、match 方法 

使用正则表达式模式对字符串执行查找，并将包含查找的结果作为数组返回。 
stringObj.match(rgExp) 

- 参数 stringObj 必选项。
> 对其进行查找的 String 对象或字符串文字。

- rgExp 必选项。
> 为包含正则表达式模式和可用标志的正则表达式对象。也可以是包含正则表达式模式和可用标志的变量名或字符串文字。 

其余说明与exec一样，不同的是如果match的表达式匹配了全局标记g将出现所有匹配项，而不用循环，但所有匹配中不会包含子匹配项。 
例子1： 
```
function MatchDemo(){ var r, re; // 声明变量。 
    var s = "The rain in Spain falls mainly in the plain"; 
    re = /(a)in/ig; // 创建正则表达式模式。 
    r = s.match(re); // 匹配搜索字符串。 
    cnsole.log(r); // 返回的数组包含了所有 "ain"出现的四个匹配，r[0]、r[1]、r[2]、r[3]。 // 但没有子匹配项a。
} // 输出结果：ain,ain,ain,ain
 ```
####  2、exec 方法 

用正则表达式模式在字符串中查找，并返回该查找结果的第一个值（数组），如果匹配失败，返回null。
rgExp.exec(str) 

参数
-  rgExp 必选项。包含正则表达式模式和可用标志的正则表达式对象。 
-  str 必选项。要在其中执行查找的 String 对象或字符串文字。 

返回数组包含： 
- input：整个被查找的字符串的值
- index：匹配结果所在的位置（位）； 
- lastInput：下一次匹配结果的位置； 

arr：结果值，arr[0]全匹配结果，arr[1,2...]为表达式内()的子匹配，由左至右为1,2...。 


```
function execDemo(){ 
    var r, re; // 声明变量。 
    var s = "The rain in Spain falls mainly in the plain"; 
    re = /[\w]*(ai)n/ig; 
    r = re.exec(s); 
    document.write(r + "<br/>"); 
    for(key in r){ 
        document.write(key + "-" + r[key] + "<br/>"); 
    } 
} 
cnsole.log(execDemo()); 
```
输出： 

rain,ai 

input-The rain in Spain falls mainly in the plain 

index-4 

lastIndex-8 

0-rain 

1-ai 

#### 3、test 方法 

返回一个 Boolean 值，它指出在被查找的字符串中是否匹配给出的正则
表达式。 

rgexp.test(str) 

参数 

- rgexp 必选项。包含正则表达式模式或可用标志的正则表达式对象。 

- str 必选项。要在其上测试查找的字符串。 

说明 
test 方法检查字符串是否与给出的正则表达式模式相匹配，如果是则返回 true，否则就返回 false。

```
function TestDemo(re, s){ 
    var s1; 
    if (re.test(s)) 
        s1 = " 匹配正则式 "; 
    else 
        s1 = " 不匹配正则式 "; 
    return("'" + s + "'" + s1 + "'"+ re.source + "'"); 
} 
cnsole.log(TestDemo(/ab/,'cdef'));

输出结果：'cdef' 不匹配正则式 'ab' 
注意：test()继承正则表达式的lastIndex属性，表达式在匹配全局标志g的时候须注意。 
```

#### 4、search 方法 

stringObj.search(rgExp)
返回与正则表达式查找内容匹配的第一个子字符串的位置（偏移位）


- 参数  stringObj 必选项。要在其上进行查找的 String 对象或字符串文字。 
- 参数  rgExp 必选项。包含正则表达式模式和可用标志的正则表达式对象。 

说明：如果找到则返回子字符至开始处的偏移位，否则返回-1。

```
function SearchDemo(){ 
    var r, re; // 声明变量。 
    var s = "The rain in Spain falls mainly in the plain."; 
    re = /falls/i; // 创建正则表达式模式。 
    re2 = /tom/i; 
    r = s.search(re); // 查找字符串。 
    r2 = s.search(re2); 
    return("r：" + r + "；r2：" + r2); // 返回 Boolean 结果。 
} 
console.log(SearchDemo());

输出：r：18；r2：-1 
```
#### 5、replace 方法 

stringObj.replace(rgExp, replaceText) 
返回根据正则表达式进行文字替换后的字符串的复制。 


- stringObj 
必选项。要执行该替换的 String 对象或字符串文字。该字符串不会被 replace 方法修改。

- rgExp 必选项。
为包含正则表达式模式或可用标志的正则表达式对象。也可以是 String 对象或文字。如果 rgExp 不是正则表达式对象，它将被转换为字符串，并进行精确的查找；不要尝试将字符串转化为正则表达式。 

- replaceText 必选项。
是一个String 对象或字符串文字，对于stringObj 中每个匹配 rgExp 中的位置都用该对象所包含的文字加以替换。在 Jscript 5.5 或更新版本中，replaceText 参数也可以是返回替换文本的函数。

说明 

replace 方法的结果是一个完成了指定替换的 stringObj 对象的复制。意思为匹配的项进行指定替换，其它不变作为StringObj的原样返回。 
> ECMAScript v3 规定，replace() 方法的参数 replacement 可以是函数而不是字符串。在这种情况下，每个匹配都调用该函数，它返回的字符串将作为替换文本使用。该函数的第一个参数是匹配模式的字符串。接下来的参数是与模式中的子表达式匹配的字符串，可以有 0 个或多个这样的参数。


```

function f2c(s) { 
    var test = /([\d]{4})-([\d]{1,2})-([\d]{1,2})/; 
    return(s.replace (test, function($0,$1,$2,$3) { 
            return($2 +"/" + $1); 
        }) 
    ); 
} 
console.log(f2c("today: 2017-11-26")); 
输出：today: 11/2017
```

#### 6、split 方法 

stringObj.split([separator[, limit]]) 
将一个字符串分割为子字符串，然后将结果作为字符串数组返回。 

参数 
- stringObj 必选项。要被分解的 String 对象或文字。该对象不会被 split 方法修改。 
- separator 可选项。字符串或 正则表达式 对象，它标识了分隔字符串时使用的是一个还是多个字符。如果忽略该选项，返回包含整个字符串的单一元素数组。 
- limit 可选项。该值用来限制返回数组中的元素个数。 
- 
说明 split 方法的结果是一个字符串数组，在 stingObj 中每个出现 separator 的位置都要进行分解。separator 不作为任何数组元素的部分返回。


```
function SplitDemo(){ 
    var s, ss; 
    var s = "The rain in Spain falls mainly in the plain."; 
    // 正则表达式，用不分大不写的s进行分隔。 
    ss = s.split(/s/i); 
    return(ss); 
} 
cnsole.log(SplitDemo());

输出：The rain in ,pain fall, mainly in the plain. 
```

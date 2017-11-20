## 正则表达式

#### 1、作用
> - 测试字符串的某个模式。例如，可以对一个输入字符串进行测试，看在该字符串是否存在一个电话号码模式或一个信用卡号码模式。这称为数据有效性验证 
> - 替换文本。可以在文档中使用一个正则表达式来标识特定文字，然后可以全部将其删除，或者替换为别的文字 
> - 根据模式匹配从字符串中提取一个子字符串。可以用来在文本或输入字段中查找特定文字 
#### 2、语法
> - 一个正则表达式就是由普通字符（例如字符 a 到 z）以及特殊字符（称为元字符）组成的文字模式。
> - 该模式描述在查找文字主体时待匹配的一个或多个字符串。正则表达式作为一个模板，将某个字符模式与所搜索的字符串进行匹配。 

#### 3、创建正则表达式

```
var re = new RegExp();
//RegExp是一个对象,和Aarray一样  
//但这样没有任何效果,需要将正则表达式的内容作为字符串传递进去  
re =new RegExp("a");
//最简单的正则表达式,将匹配字母a  
re=new RegExp("a","i");
//第二个参数,表示匹配时不分大小写
```

RegExp构造函数第一个参数为正则表达式的文本内容,而第一个参数则为可选项标志
- g （全文查找） 
- i （忽略大小写） 
- m （多行查找）


```
var re = new RegExp("a","gi")
//匹配所有的a或A  
```
正则表达式还有另一种正则表达式字面量的声明方式 

```
var re = /a/gi
```

#### 方法和属性

正则表达式对象的方法 

- test,返回一个 Boolean 值，它指出在被查找的字符串中是否存在模式。如果存在则返回 true，否则就返回 false。 
- exec,用正则表达式模式在字符串中运行查找，并返回包含该查找结果的一个数组。 
- compile,把正则表达式编译为内部格式，从而执行得更快。


#### 正则表达式对象的属性 

- source,返回正则表达式模式的文本的复本。只读。 
- lastIndex,返回字符位置，它是被查找字符串中下一次成功匹配的开始位置。 
- 1...9,返回九个在模式匹配期间找到的、最近保存的部分。只读。 
- input ($_),返回执行规范表述查找的字符串。只读。 
- lastMatch ($&),返回任何正则表达式搜索过程中的最后匹配的字符。只读。 
- lastParen ($+),如果有的话，返回任何正则表达式查找过程中最后括的子匹配。只读。 
- leftContext ($`),返回被查找的字符串中从字符串开始位置到最后匹配之前的位置之间的字符。只读。 
- rightContext ($'),返回被搜索的字符串中从最后一个匹配位置开始到字符串结尾之间的字符。只读。 
- String对象一些和正则表达式相关的方法 
- match,找到一个或多个正则表达式的匹配。 
- replace,替换与正则表达式匹配的子串。 
- search,检索与正则表达式相匹配的值。 
- split,把字符串分割为字符串数组。 
-

#### 小案例

> test方法,测试字符串,符合模式时返回true,否则返回false  
> var re = /he/;  //最简单的正则表达式,将匹配he这个单词  
> var str = "he";  
> alert(re.test(str));//true  
> str = "we";  
> alert(re.test(str));//false  
> str = "HE";  
> alert(re.test(str));
//false,大写,如果要大小写都匹配可以指定i标志(i是ignoreCase或case-insensitive的表示)  
> re = /he/i;  
> alert(re.test(str));//true  
> str = "Certainly!He loves her!";  
> alert(re.test(str));
//true,只要包含he(HE)就符合,如果要只是he或HE,不能有其它字符,则可使用^和$  
> re = /^he/i;//脱字符(^)代表字符开始位置  
> alert(re.test(str));//false,因为he不在str最开始  
> str = "He is a good boy!";  
> alert(re.test(str));//true,He是字符开始位置,还需要使用$  
> re = /^he$/i;//$表示字符结束位置  
> alert(re.test(str));//false  
> str = "He";  
> alert(re.test(str));//true  
> //当然,这样不能发现正则表达式有多强大,因为我们完全可以在上面的例子中使用==或indexOf  
> re = /\s/;// \s匹配任何空白字符，包括空格、制表符、换页符等等  
> str= "user Name";//用户名包含空格  
> alert(re.test(str));//true  
> str = "user     Name";//用户名包含制表符  
> alert(re.test(str));//true  
> re=/^[a-z]/i;//[]匹配指定范围内的任意字符,这里将匹配英文字母,不区分大小写  
> str="variableName";//变量名必须以字母开头  
> alert(re.test(str));//true  
> str="123abc";  
> alert(re.test(str));//false  


> var osVersion = "Ubuntu 8";//其中的8表示系统主版本号  
> var re = /^[a-z]+\s+\d+$/i; //+号表示字符至少要出现1次,\s表示空白字符,\d表示一个数字  
> alert(re.test(osVersion));//true,但我们想知道主版本号  
> //另一个方法exec,返回一个数组,数组的第一个元素为完整的匹配内容  
> re=/^[a-z]+\s+\d+$/i;  
> arr = re.exec(osVersion);  
> alert(arr[0]);//将osVersion完整输出,因为整个字符串刚好匹配re  
> //我只需要取出数字  
> re=/\d+/;  
> var arr = re.exec(osVersion);  
> alert(arr[0]);//8  

#### 子匹配

> //exec返回的数组第1到n元素中包含的是匹配中出现的任意一个子匹配,当字符串不匹配re时,exec方法将返回null 
> re=/^[a-z]+\s+(\d+)$/i;//用()来创建子匹配  
> arr =re.exec(osVersion);  
> alert(arr[0]);//整个osVersion,也就是正则表达式的完整匹配  
> alert(arr[1]);//8,第一个子匹配,事实也可以这样取出主版本号  
> alert(arr.length);//2  
> osVersion = "Ubuntu 8.10";//取出主版本号和次版本号  
> re = /^[a-z]+\s+(\d+)\.(\d+)$/i;//.是正则表达式元字符之一,若要用它的字面意义须转义  
> arr = re.exec(osVersion);  
> alert(arr[0]);//完整的osVersion  
> alert(arr[1]);//8  
> alert(arr[2]);//10  

#### String对象的一些和正则表达式有关的方法 


replace方法,用于替换字符串  
> var str ="some money";  
> alert(str.replace("some","much"));//much money  
> //replace的第一个参数可以为正则表达式  
> var re = /\s/;//空白字符  
> alert(str.replace(re,"%"));//some%money  
> //在不知道字符串中有多少空白字符时,正则表达式极为方便  
> str ="some some             \tsome\t\f";  
> re = /\s+/;  
> alert(str.replace(re,"#"));//但这样只会将第一次出现的一堆空白字符替换掉  
> //因为一个正则表达式只能进行一次匹配,\s+匹配了第一个空格后就退出了  
> re = /\s+/g;//g,全局标志,将使正则表达式匹配整个字符串  
> alert(str.replace(re,"@"));//some@some@some@  
> //另一个与之相似的是split  
> var str = "a-bd-c";  
> var arr = str.split("-");//返回["a","bd","c"]  
> //如果str是用户输入的,他可能输入a-bd-c也可能输入a bd c或a_bd_c,但不会是abdc(这样就说他输错了)  
> str = "a_db-c";//用户以他喜欢的方式加分隔符s  
> re=/[^a-z]/i;//前面我们说^表示字符开始,但在[]里它表示一个负字符集  
> //匹配任何不在指定范围内的任意字符,这里将匹配除字母处的所有字符  
> arr = str.split(re);//仍返回["a","bd","c"];  


在字符串中查找时我们常用indexOf,与之对应用于正则查找的方法是search  
当search方法没有找到匹配时,将返回-1 
> str = "My age is 18.Golden age!";//年龄不是一定的,我们用indexOf不能查找它的位置  
> re = /\d+/;  
> alert(str.search(re));//返回查找到的字符串开始下标10  
> //注意,因为查找本身就是出现第一次就立即返回,所以无需在search时使用g标志  
> //下面的代码虽然不出错,但g标志是多余的  
> re=/\d+/g;  
> alert(str.search(re));//仍然是10 
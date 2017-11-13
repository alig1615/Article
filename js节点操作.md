元素节点
节点类型主要有三种：元素节点，属性节点和文本节点。

节点类型 | node name | node value
---|---|---
元素 | 元素名称 | null
属性 | 属性名称 | 属性值
文本 | #text | 文本内容
> 而对DOM的主要也就是围绕元素节点和属性节点的增删改查，对元素节点的操作和对属性节点的操作。
### 元素节点
1、查
> 在对DOM进行增删改之前，首先要找到对应的元素

```
getElementByID()       // 得到单个节点
getElementsByTagName()    // 得到节点数组 NodeList
getElementsByName()      // 得到节点数组 NodeList

```
还可以利用元素节点的属性获取它的父子节点和文本节点：

子节点
```
Node.childNodes  //获取子节点列表NodeList;注意换行在浏览器中被算作了text节点，如果用这种方式获取节点列表，需要进行过滤
Node.firstChild  //返回第一个子节点
Node.lastChild  //返回最后一个子节点
```
父节点

```
Node.parentNode   // 返回父节点
Node.ownerDocument  //返回祖先节点（整个document）
```

兄弟节点


```
Node.previousSibling    // 返回前一个节点，如果没有则返回null
Node.nextSibling       // 返回后一个节点
```

2、增

> 新增节点首先要创建节点，然后将新建的节点插入DOM中，创建节点和插入节点的方法，复制节点的方法也在创建节点。

创建节点
> createElement()    // 按照指定的标签名创建一个新的元素节点

创建代码片段（为避免频繁刷新DOM，可以先创造代码片段，完成所有节点操作之后统一添加到DOM中）

```
createDocumentFragment()
```

复制节点

```
clonedNode = Node.cloneNode(boolean) // 只有一个参数，传入一个布尔值，true表示复制该节点下的所有子节点；false表示只复制该节点

```

插入节点


```
// 插入node

parentNode.appendChild(childNode);  // 将新节点追加到子节点列表的末尾
parentNode.insertBefore(newNode, targetNode);  //将newNode插入targetNode之前
 
// 插入html代码
node.insertAdjacentHTML('beforeBegin', html);  //在该元素之前插入代码
node.insertAdjacentHTML('afterBegin', html);  //在该元素的第一个子元素之前插入代码
node.insertAdjacentHTML('beforeEnd', html);  //在该元素的最后一个子元素之后插入代码
node.insertAdjacentHTML('afterEnd', html);  //在该元素之后插入代码
```

替换节点

```
parentNode.replace(newNode, targetNode);    //使用newNode替换targetNode
```

3、删
移除节点
```
parentNode.removeChild(childNode);  // 移除目标节点
node.parentNode.removeChild(node);    //在不清楚父节点的情况下使用

```
### 属性节点

> 操作属性节点，就是对DOM样式进行增删改查。对于行内样式、内联样式、外部样式有不同的操作方法；各种方法获得的样式也有可读可写和只读之分。

直接获取CSS样式


```
node.style.color     // 可读可写
```

Style本身的属性和方法
```
node.style.cssText     //获取node行内样式字符串
node.style.length      //获取行内样式个数
node.style.item(0)     //获取指定位置的样式
```
获取和修改元素样式
> HTML5为元素提供了一个新的属性：classList 来实现对元素样式表的增删改查


```
node.classList.add(value);     //为元素添加指定的类
node.classList.contains(value);  // 判断元素是否含有指定的类，如果存在返回true
node.classList.remove(value);  // 删除指定的类
node.classList.toggle(value);  // 有就删除，没有就添加指定类
```

修改DOM特性的方法


```
Node.getAttribute('id')    // 获取
Node.setAttribute('id')    // 设置
Node.removeAttribute()     // 移除
Node.attributes        // 获取DOM全部特性
```

只读方法

> - getComputedStyle是window的方法。
> - 它能够获取当前元素所有最终使用的CSS属性值，但是是只读的。
> - 它有两个参数，第一个为传入的节点，第二个可以传入:hover, :blur等获取其伪类样式，如果没有则传入null。
> - 然而IE并不支持getComputedStyle方法，可以使用currentStyle来保持兼容性：


```
window.getComputedStyle ? window.getComputedStyle(node, null) : node.currentStyle

```



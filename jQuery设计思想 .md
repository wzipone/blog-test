# jQuery 设计思想
## jQuery 如何获取元素
jQuery 的基本设计思想：选取网页元素，然后直接进行相应操作，使用$函数（也就是jQuery）接收参数，返回对元素的操作接口
```javascript
$(document) // 接受Dom对象参数
$('#myId') // 接受选择器表达式参数
$('div.myClass')

//也可以是jQuery特有的表达式
$('a:first') // 选择网页中第一个a元素
$('tr:odd') // 选择表格的奇数行
$('div:animated') // 选择当前处于动画状态的div元素
```
## jQuery 的链式操作
通过每次选择元素，操作元素，然后继续返回元素操作接口的方式，可以使一连串操作链接，以链条的形式写出来，比如：
```javascript
$('div').find('h3').eq(2).html('Hello');

// 分解开来，就是下面这样：
$('div') // 找到div元素
    .find('h3') // 选择其中的h3元素
    .eq(2) // 选择第3个h3元素
    .html('Hello'); // 将它的内容改为Hello
    .end() //退回到选中所有的h3元素的那一步
    .eq(0) //选中第一个h3元素
    .html('World'); //将它的内容改为World
```
## jQuery 如何创建元素
```javascript
let $box = $('<div class="box"></div>') // 传入标签字符串
```
## jQuery 如何移动元素
1. 插入元素内
```javascript
$box.appendTo(document.body) // 将选择的元素追加到指定元素最最后
$box.prependTo(document.body) // 追加到最前

$(document.body).append($box) // 在选择的元素的最后追加指定元素
$(document.body).prepend($box) // 最前追加指定元素
```
2. 元素外插入
```javascript
$box1.after($box2) // 插入到下个兄弟节点位置（在$box1后插入$box2）
$box2.insertAfter($box1) // 效果同上 （把$box2插入到$box1之后）

$box1.before($box2) // 插入到上一个兄弟节点位置
$box2.insertBefore($box1) // 效果同上
```

## jQuery 如何修改元素的属性
```javascript
$box.class('newClass') // 修改class属性

$box.attr('title') // 获取属性值
$box.attr('title', 'newTitle') //修改属性值
```
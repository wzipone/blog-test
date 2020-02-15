# CSS动画知识总结

## 一、动画的渲染原理

### 浏览器的大致渲染过程
1. 根据HTML构建HTML树（DOM）
2. 根据CSS构建CSS树（CSSDOM）
3. 将两个树合成为一颗渲染树（render tree）
4. Layout布局（根据文档流、盒模型、计算元素的大小和位置）
5. Paint绘制（边框颜色、文字颜色、阴影等绘制）
6. composite合成（根据层叠关系，就像PS中的图层，合并成一张图展示）

### 像素管道
#### 工作时需要了解并注意五个主要区域
这些是您拥有最大控制权的部分，也是像素至屏幕管道中的关键点：
1. JavaScript：通过JavaScript可以影响文档样式或在文档中添加删除元素
2. 样式计算：根据匹配选择器，计算出元素的CSS rules，应用规则计算每个元素的最终样式
3. 布局：只要每个元素的应用的CSS规则后，浏览器即可计算各元素占据空间大小和位置
4. 绘制：创建绘图调用的列表，然后填充像素的过程（栅格化），基本包括元素的每个可视部分，绘制一边是在多个表面（层）上完成
5. 合成：页面的各个部分可能被绘制到多层，通过合成让他们按照正确的顺序绘制到屏幕上

#### 管道运行方式 
不一定每帧都总是会经过管道每个部分的处理。实际上，不管是使用 JavaScript、CSS 还是网络动画，在实现视觉变化时，管道针对指定帧的运行通常有三种方式：
1. JS / CSS > 样式 > 布局 > 绘制 > 合成
 ![frameFull](/images/css-animation/frameFull.jpg)如果修改元素的“layout”属性，也就是改变了元素的几何属性（例如宽度、高度、左侧或顶部位置等），那么浏览器将必须检查所有其他元素，然后“自动重排”页面。任何受影响的部分都需要重新绘制，而且最终绘制的元素需进行合成
2. JS / CSS > 样式 > 绘制 > 合成
![frameNoLayout](/images/css-animation/frameNoLayout.jpg)如果修改“paint only”属性（例如背景图片、文字颜色或阴影等），即不会影响页面布局的属性，则浏览器会跳过布局，但仍将执行绘制
1. ![frameNoLayoutPaint](/images/css-animation/frameNoLayoutPaint.jpg)如果您更改一个既不要布局也不要绘制的属性，则浏览器将跳到只执行合成。这种方式开销最小

#### 两种优化CSS动画的方式
1. JS优化：使用requestAnimationFrame代替setTimeout和setInterval做动画
2. CSS优化：使用will-change或者transform做动


## 二、transition

### 一般配合tarnsform属性做动画
transform的四个常用功能
1. traslate
2. scale
3. rotate
4. skew
   
### transition用法
* 作用：补充中间帧
* 用法:transition : 属性名 时长 过渡方式 延迟
* 不是所有的属性都能产生过渡效果，比如display:none（不在渲染树中），可以使用visibility从hidden到visible做出现消失的动画

### 中间有多步的过渡动画
1. 使用多次transform，注意中中间过渡点的状态衔接，配合setTimeout或者transitionend
2. 使用animation

## 三、animation
### 声明中间帧 @keyframes
   * 使用from to
   * 使用百分比 
### animation用法
   * animation：时长 过渡方式 延迟 次数 方向 填充模式 是否暂停 动画名

## 四、css学习感悟
  把css描述为一个世界是非常恰当了，类比现实世界，有各种各样的法则和定律，现实世界就是在此基础上运转。css中有文档流、盒模型和层叠上下文等等，这些就是css世界中的法则和定律，由承载css的浏览器实现，设置的每一个样式，都按照规则展现相应的效果。


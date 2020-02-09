# 3. HTML重点标签
## 3.1 a标签
* 属性：
   * href
   * target
   * download
   * rel=noopener
* 作用：
   * 跳转到外部页面
   * 跳转到内部锚点
   * 跳转到邮箱/电话...
1. href的取值
   1. 网址
      1. https://google.com
      2. http://google.com
      3. //google.com(无协议网址，会自动选择协议)
   2. 路径
      1. /a/b/c 和 a/b/c（http的根路径为启动服务的目录）
      2. index.html 和 ./index.html
   3. 伪协议
      1. javascript:;(:;中间可写JS代码，如果什么都部写，点击a标签后页面不会有任何反应)
      2. mailtio:邮箱
      3. tel:电话号码
   4. 锚点：根据元素设置的id为锚点
2. target属性
   1. 内置的属性值
      1. _blank
      2. _self
      3. _top
      4. _parent
   2. 程序员命名的name
      1. window的name
      2. iframe的name（iframe现在用的比较少）
## 3.2 table标签
 1. 相关的标签
    1. table
    2. thead / tbody / tfoot
    3. tr / th / td
    4. 注意tr，th和td要被thead，tbody和tfoot包裹使用
 2. 相关的样式
    1. table-layout
       1. atuo（默认）：在指定table宽度的情况下，根据内容多少智能的分配列宽
       2. fixed：在指定table宽度的情况下，平均分配列宽
    2. border-collapse
    3. border-spacing
## 3.3 img标签
1. 作用：发出get请求，展示一张图片
2. 属性
   1. src：source，资源的位置
   2. alt：图片加载失败时，显示提示图片内容的文字
   3. width / height
3. 事件
   1. onload：图片加载成功触发
   2. onerror：图片加载失败触发
4. 响应式：max-width：100%（容器宽度大于图片宽度，图片按照指定的宽度显示，若容器宽度容纳不下图片的宽度，则适应容器的宽度）
5. 可替换元素
   1. 字面理解：本身没有内容的元素放在文档中占位，最终请求加载的资源会替换成为元素的内容，
   2. 一些特性
      1. 内容的渲染独立于本文档的CSS，所以内容不会受到当前文档样式影响（举例：对于img标签，设置文字的样式并不会对图片中的文字有影响）
      2. CSS只能影响内容的**位置**和**定位方式**（object-fit属性：指定内容对象的填充方式，类似于background-size；object-positon：指定内容对象的定位，类似于background-position。）
## html标签学习的感想
1. html标签有些看着很简单，但细节里会埋坑，多用多试多查资料
2. 虽然有110个标签，但是开始最主要的是掌握最常用的那些标签，分清学习的主次。
    


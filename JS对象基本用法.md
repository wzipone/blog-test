# JS 对象基本用法

## 声明对象的两种语法
1. 字面量表示，写起来简单
```javascript
let obj = {'name': 'frank', 'age': 18}
```
2. new方法，正规写法
```javascript
let obj = new Object({'name': 'frank', 'age': 18})
```

## 如何删除对象的属性
1. 写法
```javascript
delete obj.属性名 
或者
delete obj['属性名']
```
## 区分属性值为undefined 和 不含属性名
 1. 不含属性名
```javascript
'属性名' in obj === false
```
2. 含有属性名，但是值为undefined
```javascript
'属性名' in obj && obj.属性名 === undefined
```
3. 注意
```javascript
obj.属性名 === undefined 
不能判断是否为obj的属性，因为有可能obj有该属性，但是值为undefined
```

## 如何查看对象属性
### 查看属性名
1. 只查看自身的属性
```javascript
Object.keys(obj)
```
2. 查看自身和共有的属性
```javascript
console.dir(obj)
或者
Object.keys()依次打印该对象和原型链上的对象
```
3. 判断一个属性是自身的还是共有的
```javascript
obj.hasOwnProperty('属性名')
```
### 查看属性值
1. 中括号语法（注意中括号中是变量和表达式的情况）
```javascript
obj['属性名']
```
2. 点语法 
```javascript
obj.属性名
```


## 如何修改或者增加属性
1. 直接赋值
```javascript
obj.属性名 = 属性值
```
2. 批量赋值
```javascript
Object.assign(obj, {age: 18, gender: 'man'})
```
3. 修改或增加共有属性
   1. 无法通过自生修改或增加共有属性
   2. 只能在原型上修改或增加

## 'name' in obj和obj.hasOwnProperty('name') 的区别
1. 'name' in obj，自身和共有的属性都会返回true
2.  obj.hasOwnProperty('name') ，只有自身的属性会返回true
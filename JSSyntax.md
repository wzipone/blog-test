# JavaScript语法
## 表达式和语句
1. 什么是表达式和语句
   1. 表达式一般都有值 
   2. 语句可能有值也可能没值,语句一般会改变环境(声明 或 赋值)
   3. 以上连句并不绝对
2. 举例
   1. 1 + 2,就是表达式,值为3;add(1, 2)也是表达式,值为函数的返回值
   2. var a = 1,就是一条语句

## 标识符的规制
1. 标识符大小写敏感
2. 第一个字符可以是 Unicode字母(包括英文字母和其他语言的字母) $ _ 或者中文
3. 后面的字符,除了上面的还可以是数字0-9
4. JavaScript有一些保留字，不能用作标识符
5. 还有三个词虽然不是保留字，但是因为具有特别含义，也不应该用作标识符：Infinity/NaN/undefined。

## if else语句
1. 如果只有一条语句if,else if,else后可以省略花括号,但不建议省略
2. 推荐写法
```javascript
if(表达式){
    语句
}else if(表达式){
    语句
}else{
    语句
}
```
3. 次推荐写法
```javascript
function fn(){
    if(表达式){
        return 表达式
    }
    if(表达式){
        return 表达式
    }
}
```

## 循环语句

### while
* 先判断,后执行

### do while
* 先执行,后判断

### for
* 执行顺序 1-2-4-3-2-4-3...
```javascript
for( 1 ; 2 ; 3 ){
    4
}
```
### break
* 跳出最近的循环,执行下一条语句

### continue
* 跳出最近的此次循环,执行循环的下一次

## label
* 用的比较少
* 下例中,chrome会看成为对象,firefox会将foo看成标记,标记了一条语句--1
```javascript
{
    foo:1
}
```

# JS函数的执行时机

## 一、以下代码为什么会打印6个6？
```javascript
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```
1. setTimeout函数的含义是马上执行，即使参数为0
2. 马上执行，意味着完成目前的工作再执行，目前的工作就是执行完for循环
3. 在执行完for循环 i 根据作用域链找到 i的值为6
4. 最后执行6次，所以打印出来了6个6

## 二、如何让上面代码打印 0、1、2、3、4、5 的方法
1. 使用JS对for-let搭配使用的优化
```javascript
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```

2. 使用闭包，将i的值传入到手动建立的函数作用域中
```javascript
for(let i = 0; i<6; i++){
    !(function(i){
        setTimeout(()=>{
        console.log(i)
        },0)
    })(i)
}
```




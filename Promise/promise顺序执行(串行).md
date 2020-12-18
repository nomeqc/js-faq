## 实现一：
```js
function upload(name) {
    return function() {
      return new Promise((resolve,reject)=>{
        setTimeout(function() {
            console.log(name);
            resolve();
        }, 1000);
      })  
    };
}

let names = ['a', 'b', 'c'];
let promises = []
for (let name of names) {
    promises.push(upload(name));
}
let promiseObj = Promise.resolve();
for (let p of promises) {
    promiseObj = promiseObj.then(p)
}
```
每行输出间隔一秒：
```
a
b
c
```
> 特别注意：这里`upload`方法中的`return new Promise ...`要用`function(){...}`包裹

----

## 实现二：
```
function upload(name) {
    return new Promise((resolve,reject)=>{
        setTimeout(function() {
            console.log(name);
            resolve();
        }, 1000);
    })
}
const demo = async()=>{
    let names = ['a','b','c'];
    for(let name  of names) {
        let result = await upload(name);
    }
}
demo()
// demo的返回当做Promise
// demo().then(result=>{
//     console.log('输出', result);
// }
// )

```
每行输出间隔一秒：
```
a
b
c
```
> 特别注意：这里`upload`方法中的`return new Promise ...`不需要用`function(){...}`包裹，直接`return new Promise ...`即可

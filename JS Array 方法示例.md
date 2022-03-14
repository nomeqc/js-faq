# JS Array 方法示例

### Array.prototype.forEach()
```js
const array1 = ['a', 'b', 'c'];
array1.forEach((v, i, arr) => console.log(v, i, arr));
// 输出："a" 0 Array ["a", "b", "c"]
// 输出："b" 1 Array ["a", "b", "c"]
// 输出："c" 2 Array ["a", "b", "c"]
```

### Array.prototype.map()
```js
const arr = ['a', 'b', 'c'].map(item => item + 'c')
console.log(arr)
// 输出：["ac", "bc", "cc"]
```

### Array.prototype.filter()
```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const arr = words.filter(word => word.length > 6);
console.log(arr);
// 输出：["exuberant", "destruction", "present"]
```

### Array.prototype.findIndex()
```js
const index = ['a', 'b', 'c'].findIndex(item => item == 'c')
console.log(index)
// 输出：2
```

### Array.prototype.sort()
```js
[3, 1, 5 , 4, 2, 6].sort((v1, v2) => {
    // 实现升序排序。返回大于0的数 表示交换位置，返回小于0的数表示不交换位置
    return v1 - v2
})
// 输出：[1, 2, 3, 4, 5, 6]
```

### Array.prototype.every()
```js
const result = ['a', 'b', 'c'].every(item => item.length == 1)
console.log(result)
// 输出：true
```



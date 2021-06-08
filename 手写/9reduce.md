## reduce

注意事项

- 如果没有默认初始值 fn 第一个参数是 0 第二个是 1 ,
- 如果有默认初始值 fn 第一个参数是 初始值 第二个 是 数组第0个索引

```js

const list = [1, 2, 3];
Array.prototype.reduce = function (fn, initValue) {
    const arr = this;
    let index = 0;
    if (!initValue) {
        initValue = arr[index];
        index++
    }
    for(;index< arr.length; index++) {
        let tempResult = fn(initValue, arr[index], index);
        initValue = tempResult;
    }
    return initValue
}
const result = list.reduce((item, next) => {
    // debugger
    return item + next
},2)

console.log(result)

```

## 参考资料

- [手写 reduce](https://segmentfault.com/a/1190000021858714)
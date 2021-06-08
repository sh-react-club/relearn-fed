## filter

```js

Array.prototype.filter = function (fn) {
    // this 是当前数组 
    const arr = this;
    const result = [];
    for (let i =0; i< arr.length ;i ++) {
        const item = arr[i];
        const temp = fn(item, i, arr);
        if (temp) {
            result.push(item)
        }
    }
    return result
}

const list = [1,2,3];

const ding = list.filter((item) => {
    return item === 1
})


console.log(ding)

```
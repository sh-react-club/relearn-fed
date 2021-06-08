## promise


## promiseAll

实现原理 , promiseAll 接收一个数组 直到所有的 item 都成功返回 才返回，如果有一个失败 那么久失败

```js
const p1 = new Promise((resovle,reject)=>{
    setTimeout(()=>{
        resovle(1)
    },4000)
})
const p2 = new Promise((resovle,reject)=>{
    setTimeout(()=>{
        resovle(2)
    },2000)
})
const p3 = new Promise((resovle,reject)=>{
    setTimeout(()=>{
        resovle(3)
    },3000)
})
Promise.all = function (arr) {
    return new Promise((resovle, reject)=> {
        // 当所有的执行完毕返回
        let count = 0
        const len = arr.length;
        const temp = [];
        for (let i=0; i< len; i++) {
            arr[i].then(res=>{
                temp[i] = res;
                if (++count === len) {
                    resovle(temp)
                }
            }).catch(e=>{
                reject(e)
            })
        }
    })
}

```

## Promis finally


```js

Promise.prototype.finally = function (callback) {
    return this.then(
        value  => Promise.resolve(callback()).then(() => value),
        reason => Promise.resolve(callback()).then(() => { throw reason })
    );
};

p2.then(result => {console.log(result)})
.catch(error => {console.log(error)})
.finally(() => {console.log('123')});

```
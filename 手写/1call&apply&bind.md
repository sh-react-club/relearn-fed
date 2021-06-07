## apply

```js
Function.prototype.myApply = function (context, args) {
    context.fn = this;
    context.fn(...args)
    delete context.fn
}

var foo = {
     value: 1
};

function bar(name,age) {
    this.name = name;
    this.age = age;
    console.log(this.value);
    console.log(this.name);
    console.log(this.age);
}

bar.myApply(foo, ['dingsheng', 20]);

```

## call 


```js


Function.prototype.myCall = function (context, ...args) {
    context.fn = this;
    context.fn(...args)
    delete context.fn
}

var foo = {
     value: 1
};

function bar(name,age) {
    this.name = name;
    this.age = age;
    console.log(this.value);
    console.log(this.name);
    console.log(this.age);
}

bar.myCall(foo, 'dingsheng', 20)

```

## bind

```js

// 返回一个函数 第二次调用的时候在执行
// 缓存执行函数
// 第二次执行的时候 调用 apply 或者 call
Function.prototype.Mybind = function (context, ...args) {
    const _this = this; // bar 函数
    return function (...params) {
        _this.call(context,...args, ...params)
    }
}

var foo = {
     value: 1
};

function bar(name,age) {
    this.name = name;
    this.age = age;
    console.log(this.value);
    console.log(this.name);
    console.log(this.age);
}

const result = bar.Mybind(foo,'ding')
result( 10)

```
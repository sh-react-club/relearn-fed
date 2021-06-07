## new 

```js

 // new 的实现原理
    // 1 创建一个空对象
    // 2 把空对象的 __proto__ 指向构造函数的 prototype 
    // 3 拷贝构造函数的属性 
    // 4 返回这个对象
    // 5 判断构造函数 

function Otaku (name, age) {
    this.strength = 60;
    this.age = age;

    return {
        name: name,
        habit: 'Games'
    }
}


function objectFactory() {
    var obj = new Object(),
    // 从数组中删除第一个  并且返回第一个参数
    Constructor = [].shift.call(arguments);
    obj.__proto__ = Constructor.prototype;
    const ref = Constructor.apply(obj, arguments);
    console.log(ref)
    return obj;
};

var person = objectFactory(Otaku, 'Kevin', '18')

console.log(person.name) // Kevin
console.log(person.age) // Games
console.log(person.strength) // 60

person.sayYourName(); // I am Kevin

```
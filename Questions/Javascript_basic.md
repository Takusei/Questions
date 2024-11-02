# Javascript Basic

### Q: Closures （闭包）
```
闭包就是能够读取其他函数内部变量的函数，或者子函数在外调用，
子函数所在的父函数的作用域不会被释放。

function init() {
  var name = "Mozilla"; // name 是 init 创建的局部变量
  function displayName() {
    // displayName() 是内部函数，它创建了一个闭包
    console.log(name); // 使用在父函数中声明的变量
  }
  displayName();
}
init();
```

### Callback Hell
```
Use promise, generator, async/await to solve

```

### Promise
```
Promise.all、Promise.race、Promise.any的区别
all： 成功的时候返回的是一个结果数组，而失败的时候则返回最先被reject失败状态的值。
The Promise.all() static method takes an iterable of promises as input and returns a single Promise. 
This returned promise fulfills when all of the input's promises fulfill (including when an empty iterable is passed), 
with an array of the fulfillment values. It rejects when any of the input's promises rejects, with this first rejection reason.

race： 哪个结果获得的快，就返回那个结果，不管结果本身是成功状态还是失败状态。
any： 返回最快的成功结果，如果全部失败就返回失败结果。


```

### addEventListener
```
addEventListener(type, listener)
addEventListener(type, listener, options)
addEventListener(type, listener, useCapture)

my_element.addEventListener("click", function (e) {
  console.log(this.className); // logs the className of my_element
  console.log(e.currentTarget === this); // logs `true`
});
```

### 前端事件流
```
事件捕获阶段
处于目标阶段
事件冒泡阶段

先捕获，后冒泡
```

### What did `new` do?
```
new 操作符新建了一个空对象，这个对象原型指向构造函数的prototype，执行构造函数
后返回这个对象。
```

### `this`
```
The value of `this` depends on in which context it appears: function, class, or global.

通过apply 和call 改变函数的this 指向，他们两个函数的第一个参数都是一样的表示要
改变指向的那个对象，第二个参数，apply 是数组，而call 则是arg1,arg2...这种形式。通
过bind 改变this 作用域会返回一个新的函数，这个函数不会马上执行。

let obj = {
  name: this.name,
  objAge: this.age,
  myLove: function (fm, t) {
    console.log(this.name + "年龄" + this.age, "来自" + fm + "去往" + t);
  },
};
let obj1 = {
  name: "huang",
  age: 22,
};
obj.myLove.call(obj1, "达州", "成都"); //huang年龄22来自达州去往成都
obj.myLove.apply(obj1, ["达州", "成都"]); //huang年龄22来自达州去往成都

obj.myLove.bind(obj1, "达州", "成都")(); // (注意前面有个调用)huang年龄22来自达州去往成都

```

### 异步加载JS 的方法
```
defer：defer 特性告诉浏览器不要等待脚本。相反，浏览器将继续处理 HTML，构建 DOM。
脚本会“在后台”下载，然后等 DOM 构建完成后，脚本才会执行。
<script defer src="xxx"/>


async: async 脚本会在后台加载，并在加载就绪时运行。DOM 和其他脚本不会等待它们，它们也不会等待其它的东西。
async 脚本就是一个会在加载完成时执行的完全独立的脚本。
<script async src="https://google-analytics.com/analytics.js"></script>

同时存在defer 和async，那么defer 的优先级比较高，脚本将在页面完成时执行。
创建script 标签，插入到DOM 中
```

### Js Garbage Collection
```
必要性：
由于字符串、对象和数组没有固定大小，所有当他们的大小已知时，才能对他
们进行动态的存储分配。JavaScript 程序每次创建字符串、数组或对象时，解释器都必
须分配内存来存储那个实体。只要像这样动态地分配了内存，最终都要释放这些内存以
便他们能够被再用，否则，JavaScript 的解释器将会消耗完系统中所有可用的内存，造
成系统崩溃。

JavaScript 的解释器可以检测到何时程序不再使用一个对象
了，当他确定了一个对象是无用的时候，他就知道不再需要这个对象，可以把它所占用
的内存释放掉了。

There are mainly 2 methods:

1. Reference-counting garbage collection:
(Note: No modern JavaScript engine uses reference-counting for garbage collection anymore.)
引用计数法的意思就是每个值没引用的次数，
当声明了一个变量，并用一个引用类型的值赋值给改变量，则这个值的引用次数为1,；
相反的，如果包含了对这个值引用的变量又取得了另外一个值，则原先的引用值引用次
数就减1，当这个值的引用次数为0 的时候，说明没有办法再访问这个值了，因此就把
所占的内存给回收进来，这样垃圾收集器再次运行的时候，就会释放引用次数为0 的这
些值。
用引用计数法会存在内存泄露，下面来看原因：
function problem() {
var objA = new Object();
var objB = new Object();
objA.someOtherObject = objB;
objB.anotherObject = objA;
}
在这个例子里面，objA 和objB 通过各自的属性相互引用，这样的话，两个对象的引用
次数都为2，在采用引用计数的策略中，由于函数执行之后，这两个对象都离开了作用
域，函数执行完成之后，因为计数不为0，这样的相互引用如果大量存在就会导致内存
泄露。

2. Mark-and-sweep algorithm:
This algorithm reduces the definition of "an object is no longer needed" to "an object is unreachable".

This algorithm assumes the knowledge of a set of objects called roots. 
In JavaScript, the root is the global object. 
Periodically, the garbage collector will start from these roots, find all objects that are referenced from these roots, 
then all objects referenced from these, etc. 
Starting from the roots, the garbage collector will thus find all reachable objects and collect all non-reachable objects.
```

### eval 是做什么的
```
它的功能是将对应的字符串解析成JS 并执行，应该避免使用JS，因为非常消耗性能（2
次，一次解析成JS，一次执行）
console.log(eval('2 + 2'));
// Expected output: 4

console.log(eval(new String('2 + 2')));
// Expected output: 2 + 2

console.log(eval('2 + 2') === eval('4'));
// Expected output: true

console.log(eval('2 + 2') === eval(new String('2 + 2')));
// Expected output: false
```

### CommonJs, AMD (Asynchronous Module Definition), ES6
```
commonjs:

//payments.js
var customerStore = require('store/customer'); // import module
//store/customer.js
function customerStore(){
    return customers.get('store);
}
modules.exports = customerStore;

AMD:
AMD was born as CommonJS wasn’t suited for the browsers early on. As the name implies, it supports asynchronous module loading.

define(['module1', ',module2'], function(module1, module2) {
  console.log(module1.setName());
});
The function is called only when the requested modules are finished loading. 


ES6:
//------ lib.js ------
export const sqrt = Math.sqrt;
export function square(x) {
    return x * x;
}
export function diag(x, y) {
    return sqrt(square(x) + square(y));
}
//------ main.js ------
import { square, diag } from 'lib';
console.log(square(11)); // 121
console.log(diag(4, 3)); // 5

```

### 实现一个once 函数，传入函数参数只执行一次
```
var once = function(fn) {
    let flag = false
    return function(...args){
        if (flag) {
            return undefined
        }
        flag = true
        return fn(...args)
    }
};
/**
 * let fn = (a,b,c) => (a + b + c)
 * let onceFn = once(fn)
 *
 * onceFn(1,2,3); // 6
 * onceFn(2,3,6); // returns undefined without calling fn
 */

```

### 如何实现一个私有变量，用getName 方法可以访问，不能直接访问
```
1. closure
function createPerson(name) {
  let _name = name; // 私有变量
  return {
    getName: function() {
      return _name;
    }
  };
}

const person = createPerson('Alice');
console.log(person.getName()); // 输出: Alice
console.log(person._name);     // 输出: undefined

2. 使用 ES6 私有字段（Private Fields）
class Person {
  #name; // 私有字段

  constructor(name) {
    this.#name = name;
  }

  getName() {
    return this.#name;
  }
}

const person = new Person('David');
console.log(person.getName()); // 输出: David
console.log(person.#name);     // 语法错误，无法直接访问私有字段
```

### ==和===、以及Object.is 的区别
```
Object.is 主要的区别就是+0！=-0 而NaN==NaN
```

### setTimeout vs setInterval
```
setTimeout 用于在指定的延迟时间后执行一次函数。
setTimeout(function, delay, arg1, arg2, ...);


setInterval 用于按照指定的时间间隔周期性地执行函数，直到被明确取消。
setInterval(function, interval, arg1, arg2, ...);

取消方式：
setTimeout：使用 clearTimeout(timeoutId) 取消。
setInterval：使用 clearInterval(intervalId) 取消。

```
### Js 是单线程的，那么它是怎么处理异步操作的？
```
JavaScript 是一门单线程语言，即在同一时间只能执行一个任务。然而，它通过事件循环（Event Loop）机制有效地处理异步操作，如网络请求、定时器和用户交互等，从而避免阻塞主线程。

事件循环机制

事件循环是 JavaScript 处理异步任务的核心。它协调调用栈（Call Stack）和任务队列（Task Queue）之间的关系，确保异步任务在适当的时机执行。

主要组件：

1. 调用栈（Call Stack）：存储当前正在执行的函数。当函数被调用时，会被压入栈中；执行完毕后，从栈中弹出。

2. Web APIs：由浏览器提供的功能，如 setTimeout、HTTP 请求和 DOM 事件等。当执行异步操作时，这些任务会被交由浏览器处理，而非阻塞主线程。

3. 任务队列（Task Queue）：

  宏任务队列（Macro Task Queue）：包含如 setTimeout、setInterval 和 I/O 操作等任务。
  微任务队列（Micro Task Queue）：包含如 Promise 回调和 MutationObserver 等任务。微任务的优先级高于宏任务。

执行流程：

同步代码直接在调用栈中执行。
异步操作由 Web APIs 处理，完成后将回调函数放入相应的任务队列。
事件循环首先检查调用栈是否为空，若为空，则依次处理微任务队列中的所有任务，然后再处理宏任务队列中的第一个任务。
```

### Promise 代码的执行顺序
```
new Promise(function (resolve, reject) {
  console.log(2);
  resolve();
})
  .then(function () {
    console.log(3);
  })
  .then(function () {
    console.log(4);
  });

process.nextTick(function () {
  console.log(5);
});

console.log(6);

//输出2,6,5,3,4,1

同步任务：立即执行主线程上的同步代码。
  console.log(2)：输出 2。
  console.log(6)：输出 6。

微任务（Microtasks）：在当前事件循环结束前执行的任务，包括 process.nextTick 和 Promise 的回调。
  process.nextTick 的回调：输出 5。
  Promise 的第一个 then 回调：输出 3。
  Promise 的第二个 then 回调：输出 4。

宏任务（Macrotasks）：在下一个事件循环中执行的任务，如 setTimeout。

setTimeout 的回调：输出 1。

script(主程序代码)—>process.nextTick—>Promises...——>setTimeout——>setInterval——>setImmediate——> I/O——>UI rendering

sync task => nextTicket => promise.then()/promise resolve => setTimeout

```

### Deep Copy
```
1. Using JSON.parse() and JSON.stringify():

const original = { a: 1, b: { c: 2 } };
const copy = JSON.parse(JSON.stringify(original));

2. Using Recursive Function:

function deepClone(obj, hash = new WeakMap()) {
  if (obj === null || typeof obj !== 'object') return obj;
  if (hash.has(obj)) return hash.get(obj); // Handle circular references

  const clone = Array.isArray(obj) ? [] : {};
  hash.set(obj, clone);

  for (const key in obj) {
    if (obj.hasOwnProperty(key)) {
      clone[key] = deepClone(obj[key], hash);
    }
  }
  return clone;
}

const original = { a: 1, b: { c: 2 } };
const copy = deepClone(original);

```

### 数组去重
```
Array.from(new Set(array))
```

### How to check if it's an array?
```
DON't use typeof => will return object

Use Array.isArray() or instanceof

const arr = [1, 2, 3];
console.log(arr instanceof Array);
```

### JS 实现跨域
```
JSONP：适用于仅需 GET 请求且后端支持的简单场景。 

CORS：适用于后端可配置响应头的场景，支持多种请求方法。 (Access-Control-Allow-Origin)

代理服务器：适用于前后端分离且需要统一代理的场景。

服务器端设置跨域头：适用于后端代码可修改的项目。
```
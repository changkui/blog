## Promise 使用、原理以及实现过程



### 1.什么是 Promise

promise 是目前 js 异步编程的主流解决方案，遵循 Promises/A+ 方案。

#### 2.Promise 原理简析

（1） promise 本身相当于一个状态机，拥有三种状态

- pending
- fulfilled
- rejected

一个 promise 对象初始化时的状态是 pending，调用了 resolve 后会将 promise 的状态扭转为 fulfilled，调用 reject 后会将 promise 的状态扭转为 rejected，这两种扭转一旦发生便不能再扭转该 promise 到其他状态。

（2）promise 对象原型上有一个 then 方法，then 方法会返回一个新的 promise 对象，并且将回调函数 return 的结果作为该 promise resolve 的结果，then 方法会在一个 promise 状态被扭转为 fulfilled 或 rejected 时被调用。then 方法的参数为两个函数，分别为 promise 对象的状态被扭转为 fulfilled 和 rejected 对应的回调函数


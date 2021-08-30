## js操作数组方法

#### 1.concat()

concat() 方法用于连接两个或多个数组。

**注释：**该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。

```js
var arr = [1, 9, 3, 8, 5, 3];
var concatVal = arr.concat([3, 3, 3, 3]);
console.log(arr, concatVal);	// [3, 5, 8, 3, 6, 9, 1] [3, 5, 8, 3, 6, 9, 1, 3, 3, 3, 3]
```

#### 2.join()

join() 方法用于把数组中的所有元素放入一个字符串。

元素是通过指定的分隔符进行分隔的。

```js
var arr = [1, 9, 3, 8, 5, 3];
var join = arr.join(',');
console.log(arr, join);	// [1, 9, 3, 8, 5, 3] 1,9,3,8,5,3
```

#### 3.push()

push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。

```js
var arr = [1, 9, 3, 8, 5, 3];
var push = arr.push(2)
console.log(arr, push);	//[1, 9, 3, 8, 5, 3, 2]  7
```

#### 4.pop()

pop() 方法用于删除并返回数组的最后一个元素。

```js
var arr = [1, 9, 3, 8, 5, 3];
var pop = arr.pop();
console.log(arr, pop);	// [3, 5, 8, 3, 6, 9] 1
```

#### 5.shift()

shift() 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。

```js
var arr = [1, 9, 3, 8, 5, 3];
var shift = arr.shift();
console.log(arr, shift);	// [9, 3, 8, 5, 3, 2] 1
```

#### 6.unshift()

unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。

```js
var arr = [1, 9, 3, 8, 5, 3];
var unshift = arr.unshift(1, 2, 3);
console.log(arr, unshift);	// [1, 2, 3, 9, 3, 8, 5, 3, 2]  9
```

#### 7.slice()

slice() 方法可从已有的数组中返回选定的元素。

```js
var arr = [1, 9, 3, 8, 5, 3];
var slice = arr.slice(3, 5);
console.log(arr, slice);	// [3, 5, 8, 3, 6, 9, 1] [3, 6]
```

#### 8.splice()

splice() 方法向/从数组中添加/删除项目，然后返回被删除的项目。

**注释：**该方法会改变原始数组。

```js
arrayObject.splice(index,howmany,item1,.....,itemX)
```

| 参数              | 描述                                                         |
| :---------------- | :----------------------------------------------------------- |
| index             | 必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。 |
| howmany           | 必需。要删除的项目数量。如果设置为 0，则不会删除项目。       |
| item1, ..., itemX | 可选。向数组添加的新项目。                                   |

```js
var arr = [1, 9, 3, 8, 5, 3];
var splice = arr.splice(2, 1, 6);	// 从下标为2开始删除1个数[3], 并加入6到下标2的位置后面的往后移
console.log(arr, splice);	// [1, 9, 6, 8, 5, 3] [3]
```

#### 9.sort()

sort() 方法用于对数组的元素进行排序。

**注释：**该方法会改变原始数组。

```js
var arr = [1, 9, 3, 8, 5, 3];
var sorta = arr.sort();
console.log(arr, sorta);	// [1, 3, 3, 5, 8, 9] [1, 3, 3, 5, 8, 9]

var sortb = arr.sort(function(a, b) {
  return b - a;
});
console.log(arr, sortb);	// [9, 8, 5, 3, 3, 1] [9, 8, 5, 3, 3, 1]
```

#### 10.reverse()

reverse() 方法用于颠倒数组中元素的顺序。

**注释：**该方法会改变原来的数组，而不会创建新的数组。
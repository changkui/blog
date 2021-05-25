## ES6数组方法

- ES6数组方法有 **forEach**, **map** , **filter**, **find**, **every**, **some**, **reduce**.

### forEach

```js
//ES5遍历
var colors=['red','green','yellow'];

for(var i=0;i<colors.length;i++){
  console.log(colors[i])
}

//ES6遍历
colors.forEach(function(color){
  console.log(color)
})
```

- 迭代器函数首先把数组每个值依次循环，直到最后一个。forEach是通过**回调函数**来提供参数的。回调函数也是一种闭包，所以每个回调函数都有自己的**私有作用域**，互不影响，内部变量不会及时释放。如果在闭包中**return**的话，也只是在当前函数中返回，而且在forEach中其他闭包函数中还是存在的，所以会出现**return**中是没办法结束循环的。

```js
let arr=[1,2,3];
arr.forEach(function(value,key,arr){
  console.log(value);  //-->1,2,3
  //console.log(key);  //-->0,1,2
  //console.log(arr); //-->arr
});
```

- 可以看出他在函数中有三个参数，**value** , **key**, **arr**.
- 其中函数也可以写在外部

```js
let arr = [1, 2, 3];
function arr(value,key,arr){
  console.log(value);  //-->1,2,3
  //console.log(key);  //-->0,1,2
  //console.log(arr); //-->arr
}
arr.forEach(arr)
```

### map

- 场景1 假定有一个数值数组(A),将A数组中的值以双倍的形式放到B数组中

```js
var numbers=[1, 2, 3];
var numbersA=[];

// ES5
for (var i=0; i<numbers.length; i++){
  numbersA.push(numbers[i]*2)
};
console.log(numbersA);

//ES6 map
var numbersA = numbers.map(function(number){
  return number*2
});

console.log(numbersA);

//forEach
numbersA.forEach(function(number){
  console.log(number)
})
```

- 场景2 假定有一个对象数组（A），将A数组中对像某个属性的值存储到B数组中

```js
var cars=[
  {model:"buick", price:"cheap"},
  {model:"bmw", price:"expensive"},
];

var prices = cars.map(function(car){
  return cars.price
});

console.log(prices)
```

- 原理：把数组中的值放入迭代器函数中，然后**return**结果出来，map需要返回值，如果不给**return**，默认返回的是undefined。map返回的是**新数组**。

### filter

- 场景1 假定有一个对象数组（A），获取数组中指定类型的对象放到B数组中

```js
let products = [
  {name:'cucumber', type:'vegetable'},
  {name:'banana', type:'fruit'},
  {name:'celery', type:'vegetable'},
  {name:'orange', type:'fruit'},
];

//ES5
let filteredProducts = [];

for (var i=0;i<products.length; i++){
  if(products[i].type == "fruit"){
    filteredProducts.push(products[i])
  }
};
console.log(filteredProducts);

//ES6
let filter2=products.filter(function(product){
  return product.type=="vegetable"
});
```

- 原理：把数组中的值放入迭代器函数中，如果与匹配的内容相等，**return**true,把不匹配的过滤出去。
- 场景2 假定有一个对象数组A，过滤多个满足条件对象

```js
let product2=[
  {name:'cucumber',type:'vegetable',price:5},
  {name:'banana',type:'fruit',price:5},
  {name:'celery',type:'vegetable',price:12},
  {name:'orange',type:'fruit',price:5},
];

let newProduct=product2.filter(function(product){
  return product.type==="vegetable" && product.price > 0  && product.price < 10 
});
console.log(newProduct);
```

- 场景3 假定有两个数组AB，根据A中id值，过滤掉B数组中不符合的数据。

```js
let post={id:4,title:"javascript"};

let comments=[
  {postId:4,content:"vue"},
  {postId:3,content:"vue2.0"},
  {postId:2,content:"vue3.0"},
  {postId:2,content:"Node.js"}
];

function commentForPost(post,comments){
  return comments.filter(function(comment){
    return comment.postId==post.id
  });
};

console.log(commentForPost(post,comments));
```

### find

- 场景1 假定有一个对象数组A，找到符合条件的对象

```js
let users=[
  {name:"jill"},
  {name:"tome"},
  {name:"bill"}
];

let user;

//ES5
for(var i=0;i<users.length;i++){
  if(users[i].name=="tome"){
    user=users[i];
    break;//找到不会执行后面的
  }
};

//ES6

user=users.find(function(user){
  return user.name=="tome";
})
```

- 场景2 假定有一个对象数组A，根据指定对象的条件找到数组中符合条件的对象

```js
let posts=[
  {id:3,title:"node.js"},
  {id:4,title:"vue.js"}
];

let comment={id:3,content:"hello word"};

function postForComment(posts,comment){
  return posts.find(function(post){
    return post.id==comment.id;
  })
};
```

### every (一假即假 ) some (一真即真)

- 场景1 计算对象数组中每个电脑的操作系统是否可用，大于16位操作系统表示可用，否则不可用

```js
let computers=[
  {name:"Apple",ram:16},
  {name:"IBM",ram:4},
  {name:"Acer",ram:32},
];

var everyComputers=true;
var someComputers=false;

//ES5
for(var i=0;i<computers.length;i++) {
  var computer=computers[i];
  console.log(computer.ram)
  if(computer.ram < 16) {
    everyComputers=false
  } else {
    someComputers=true
  }
};

//ES6
var every = computers.every(function(computer){
  return computer.ram>16
});

console.log(every);

var some = computers.some(function(computer){
  return computer.ram>16
});

console.log(some);
```

- 场景2 假定有一个注册页面，判断所有input内容长度是否大于0

```js
function Filed(value){
  this.value=value;
};

Filed.prototype.validate=function(){
  return this.value.length>0;
}


var username=new Filed("");
var telephone=new Filed("18282828282828");
var email = new Filed("LonJin_up@163.com");

console.log(username.validate());
console.log(telephone.validate());

var fields=[username,telephone,email];

var formIsValid = fields.every(function(field){
  return field.validate()
});

if(formIsValid) {
  console.log("注册成功")
} else {
  console.log("注册失败") 
}
```

### reduce

- 场景1，计算数组中所有值的总和

```js
//ES5
var numbers=[10,20,30];
var sum=0;

for (var i=0; i < numbers.length; i++){
  sum += numbers[i];
}

console.log(sum);


//ES6
var sumValue = numbers.reduce(function(sum2,number2){
  console.log(sum2);//第一个参数需要初始化，所以打印出来第一个是0
  return sum2+number2
}, 0);

console.log(sumValue);
```

- 场景2 将数组中对象的某个属性抽离到另外一个数组中

```js
var primaryColor=[
  {color:'red'},
  {color:'yellow'},
  {color:'blue'},
];

var color=primaryColor.reduce(function(previous,primaryColor){
  previous.push(primaryColor.color);
  return previous
}, []);

console.log(color)
```

- 场景3 判断字符串中括号是否对称

```js
function balanceParens(string){
  return !string.split("").reduce(function(previous,char){
    if(previous < 0) {
      return previous
    }

    if (char=="(") {
      return ++previous
    }

    if (char==")") {
      return --previous
    }

    return previous
  }, 0);
}
console.log(balanceParens("(((())))"))
```
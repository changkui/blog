数组去重
=======

Array类型并没有提供去重复的方法，如果要把数组的重复元素干掉，那得自己想办法：

方法一：ES6方法：
----------
```js
var arr = [2, 3, 5, 4, 5, 2, 2, '5'];
var s = new Set();
arr.map((item,index) => {
  s.add(item)
})
var temp = [];
for(var i of s) {
  temp.push(i)
}
console.log(temp)
```
得到结果  [ 2, 3, 5, 4, '5' ]方法很简单，不得不说es6是大势所趋啊，也希望各大浏览器厂商赶紧支持起来！

方法二：利用indexOf方法；
----------------
```js
var aa = [1, 3, 5, 4, 3, 3, 1, 4];
function arr(arr) {
	var result = []
	for(var i = 0; i < arr.length; i++){
		if(result.indexOf(arr[i]) == -1){
			result.push(arr[i])
		}
	}
	console.log(result)
}            
arr(aa)
```
方法三：
----
```js
function unique(arr) {
	var result = [], isRepeated;
	for (var i = 0, len = arr.length; i < len; i++) {
		isRepeated = false;
		for (var j = 0, len = result.length; j < len; j++) {
			if (arr[i] == result[j]) {   
				isRepeated = true;
				break;
			}
		}
		if (!isRepeated) {
			result.push(arr[i]);
		}
	}
	return result;
}
```
方法四：
----

总体思路是把数组元素逐个搬运到另一个数组，搬运的过程中检查这个元素是否有重复，如果有就直接丢掉。从嵌套循环就可以看出，这种方法效率极低。我们可以用一个hashtable的结构记录已有的元素，这样就可以避免内层循环。恰好，在Javascript中实现hashtable是极为简单的，改进如下：
```js
function unique(arr) {
	var result = [], hash = {};
	for (var i = 0, elem; (elem = arr[i]) != null; i++) {
		if (!hash[elem]) {
			result.push(elem);
			hash[elem] = true;
		}
	}
	return result;
}
```
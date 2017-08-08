#### 基本数据类型
1. JavaScript在设计时，有两种比较运算符：  
> 第一种是 == 比较，它会自动转换数据类型再比较，很多时候，会得到非常诡异的结果；  
第二种是 === 比较，它不会自动转换数据类型，如果数据类型不一致，返回false，如果一致，再比较。  
由于JavaScript这个设计缺陷，不要使用 == 比较，始终坚持使用 === 比较。
2. NaN这个特殊的Number与所有其他值都不相等，包括它自己：
```
NaN === NaN; // false
```
> 唯一能判断NaN的方法是通过isNaN()函数：
```
isNaN(NaN); // true
```
3. 浮点数的相等比较：
```
1 / 3 === (1 - 2 / 3); // false
```
> 这不是JavaScript的设计缺陷。浮点数在运算过程中会产生误差，因为计算机无法精确表示无限循环小数。要比较两个浮点数是否相等，只能计算它们之差的绝对值，看是否小于某个阈值：
```
Math.abs(1 / 3 - (1 - 2 / 3)) < 0.0000001; // true
```

#### 数组
1. slice
> slice()就是对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array：
```
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
arr.slice(3); // 从索引3开始到结束: ['D', 'E', 'F', 'G']
```
2. push和pop
> push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除：
```
var arr = [1, 2];
arr.push('A', 'B'); // 返回Array新的长度: 4
arr; // [1, 2, 'A', 'B']
arr.pop(); // pop()返回'B'
arr; // [1, 2, 'A']
arr.pop(); arr.pop(); arr.pop(); // 连续pop 3次
arr; // []
arr.pop(); // 空数组继续pop不会报错，而是返回undefined
arr; // []
```
3. unshift和shift
> unshift()向Array的头部添加若干元素，shift()则把Array的最第一个元素删除：
```
var arr = [1, 2];
arr.unshift('A', 'B'); // 返回Array新的长度: 4
arr; // ['A', 'B', 1, 2]
arr.shift(); // 'A'
arr; // ['B', 1, 2]
arr.shift(); arr.shift(); arr.shift(); // 连续shift 3次
arr; // []
arr.shift(); // 空数组继续shift不会报错，而是返回undefined
arr; // []
```
4. sort
> sort()可以对当前的Array进行排序，它会直接修改当前Array的元素位置，直接调用时，按照默认顺序排序：
```
var arr = ['B', 'C', 'A'];
arr.sort();
arr; // ['A', 'B', 'C']
```
5. reverse
> reverse()把整个Array的元素顺序反转
```
var arr = ['one', 'two', 'three'];
arr.reverse(); 
arr; // ['three', 'two', 'one']
```
6. splice
> splice()可以从指定的索引开始删除若干元素，然后从该位置添加若干元素：
```
var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
// 从索引2开始删除3个元素,然后再添加两个元素:
arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
// 只删除,不添加:
arr.splice(2, 2); // ['Google', 'Facebook']
arr; // ['Microsoft', 'Apple', 'Oracle']
// 只添加,不删除:
arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
```
7. concat
> concat()把当前的Array和另一个Array连接起来，并返回一个新的Array
```
var arr = ['A', 'B', 'C'];
var added = arr.concat([1, 2, 3]);
added; // ['A', 'B', 'C', 1, 2, 3]
arr; // ['A', 'B', 'C']
```
> 请注意，concat()方法并没有修改当前Array，而是返回了一个新的Array。  

> 实际上，concat()方法可以接收任意个元素和Array，并且自动把Array拆开，然后全部添加到新的Array里：
```
var arr = ['A', 'B', 'C'];
arr.concat(1, 2, [3, 4]); // ['A', 'B', 'C', 1, 2, 3, 4]
```
8. join
> join()把当前的Array每个元素都用指定的字符串连接起来，然后返回连接后的字符串：
```
var arr = ['A', 'B', 'C', 1, 2, 3];
arr.join('-'); // 'A-B-C-1-2-3'
```
> 如果Array的元素不是字符串，将自动转换为字符串后再连接。





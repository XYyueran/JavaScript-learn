# JavaScript learn
# [内容参考来源](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/00143449917624134f5c4695b524e81a581ab5a222b05ec000)
>## 入门
>>### 快速入门
+ JavaScript代码可以放在网页的任何地方，或者通过<script>标签的src引用至html中，同一个页面可以引用多个JavaScript文件，按照引用顺序执行JavaScript文件。
+ 编译器:vscode、sublime、notepad++（仅window平台），不推荐使用记事本或者word编写。
+ 浏览器运行JavaScript需要依托与页面
+ 以谷歌浏览器为例，随便打开一个网页，然后点击菜单“查看(View)”-“开发者(Developer)”-“开发者工具(Developer Tools)”。先点击“控制台(Console)“，在这个面板里可以直接输入JavaScript代码，按回车后执行。例如输入console.log(2333);即为控制台输入2333。
>>### 基本语法
+ 语法与java类似，语句结束添加“;”，但是也不是强制要求添加。浏览器引擎在执行JavaScript代码的时候会自动补上“；”
+ 缩进不是JavaScript语法要求必须的，但缩进有助于我们理解代码的层次
+ 以"//"开头直到行末的字符被视为行注释，注释是给开发人员看到，JavaScript引擎会自动忽略。或者多行注释则采用“/\*XXXX\*/”
+ javaScript严格区分大小写
>>### 数据类型
+ Number:JavaScript不区分整数和浮点数，统一用Number表示。例如1123；0.255；1.235e3；-55；NaN；Infinity；Number可以直接进行四则运算。
+ 字符串:使用单引号（“''”）或者双引号(“""”)包裹。"asd"内容为a，s，d三个字符。
+ 布尔值:布尔值和布尔代数的表示完全一致，一个布尔值只有true、false两种值，要么是true，要么是false，可以直接用true、false表示布尔值。运算包括比较运算，与或非运算。比较运算中== 和=== 相区别，==只是比较值相等，===则还需要比较类型相等。
+ null:null表示一个“空”的值，它和0以及空字符串''不同，0是一个数值，''表示长度为0的字符串，而null表示“空”。
+ undefined: undefined表示值未定义
+ 数组:数组是一组按顺序排列的集合，集合的每个值称为元素。数组用[]表示，元素之间用,分隔。例如new Array(1,2,3)。索引从0开始。完整示例 var arr = [1, 2, 3.14, 'Hello', null, true];
arr[0]; // 返回索引为0的元素，即1
arr[5]; // 返回索引为5的元素，即true
arr[6]; // 索引超出了范围，返回undefined
+ 对象:JavaScript的对象是一组由键-值组成的无序集合，var person = {name: 'Bob', age: 20,tags: ['js', 'web', 'mobile'], city: 'Beijing',hasCar: true,zipcode: null};JavaScript对象的键都是字符串类型，值可以是任意数据类。获取则通过类似person.name获取，person.name值为‘Bob’
>>### 变量
+ 变量的概念基本上和初中代数的方程变量是一致的，只是在计算机程序中，变量不仅可以是数字，还可以是任意数据类型；变量在JavaScript中就是用一个变量名表示，变量名是大小写英文、数字、$和_的组合，且不能用数字开头。变量名也不能是JavaScript的关键字（尽量不要使用中文）
+ strict模式: JavaScript在设计之初，为了方便初学者学习，并不强制要求用var申明变量。这个设计错误带来了严重的后果：如果一个变量没有通过var申明就被使用，那么该变量就自动被申明为全局变量：在JavaScript文件头部书写'use strict';即为启用该模式。在strict模式下运行的JavaScript代码，强制通过var申明变量，未使用var申明变量就使用的，将导致运行错误。
>>字符串
+ 可以通过+号对多个字符串进行拼接。
+ 可以通过类数组操作获取字符串长度和每个位置的字符。
+ toUpperCase-转换为大写；toLowerCase-转换为小写；indexOf-搜索指定字符串出现的位置；substring-返回指定索引区间的子串
>>数组
+ indexOf-与String类似，Array也可以通过indexOf()来搜索一个指定的元素的位置
+ slice-对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array（不会破坏原有数组）。第一个参数为起始索引，第二个参数为结束索引（不包括结束索引），如果没有第二个参数，则默认到最后索引。如果不写任何参数，则完全获取截取，相当与复制
+ push和pop-push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除掉。会破坏原有数组。
+ unshift和shift
+ sort-sort()可以对当前Array进行排序，它会直接修改当前Array的元素位置，直接调用时，按照默认顺序排序。会破坏原有数组
+ reverse-将内部元素反转。会破坏原有数组
+ splice-splice()方法是修改Array的“万能方法”，它可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素：
	>* var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
// 从索引2开始删除3个元素,然后再添加两个元素:
	>* arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
	>* arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
// 只删除,不添加:
	>* arr.splice(2, 2); // ['Google', 'Facebook']
	>* arr; // ['Microsoft', 'Apple', 'Oracle']
// 只添加,不删除:
	>* arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
	>* arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
+ concat-concat()方法把当前的Array和另一个Array连接起来，并返回一个新的Array：
+ join-join()方法是一个非常实用的方法，它把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串
>>对象
+ 
+ JavaScript的对象是一种无序的集合数据类型，它由若干键值对组成。
+ delete-删除属性
+ in-检测是否拥有某一属性，可以用in操作符。包括继承的属性
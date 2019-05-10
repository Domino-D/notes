#### 变量定义与扩展

Dart数字变量定义

```dart
var a = 1;
num b = 1;
int c = 2; // 整型
double d = 3.4; // 浮点型
```



Dart字符串变量定义

```dart
var a = '456';
String b = '123';
```



Dart布尔值变量定义与扩展

```dart
var a = true;
bool b = false;

// 扩展
bool foo = true;
var str = '123';
if(foo) {
  // 可执行
}
if(str) {
  // 不执行
}
if(str == '123') {
  // 可执行
}
```

> + 如果单个变量作为条件进行判断时候，变量类型必须为布尔型，否则报错
> + 与JS相比，没有JS变量类型灵活多变，更受控



Dart列表变量定义

```dart
var list = [1, 2, 3];
List list1 = [4, 5, 6];
```



Dart对象变量定义

```dart
var map = {'a': 123, 'b': 456};
Map map1 = {'a': 123, 'b': 456};
```

> + 键名需要用引号，键名也可以是纯数字不含引号，区别于JS
> + Dart对象没有点方法，调用对象中某键值或者赋值，使用 Map['key']来实现



Dart函数定义与扩展

```dart
func() {
  // statement
}

func() => statement
  
// 扩展
func(int a, [bool b, String c: '123']) { // 必填参数：a，可选参数：b，可选默认参数：c
  // statement
}
```



#### 变量申明

```dart
// var
// 申明动态类型变量
// 不能与静态类型申明同时出现
var a = '123';
var String a1 = 'abc'; // 错误申明方式


// dynamic
// 申明动态类型变量
// 不能与静态类型申明同时出现
dynamic b = 123;
dynamic String b1 = 'abc'; // 错误申明方式


// final
// 申明动态类型变量，赋值后不可变更
// 可以与静态类型申明同时出现
final c = true;
final bool c1 = false;


// const
// 申明动态类型变量，赋值后不可变更
// 可以与静态类型申明同时出现
const d = true;
const bool d1 = false;
```

> + var 和 dynamic 可以互换通用
> + final 和 const 可以互换通用
> + final 和 const 申明的列表或对象类型的Dart变量，内部元素值也不能做修改，不同于JS



#### 操作符

对比 Dart 与 JS 操作符号

| 运算符                         | Dart                    | JS                      | 备注     |
| ------------------------------ | ----------------------- | ----------------------- | -------- |
| 赋值、加、减、乘、除、取余     | = + - * / %             | = + - * / %             | 完全相同 |
| 向下取整                       | ~/                      | N/A                     |          |
| 自增、自减                     | ++var var++ --var var-- | ++var var++ --var var-- | 完全相同 |
| 全等                           | ==                      | ===                     |          |
| 抽象等于                       | N/A                     | ==                      |          |
| 不等                           | !=                      | !==                     |          |
| 小于、小于等于、大于、大于等于 | < <= > >=               | < <= > >=               | 完全相同 |
| 类型判断                       | is is!                  | N/A                     |          |



#### 字符串属性与操作方法

###### 属性

| 属性       | 描述                       |
| ---------- | -------------------------- |
| isEmpty    | 判断字符串是否为空字符串   |
| isNotEmpty | 判断字符串是否为非空字符串 |
| length     | 获取字符串长度             |

###### 方法

| 方法                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| compareTo(String other) → int                                | 将此对象与另一对象进行比较，小于本身1，相等0，大于本身-1，字符串比较 |
| contains(Pattern other, [int startIndex = 0]) → bool         | 判断字符串中是否包含给定字符串或正则表达式，返回【boolean】  |
| endsWith(String other) → bool                                | 判断字符串是否以给定字符串结尾，返回【boolean】              |
| indexOf(Pattern pattern, [int start]) → int                  | 获取给定字符串在字符串中的第一个指针值                       |
| lastIndexOf(Pattern pattern, [int start]) → int              | 获取给定字符串在字符串中的最后一个指针值                     |
| padLeft(int width, [String padding = ' ']) → String          | 如果字符串自身长度小于width，在字符串左侧填补padding补足     |
| padRight(int width, [String padding = ' ']) → String         | 如果字符串自身长度小于width，在字符串右侧填补padding补足     |
| replaceAll(Pattern from, String replace) → String            | 全局替换内容，返回替换后字符串，不改变原字符串               |
| replaceFirst(Pattern from, String to, [int startIndex = 0]) → String | 替换字符串中第一个匹配内容，可指定匹配起始指针，返回新字符串，不改变原字符串 |
| split(Pattern pattern) → List<String>                        | 按照给定方式，将字符串拆分为列表，返回列表                   |
| splitMapJoin(Pattern pattern, {(Match) → String onMatch, (String) → String onNonMatch}) → String | 同时替换匹配目标和不匹配目标，返回字符串                     |
| startsWith(Pattern pattern, [int index = 0]) → bool          | 判断字符串是否以给定字符串开头，返回【boolean】              |
| substring(int startIndex, [int endIndex]) → String           | 返回此字符串的子字符串，[左闭右开)，未指定结束指针默认为末尾指针 |
| toLowerCase()                                                | 将此字符串中的所有字符转换为小写，不改变本身                 |
| toString()                                                   | 返回此对象的字符串表示形式                                   |
| toUpperCase()                                                | 将此字符串中的所有字符转换为大写，不改变本身                 |
| trim()                                                       | 去除字符串首尾空格，不改变本身                               |
| trimLeft()                                                   | 去除字符串首部空格，不改变本身                               |
| trimRight()                                                  | 去除字符串尾部空格，不改变本身                               |

示例

```dart
// padLeft
'abc'.padLeft(5, '_'); // __abc
'abc'.padLeft(1, '_'); // abc

// splitMapJoin
'ababab'.splitMapJoin('a', onMatch: (m) => 'c', onNonMatch: (n) => 'd'); // cdcdcd
'ababab'.splitMapJoin('a', onMatch: (m) => 'c', onNonMatch: (n) => n); // cbcbcb
```



#### 数字属性与操作方法

###### 属性

| 属性       | 描述                                    |
| ---------- | --------------------------------------- |
| isFinite   | 判断数字是否为有限大小                  |
| isInfinite | 判断数字是否为无穷大小                  |
| isNegative | 判断数字是否为负数                      |
| sign       | 判断数字为正数、负数或零，返回 1，-1，0 |
| isEven     | 判断数字为偶数                          |
| isOdd      | 判断数字为奇数                          |

###### 方法

| 方法                                        | 描述                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| abs()                                       | 取绝对值                                                     |
| ceil()                                      | 向上取整                                                     |
| ceilToDouble()                              | 向上取整同时转为浮点型                                       |
| clamp(num lowerLimit, num upperLimit) → num | 数字在区间内，返回该数字；数字不在区间内，返回最接近该数字的边界值 lowerLimit \|\| upperLimit |
| compareTo(num other) → int                  | 比较数值两数值大小，返回 1，-1，0                            |
| floor()                                     | 向下取整                                                     |
| floorToDouble()                             | 向下取整同时转为浮点型                                       |
| round()                                     | 四舍五入                                                     |
| roundToDouble()                             | 四舍五入同时转为浮点型                                       |
| remainder(x)                                | x表述除数，计算数值除以除数后得到的余数                      |
| toInt()                                     | 转为整型                                                     |
| toDouble()                                  | 转为浮点型                                                   |
| toString()                                  | 转为字符串                                                   |
| truncate()                                  | 舍去小数，截断功能                                           |

示例

```dart
// clamp
num number = 6,4;
number.clamp(5, 7); // 6.4
number.clamp(5, 6); // 6
number.clamp(7, 9); // 7
```



#### 列表属性与操作方法

###### 属性

| 属性       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| first      | 返回列表中第一个元素                                         |
| isEmpty    | 判断列表为空列表【boolean】                                  |
| isNotEmpty | 判断列表为非空列表【boolean】                                |
| length     | 列表长度                                                     |
| last       | 返回列表中最后一个元素                                       |
| reversed   | 返回倒序列表                                                 |
| single     | 检查列表是否只用一个元素并返回该元素，否则报错[Too many elements] |

###### 方法

| 方法                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| add(el)                                                      | 在列表末尾添加单个元素                                       |
| addAll([el1, el2, ...])                                      | 在列表末尾添加多个元素                                       |
| asMap()                                                      | 将列表转换为对象，键名为原列表指针                           |
| any()                                                        | 列表中是否有至少一个元素满足条件【boolean】，类同于contains() |
| clear()                                                      | 清空列表，改变原列表                                         |
| contains(el)                                                 | 列表中是否包含某元素【boolean】，类同于any()                 |
| elementAt(index)                                             | 返回对应指针的元素值                                         |
| every((E) → bool test) → bool                                | 列表中是否每个元素都满足条件【boolean】                      |
| expand((el) => statement)                                    | 对列表中的每个元素进行扩展操作，返回可遍历对象(el1, el2, el3, ...) |
| fillRange(int start, int end, [int fillValue])               | 指定指针区间单一元素填充，start 必填，end 必填，[左闭右开)，fillValue 为单个 int 型变量 |
| firstWhere((E) → bool test, {() → E orElse})                 | 返回列表中满足条件的第一个元素，不满足则返回-1               |
| getRange(int start, int end) → Iterable<E>                   | 获取指针区间内元素的可遍历对象，[左闭右开)                   |
| insert(int index, int value)                                 | 在列表指定指针位置插入单个int型元素                          |
| insertAll(int index, Iterable<int> iterable)                 | 在列表指定指针位置插入int型元素列表                          |
| indexOf(el) → int                                            | 返回给定元素指针，不满足则返回-1                             |
| indexWhere((int) → bool test, [int start = 0])               | 返回列表中满足条件的第一个元素的指针，可指定验证起始指针，默认从头开始，不满足则返回-1 |
| join([String separator = ""])                                | 返回字符串，默认不分割，参照JS中join方法                     |
| lastIndexOf(int element, [int start])                        | 返回指定元素的指针值，可以给定起始查询指针，不满足则返回-1   |
| lastIndexWhere((dynamic) → bool test, [int start]) → int     | 返回列表中满足条件的倒数第一个元素的指针，可指定起始指针，不满足则返回-1 |
| lastWhere((E) → bool test, {() → E orElse}) → E              | 返回列表中满足条件的倒数第一个元素，否则报错                 |
| map<T>((E) → T f) → iterable<T>                              | 遍历扩展每个列表中的元素，返回可遍历对象                     |
| removeAt(int index) → int                                    | 删除指定指针对应的元素值，返回被删除元素，更改原列表         |
| remove(el)                                                   | 删除指定元素值，返回【boolean】，更改原列表                  |
| removeLast() → int                                           | 删除列表最后一个元素，返回被删除元素值，更改原列表           |
| removeRange(int start, int end)                              | 删除列表指针区间内元素，无返回值，更改原列表                 |
| removeWhere((String) → bool test) → void                     | 删除列表中满足判断条件的所有元素，无返回值，更改原列表       |
| replaceRange(int start, int end, Iterable<int> replacement)  | 替换列表中给定指针区间内的元素，更改原列表                   |
| retainWhere((int) → bool test) → void                        | 筛选出列表中满足条件的所有元素的列表，替代原列表，无返回值   |
| setAll(int index, Iterable<int> iterable) → void             | 从指定指针开始替换列表元素，不能溢出，无返回值               |
| setRange(int start, int end, Iterable<int> iterable, [int skipCount = 0]) → void | 更改列表指定指针区间内的元素，无返回值                       |
| shuffle() → void                                             | 随机排序列表，无返回值                                       |
| skip(int count) → Iterable<E>                                | 跳过列表前count个元素，返回可遍历对象，非列表                |
| sort([(int, int) → int compare]) → void                      | 快速排序                                                     |
| sublist(int start, [int end]) → List<String>                 | 从列表中截取起止指针区间内的元素，返回结果列表，[左闭右开)   |
| take(int count) → Iterable<E>                                | 截取列表前count个元素，并返回可遍历对象                      |
| takeWhile((E) → bool test) → Iterable<E>                     | 从列表首个元素开始验证条件，返回可遍历对象，任一元素不符合条件，立即停止条件判断 |
| toList()                                                     | 列表化数据，可遍历对象转列表                                 |
| toSet()                                                      | 去重列表化数据                                               |
| toString()                                                   | 字符串话数据                                                 |
| where((E) → bool test) → Iterable<E>                         | 筛选出满足条件的可遍历对象                                   |
| whereType<T>() → Iterable<T>                                 | 筛选列表中某类型的所有元素，返回可遍历对象                   |

示例：

```dart
// expand
List a = [1, 2, 3];
var b = a.expand((el) => [el, el + 1]);
var c = b.toList();
print(b); // (1, 2, 2, 3, 3, 4)
print(c); // [1, 2, 2, 3, 3, 4]

// fillRange
List list = [1, 2, 3];
list.fillRange(1, 2, 4); // [1, 4, 3]
list.fillRange(1, 3, 4); // [1, 4, 4]

// getRange
List foo = [1, 2, 3];
var res = foo.getRange(1, 3);
print(res); // (2, 3)

// lastIndexWhere
List liw = [4, 5, 6];
liw.lastIndexWhere((el) => el > 4); // 2
liw.lastIndexWhere((el) => el > 1, 1) // 1
liw.lastIndexWhere((el) => el > 1, 0) // -1

// lastWhere
List lw = [4, 5, 6];
lw.lastWhere((el) => el > 1); // 6

// map
var ls = [1, 2, 3];
var resls = ls.map((el) => el + 1);
var resls = ls.map((el) => el + 1).toList();
print(resls); // (1, 2, 3)

// replaceRange
List l = [1, 2, 3, 4, 5];
l.replaceRange(0, 2, [4, 5, 6]); // [4, 5, 6, 3, 4, 5]
l.replaceRange(0, 2, [4]); // [4, 3, 4, 5]
l.replaceRange(0, 2, []); // [3, 4, 5]

// retainWhere
var retainList = [1, 2, 3, 4];
retainList.retainWhere((el) => el > 2)
print(retainList); // [3, 4]

// setAll
var setList = [1, 2, 3];
setList.setAll(1, [4, 5]);
print(setList); // [1, 4, 5]
setList.setAll(1, [4, 5, 6]);
print(setList); // RangeError.checkValidRange

// setRange
List<int> list1 = [1, 2, 3, 4];
List<int> list2 = [5, 6, 7, 8, 9];
list1.setRange(1, 3, list2, 3);
print(list1); // [1, 8, 9, 4]
list1.setRange(1, 3, list2, 1);
print(list1); // [1, 6, 7, 4]
list1.setRange(1, 3, list2, 4);
print(list1); // Too few elements

// skip
List ls1 = [1, 2, 3, 4];
var iterable = ls1.skip(2);
var iterable1 = ls1.skip(2).toList();
print(iterable); // (3, 4)
print(iterable1); // [3, 4]

// sort
List<num> ls2 = [1, 2, 3, 4];
List<num> ls3 = [5, 6, 7];
ls2.sort((a, b) => b - a);
ls3.sort((a, b) => a - b);
print(ls2); // [4, 3, 2, 1]
print(ls3); // [5, 6, 7]

// takeWhile
List<int> list2 = [6, 5, 7, 8, 9];
var res1 = list2.takeWhile((el) => el > 5); 
var res2 = list2.takeWhile((el) => el > 4);
var res1 = list2.takeWhile((el) => el > 6); 
print(res1); // (6)
print(res2); // (6, 5, 7, 8, 9)
print(res3); // ()

// whereType
List list2 = [6, '5', 7, 8, 9];
var res = list2.whereType<String>();
print(res); // (5)
```



#### 函数

函数定义

```dart
// 函数通常定义方式
func_name() {
  // func_body
}

// void 表示函数没有任何返回值
void func_name() {
  // func_body
}
```

函数调用

```dart
void main() {
  func()
}
func() {
  print('function')
}
```

函数返回值

```dart
return_type func_name() {
  return value;
}
```

+ return_type 为有效的数据类型
+ return 可选，未指定为 null
+ 函数实际返回值，必须与指定的 return_type 相一致
+ 单个函数只有一个返回值

```dart
void main() {
  print(func());
}

String func() {
  return 'abc';
}
```

函数可选参数，命名参数，默认参数

```dart
void main() {
 func1(123);
 func2(123);
 func2(123,s1:'abc');
 func2(123,s2:'abc',s1:'def');
 func3(123);
}

void func1(n1,[s1]) {
 print(n1);
 print(s1);
}

void func2(n1,{s1,s2}) {
 print(n1);
 print(s1);
}

void func3(n1,{s1:12}) {
   print(n1);
   print(s1);
}
/**
123
null
123
null
123
abc
123
def
123
12
*/
```



#### 字典（对象）

###### 属性

| 属性       | 描述                   |
| ---------- | ---------------------- |
| keys       | 获取所有键名可遍历对象 |
| values     | 获取所有键值可遍历对象 |
| length     | 获取键值对数量         |
| isEmpty    | 判断是否为空对象       |
| isNotEmpty | 判断是否为非空对象     |

###### 方法

| 方法                                                    | 描述                                     |
| ------------------------------------------------------- | ---------------------------------------- |
| addAll()                                                | 末尾添加键值对                           |
| clear()                                                 | 清空对象                                 |
| containsKey(Object key) → bool                          | 判断对象中是否包含某个键名               |
| containsValue(Object value) → bool                      | 判断对象中是否包含某个键值               |
| forEach((k, v) => ...)                                  | 循环调用内部键值对方法                   |
| remove(key)                                             | 删除指定键值对，返回值为指定键值对应的值 |
| removeWhere((dynamic, dynamic) → bool predicate) → void | 删除满足条件的键值对                     |
| toString()                                              | 转换为字符串                             |


## 多种数据类型变量定义与内置方法

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

| 方法          | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| toLowerCase() | 将此字符串中的所有字符转换为小写，不改变本身                 |
| toUpperCase() | 将此字符串中的所有字符转换为大写，不改变本身                 |
| trim()        | 去除头尾空格的字符串，不改变本身                             |
| compareTo()   | 将此对象与另一对象进行比较，小于本身1，相等0，大于本身-1，字符串比较 |
| replaceAll()  | 用给定值替换与指定模式匹配的所有子字符串，不改变本身，返回结果字符串 |
| split()       | 在指定分隔符的匹配处拆分字符串，返回子字符串列表             |
| substring()   | 返回此字符串的子字符串，[左开右闭)                           |
| toString()    | 返回此对象的字符串表示形式                                   |



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

方法

| 方法         | 描述                                    |
| ------------ | --------------------------------------- |
| abs()        | 取绝对值                                |
| ceil()       | 向上取整                                |
| floor()      | 向下取整                                |
| round()      | 四舍五入                                |
| remainder(x) | x表述除数，计算数值除以除数后得到的余数 |
| compareTo()  | 比较数值两数值大小，返回 1，-1，0       |
| toInt()      | 转为整型                                |
| toDouble()   | 转为浮点型                              |
| toString()   | 转为字符串                              |
| truncate()   | 舍去小数，截断功能                      |



#### 列表属性与操作方法

属性

| 属性       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| first      | 返回列表中第一个元素                                         |
| isEmpty    | 判断列表为空列表【boolean】                                  |
| isNotEmpty | 判断列表为非空列表【boolean】                                |
| length     | 列表长度                                                     |
| last       | 返回列表中最后一个元素                                       |
| reversed   | 返回倒序列表                                                 |
| single     | 检查列表是否只用一个元素并返回该元素，否则报错[Too many elements] |

方法

| 方法                                                       | 描述                                         |
| ---------------------------------------------------------- | -------------------------------------------- |
| add(el)                                                    | 在列表末尾添加单个元素                       |
| addAll([el1, el2])                                         | 在列表末尾添加多个元素                       |
| insert(index,value)                                        | 在列表指定指针位置添加单个元素               |
| insertAll(index, iterable_list_of_values)                  | 在列表指定指针位置添加多个元素               |
| replaceRange(int start_index,int end_index,Iterable[item]) | 替代列表起止指针的多个元素，起始指针左闭右开 |
| remove()                                                   | 删除指定值元素                               |
| removeAt(int index)                                        | 删除对应指针的元素                           |
| removeLast()                                               | 删除列表中最后一个元素                       |
| removeRange(int start, int end)                            | 删除给定指针区间内的元素，左闭右开           |
| indexOf(el)                                                | 返回给定元素指针                             |
| lastIndexOf(el)                                            | 返回给定元素指针                             |

```dart
List l = [1, 2, 3, 4, 5];
l.replaceRange(0, 2, [4, 5, 6]); // [4, 5, 6, 3, 4, 5]
l.replaceRange(0, 2, [4]); // [4, 3, 4, 5]
l.replaceRange(0, 2, []); // [3, 4, 5]
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

属性

| 属性       | 描述               |
| ---------- | ------------------ |
| keys       | 获取所有键名集合   |
| values     | 获取所有键值集合   |
| length     | 获取键值对数量     |
| isEmpty    | 判断是否为空对象   |
| isNotEmpty | 判断是否为非空对象 |

方法

| 方法                   | 描述                                     |
| ---------------------- | ---------------------------------------- |
| addAll()               | 末尾添加键值对                           |
| clear()                | 清空对象                                 |
| remove(key)            | 删除指定键值对，返回值为指定键值对应的值 |
| forEach((k, v) => ...) | 循环调用内部键值对方法                   |


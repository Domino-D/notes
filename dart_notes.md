## 多种数据类型变量定义与内置方法

#### 变量定义

```dart
// number
num a = 1;
// or
int b = 2;
// or
double c = 3.4;


// string
String a = '123';
// or
var b = '456';


// boolean
bool a = true;
var b = '123';
// 在条件判断中，判别变量必须是布尔型
if(a) {
  // 可执行
}
if(b) {
  // 不执行
}
if(b == '123') {
  // 可执行
}

// list
List list = [1, 2, 3];
var list1 = [4, 5, 6];

// map
// 键值对中键名必须用引号编写，区别于js
Map map = {'a': 123, 'b': 456};
var map1 = {'a': 123, 'b': 456};

// function
func() { ... }
func() => ...
// 必填参数：a，可选参数：b，可选默认参数：c
func(int a, [bool b, String c: '123']) { ... }
```

#### 操作符

```dart
// + - * / %
// ~/
// 计算结果向下取整
var a = 3.6 ~/ 2; // 1

// ++var var++ --var var--
// == != < <= > >=

// is is!
// 类型判断
var a = 123;
var b = '123';
print(a is num); // true
print(a is! num); //false
print(b is String); //true
print(b is! String); //false
```



#### 字符串属性与操作方法

###### 属性 

| 属性    | 描述                     |
| ------- | ------------------------ |
| isEmpty | 判断字符串是否为空字符串 |
| length  | 获取字符串长度           |

###### 方法

| 方法          | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| toLowerCase() | 将此字符串中的所有字符转换为小写，不改变本身                 |
| toUpperCase() | 将此字符串中的所有字符转换为大写，不改变本身                 |
| trim()        | 去除头尾空格的字符串，不改变本身                             |
| compareTo()   | 将此对象与另一对象进行比较，小于本身1，相等0，大于本身-1，字符串比较 |
| replaceAll()  | 用给定值替换与指定模式匹配的所有子字符串，不改变本身，返回结果字符串 |
| split()       | 在指定分隔符的匹配处拆分字符串，返回子字符串列表             |
| substring()   | 返回此字符串的子字符串，[左包右闭)                           |
| toString()    | 返回此对象的字符串表示形式                                   |



#### 数值属性与操作方法

###### 属性

| 属性       | 描述                                    |
| ---------- | --------------------------------------- |
| isFinite   | 判断数值为是否为有限大小                |
| isInfinite | 判断数值为是否为无穷大小                |
| isNegative | 判断数值为是否为负数                    |
| sign       | 判断数值为正数、负数或零，返回 1，-1，0 |
| isEven     | 判断数值为偶数                          |
| isOdd      | 判断数值为奇数                          |

方法

| 方法         | 描述                                    |
| ------------ | --------------------------------------- |
| abs()        | 绝对值                                  |
| ceil()       | 向上取整                                |
| floor()      | 向下取整                                |
| round()      | 四舍五入                                |
| remainder(x) | x表述除数，计算数值除以除数后得到的余数 |
| compareTo()  | 比较数值两数值大小，返回 1，-1，0       |
| toInt()      | 转为整形                                |
| toDouble()   | 转为浮点型                              |
| toString()   | 转为字符串                              |
| truncate()   | 舍去小数，截断功能                      |

#### 数组属性与操作方法

属性

| 属性       | 描述                                           |
| ---------- | ---------------------------------------------- |
| first      | 返回数组中第一个元素                           |
| isEmpty    | 判断数组为空数组【boolean】                    |
| isNotEmpty | 判断数组为非空数组【boolean】                  |
| length     | 数组长度                                       |
| last       | 返回数组中最后一个元素                         |
| reversed   | 返回倒序数组                                   |
| single     | 检查数组是否只用一个元素并返回该元素，否则报错 |

方法

| 方法                                                       | 描述                                         |
| ---------------------------------------------------------- | -------------------------------------------- |
| add(el)                                                    | 在数组末尾添加单个元素                       |
| addAll([el1, el2])                                         | 在数组末尾添加多个元素                       |
| insert(index,value)                                        | 在数组指定指针位置添加单个元素               |
| insertAll(index, iterable_list_of_values)                  | 在数组指定指针位置添加多个元素               |
| replaceRange(int start_index,int end_index,Iterable[item]) | 替代数组起止指针的多个元素，起始指针左闭右开 |
| remove()                                                   | 删除指定值元素                               |
| removeAt(int index)                                        | 删除对应指针的元素                           |
| removeLast()                                               | 删除数组中最后一个元素                       |
| removeRange(int start, int end)                            | 删除给定指针区间内的元素，左闭右开           |

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

| 属性       | 描述                 |
| ---------- | -------------------- |
| keys       | 获取所有键值集合     |
| values     | 获取所有键对应值集合 |
| length     | 获取键值对数量       |
| isEmpty    | 判断是否为空对象     |
| isNotEmpty | 判断是否为非空对象   |

方法

| 方法                   | 描述                                     |
| ---------------------- | ---------------------------------------- |
| addAll()               | 末尾添加键值对                           |
| clear()                | 清空对象                                 |
| remove(key)            | 删除指定键值对，返回值为指定键值对应的值 |
| forEach((k, v) => ...) | 循环调用内部键值对方法                   |


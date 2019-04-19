#### 多种数据类型变量定义与内置方法

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


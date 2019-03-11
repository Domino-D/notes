flutter from tody. mark - 2019/1/24

> - MaterialApp
> - Scaffold
> - Text
>
> ```dart
> import 'package:flutter/material.dart';
> 
> void main() => runApp(MyApp());
> 
> var name = 'k';
> 
> class MyApp extends StatelessWidget {
>  	@override
>  	Widget build(BuildContext context) {
>    		return new MaterialApp(
>      		title: "title",
>      		theme: ThemeData.light(), //背景主题色
>      		debugShowCheckedModeBanner: false, //消除界面右上角debug标签
>      		home: new Scaffold(
>        		body: new Text(
>          		"data $name", //变量引用，以$开头：$variablity
>          		textAlign: TextAlign.center,
>          		overflow: TextOverflow.clip, //clip:折叠; ellipsis:省略号; fade:淡出
>          		textScaleFactor: 3, //放大比率
>          		style: TextStyle(
>            		fontWeight: FontWeight.bold,
>            		fontFamily: "arial",
>            		height: 2, //行高
>            		decoration: TextDecoration.underline, //文本装饰类型
>            		decorationColor: Colors.red, //文本装饰颜色
>            		decorationStyle: TextDecorationStyle.dashed, //文本装饰样式
>          		),
>        		),
>      		),
>    		);
>  	}
> }
> ```


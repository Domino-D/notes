flutter from tody. mark - 2019/1/24

Demo

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

Basic widgets

> Container
>
> ```dart
> (new) Container({
>   Key key,
>   AlignmentGeometry alignment,//浮动对齐
>   EdgeInsetsGeometry padding,//内边距
>   Color color,//背景色
>   Decoration decoration,//child后的样式
>   Decoration foregroundDecoration,//child前的样式
>   double width,
>   double height,
>   BoxConstraints constraints,
>   EdgeInsetsGeometry margin,//外边距
>   Matrix4 transform,//旋转
>   Widget child//子类
> }) → Container
>   
> ```
>
> Row
>
> ```dart
> (new) Row({
>   Key key,
>   MainAxisAlignment mainAxisAlignment: MainAxisAlignment.start,//横向对齐方式
>   MainAxisSize mainAxisSize: MainAxisSize.max,//横向轴最大尺寸
>   CrossAxisAlignment crossAxisAlignment: CrossAxisAlignment.center,//竖直位置
>   TextDirection textDirection,//文字方向
>   VerticalDirection verticalDirection: VerticalDirection.down,//竖直方向
>   TextBaseline textBaseline,//文字基准线
>   List<Widget> children: const <Widget> []//子类（数组）
> }) → Row
> ```
>
> Column
>
> ```dart
> (new) Column({
>   Key key,
>   MainAxisAlignment mainAxisAlignment: MainAxisAlignment.start,//横向对齐方式
>   MainAxisSize mainAxisSize: MainAxisSize.max,//横向轴最大尺寸
>   CrossAxisAlignment crossAxisAlignment: CrossAxisAlignment.center,//竖直位置
>   TextDirection textDirection,//文字方向
>   VerticalDirection verticalDirection: VerticalDirection.down,//竖直方向
>   TextBaseline textBaseline,//文字基准线
>   List<Widget> children: const <Widget> []//子类（数组）
> }) → Column
> ```


#### flutter from tody. mark - 2019/1/24

#### Demo

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

#### Basic widgets

> Container
>
> ```dart
> (new) Container({
> 	Key key,
> 	AlignmentGeometry alignment,//浮动对齐
> 	EdgeInsetsGeometry padding,//内边距
> 	Color color,//背景色
> 	Decoration decoration,//child后的样式
> 	Decoration foregroundDecoration,//child前的样式
> 	double width,
> 	double height,
> 	BoxConstraints constraints,
> 	EdgeInsetsGeometry margin,//外边距
> 	Matrix4 transform,//旋转
> 	Widget child//子类
> }) → Container
> 
> ```
>
> 
>
> Row
>
> ```dart
> (new) Row({
> Key key,
> MainAxisAlignment mainAxisAlignment: MainAxisAlignment.start,//横向对齐方式
> MainAxisSize mainAxisSize: MainAxisSize.max,//横向轴最大尺寸
> CrossAxisAlignment crossAxisAlignment: CrossAxisAlignment.center,//竖直位置
> TextDirection textDirection,//文字方向
> VerticalDirection verticalDirection: VerticalDirection.down,//竖直方向
> TextBaseline textBaseline,//文字基准线
> List<Widget> children: const <Widget> []//子类（数组）
> }) → Row
> ```
>
> 
>
> Column
>
> ```dart
> (new) Column({
> Key key,
> MainAxisAlignment mainAxisAlignment: MainAxisAlignment.start,//横向对齐方式
> MainAxisSize mainAxisSize: MainAxisSize.max,//横向轴最大尺寸
> CrossAxisAlignment crossAxisAlignment: CrossAxisAlignment.center,//竖直位置
> TextDirection textDirection,//文字方向
> VerticalDirection verticalDirection: VerticalDirection.down,//竖直方向
> TextBaseline textBaseline,//文字基准线
> List<Widget> children: const <Widget> []//子类（数组）
> }) → Column
> ```
>
> 
>
> Image
>
> ```dart
> Image.asset //加载资源图片，就是加载项目资源目录中的图片,加入图片后会增大打包的包体体积，用的是相对路径
> Image.network //网络资源图片，意思就是你需要加入一段http://xxxx.xxx的这样的网络路径地址
> Image.file //加载本地图片，就是加载本地文件中的图片，这个是一个绝对路径，跟包体无关【不常用】
> Image.memory //加载Uint8List资源图片【不常用】
> 
> //——————————————————————
> //attribute
> image: AssetImage(String assetName, {AssetBundle bundle, String package}) → AssetImage
> 
> image: NetworkImage(String url, {double scale: 1.0, Map<String, String> headers}) → NetworkImage
> ```
>
> 
>
> Text
>
> ```dart
> Text(String data,{ //文字字符串
> Key key,
> TextStyle style, //文字样式
> StrutStyle strutStyle,
> TextAlign textAlign, //对齐方式
> TextDirection textDirection, //文字装饰
> Locale locale,
> bool softWrap,
> TextOverflow overflow, //溢出显示
> double textScaleFactor, //缩放比例
> int maxLines, //最大行数
> String semanticsLabel
> }) → Text
> ```
>
> 
>
> Icon
>
> ```dart
> Icon(IconData icon, { 
> Key key,
> double size, //尺寸，默认24px
> Color color, //主题色
> String semanticLabel, //语义标签，供残障用户使用
> TextDirection textDirection //渲染图标方向，需要IconData.matchTextDirection字段为true
> }) → Icon
> 
> //extensions
> IconButton({
> Key key,
> double iconSize: 24.0,
> EdgeInsetsGeometry padding: const EdgeInsets.all(8.0),
> AlignmentGeometry alignment: Alignment.center,
> Widget icon,
> Color color,
> Color highlightColor, //按钮处于向下（按下）状态时按钮的辅助颜色
> Color splashColor, //按钮处于向下（按下）状态时按钮的主要颜色
> Color disabledColor,
> () → void onPressed, //点击回调函数
> String tooltip //辅助文字说明标签
> }) → IconButton
> 
> Icons //引用flutter内置图标
> 
> IconTheme({
> Key key,
> IconThemeData data,//IconThemeData({Color color, double opacity, double size}) → IconThemeData
> Widget child //Icon和ImageIcon应用IconThemeData中定义的主题属性
> }) → IconTheme
> 
> ImageIcon(ImageProvider<dynamic> image,{
> Key key,
> double size,
> Color color,
> String semanticLabel
> }) → ImageIcon
> ```
>
> FlatButton 背景透明按钮
>
> FloatingActionButton 浮动按钮
>
> IconButton 图标按钮
>
> PopupMenuButton 下拉菜单按钮
>
> 
>
> RaisedButton
>
> ```dart
> (new) RaisedButton({
> Key key,
> () → void onPressed,
> (bool) → void onHighlightChanged,
> ButtonTextTheme textTheme,
> Color textColor,
> Color disabledTextColor,
> Color color,
> Color disabledColor,
> Color highlightColor, //按钮处于向下（按下）状态时按钮的辅助颜色
> Color splashColor, //按钮处于向下（按下）状态时按钮的主要颜色
> Brightness colorBrightness,
> double elevation,
> double highlightElevation,
> double disabledElevation,
> EdgeInsetsGeometry padding,
> ShapeBorder shape,
> Clip clipBehavior: Clip.none,
> MaterialTapTargetSize materialTapTargetSize,
> Duration animationDuration,
> Widget child
> }) → RaisedButton
> ```
>
> 
>
> AppBar
>
> ```dart
> (new) AppBar({
>   Key key,
>   Widget leading, //标题上方widget
>   bool automaticallyImplyLeading: true,
>   Widget title,
>   List<Widget> actions, //标题下方功能按钮组
>   Widget flexibleSpace,
>   PreferredSizeWidget bottom,
>   double elevation,
>   Color backgroundColor,
>   Brightness brightness,//亮度
>   IconThemeData iconTheme,
>   TextTheme textTheme,
>   bool primary: true,
>   bool centerTitle, //标题是否居中
>   double titleSpacing: NavigationToolbar.kMiddleSpacing,
>   double toolbarOpacity: 1.0, //工具栏透明度
>   double bottomOpacity: 1.0 //底部透明度
> }) → AppBar
> ```

#### Theme

> ThemeData
>
> ```dart
> (new) ThemeData({
>   Brightness brightness,
>   MaterialColor primarySwatch,
>   Color primaryColor,
>   Brightness primaryColorBrightness,
>   Color primaryColorLight,
>   Color primaryColorDark,
>   Color accentColor,
>   Brightness accentColorBrightness,
>   Color canvasColor,
>   Color scaffoldBackgroundColor,
>   Color bottomAppBarColor,
>   Color cardColor,
>   Color dividerColor,
>   Color highlightColor,
>   Color splashColor,
>   InteractiveInkFeatureFactory splashFactory,
>   Color selectedRowColor,
>   Color unselectedWidgetColor,
>   Color disabledColor,
>   Color buttonColor,
>   ButtonThemeData buttonTheme,
>   Color secondaryHeaderColor,
>   Color textSelectionColor,
>   Color cursorColor,
>   Color textSelectionHandleColor,
>   Color backgroundColor,
>   Color dialogBackgroundColor,
>   Color indicatorColor,
>   Color hintColor,
>   Color errorColor,
>   Color toggleableActiveColor,
>   String fontFamily,
>   TextTheme textTheme,
>   TextTheme primaryTextTheme,
>   TextTheme accentTextTheme,
>   InputDecorationTheme inputDecorationTheme,
>   IconThemeData iconTheme,
>   IconThemeData primaryIconTheme,
>   IconThemeData accentIconTheme,
>   SliderThemeData sliderTheme,
>   TabBarTheme tabBarTheme,
>   CardTheme cardTheme,
>   ChipThemeData chipTheme,
>   TargetPlatform platform,
>   MaterialTapTargetSize materialTapTargetSize,
>   PageTransitionsTheme pageTransitionsTheme,
>   AppBarTheme appBarTheme,
>   BottomAppBarTheme bottomAppBarTheme,
>   ColorScheme colorScheme,
>   DialogTheme dialogTheme,
>   Typography typography,
>   CupertinoThemeData cupertinoOverrideTheme
> }) → ThemeData
> ```

#### Layout

> ##### Basic layout
>
> Container 
>
> ```dart as above
> //as above
> ```
>
> Padding
>
> ```dart
> Padding({Key key, EdgeInsetsGeometry padding, Widget child}) → Padding
> ```
>
> Center
>
> ```dart
> Center({Key key, double widthFactor, double heightFactor, Widget child}) → Center
> ```
>
> Align
>
> ```dart
> Align({Key key, AlignmentGeometry alignment: Alignment.center, double widthFactor, double heightFactor, Widget child}) → Align
> ```
>
> FittedBox 内部元素大小随动变化
>
> ```dart
> FittedBox({Key key, BoxFit fit: BoxFit.contain, AlignmentGeometry alignment: Alignment.center, Widget child}) → FittedBox
> ```
>
> AspectRatio   定长宽比widget
>
> ```dart
> AspectRatio({Key key, double aspectRatio, Widget child}) → AspectRatio
> ```
>
> ConstrainedBox 约束内部元素widget
>
> ```dart
> ConstrainedBox({Key key, BoxConstraints constraints, Widget child}) → ConstrainedBox
> ```
>
> IntrinsicHeight 子元素撑满高度
>
> ```dart
> IntrinsicHeight({Key key, Widget child}) → IntrinsicHeight
> ```
>
> IntrinsicWidth  子元素撑满宽度
>
> ```dart
> IntrinsicWidth({Key key, double stepWidth, double stepHeight, Widget child}) → IntrinsicWidth
> ```
>
> ##### Complex layout
>
> Row
>
> ```dart
> //as above
> ```
>
> Column
>
> ```dart
> //as above
> ```
>
> Stack 允许堆叠
>
> ```dart
> Stack({Key key, AlignmentGeometry alignment: AlignmentDirectional.topStart, TextDirection textDirection, StackFit fit: StackFit.loose, Overflow overflow: Overflow.clip, List<Widget> children: const <Widget> []}) → Stack
> ```
>
> Flow 
>
> ```dart
> Flow({Key key, FlowDelegate delegate, List<Widget> children: const <Widget> []}) → Flow
> ```
>
> Table
>
> ```dart
> Table({Key key, List<TableRow> children: const <TableRow> [], Map<int, TableColumnWidth> columnWidths, TableColumnWidth defaultColumnWidth: const FlexColumnWidth(1.0), TextDirection textDirection, TableBorder border, TableCellVerticalAlignment defaultVerticalAlignment: TableCellVerticalAlignment.top, TextBaseline textBaseline}) → Table
> ```
>
> Wrap
>
> ```dart
> Wrap({Key key, Axis direction: Axis.horizontal, WrapAlignment alignment: WrapAlignment.start, double spacing: 0.0, WrapAlignment runAlignment: WrapAlignment.start, double runSpacing: 0.0, WrapCrossAlignment crossAxisAlignment: WrapCrossAlignment.start, TextDirection textDirection, VerticalDirection verticalDirection: VerticalDirection.down, List<Widget> children: const <Widget> []}) → Wrap
> ```
>
> ListBody
>
> ```dart
> ListBody({Key key, Axis mainAxis: Axis.vertical, bool reverse: false, List<Widget> children: const <Widget> []}) → ListBody
> ```
>
> ListView
>
> ```dart
> ListView({Key key, Axis scrollDirection: Axis.vertical, bool reverse: false, ScrollController controller, bool primary, ScrollPhysics physics, bool shrinkWrap: false, EdgeInsetsGeometry padding, double itemExtent, bool addAutomaticKeepAlives: true, bool addRepaintBoundaries: true, bool addSemanticIndexes: true, double cacheExtent, List<Widget> children: const <Widget> [], int semanticChildCount, DragStartBehavior dragStartBehavior: DragStartBehavior.down}) → ListView
> ```


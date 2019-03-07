antd

> * Modal对话框中，默认设置宽度最大为650px，且增加了！important最高权重。
>
>   Modal提供了 **wrapClassName** 属性，可以命名对话框外层容器的类名。通过在css文件中如下修改层叠阀盖默认最大宽度650px。
>
>   ```css
>   .wrapClassName .ant-modal {
>       width: 1000px;
>   }
>   ```

> * 全局提示 message.config 配置
>
>   ```javascript
>   message.config({
>       top: 100, //@param number || string 距离顶部位置，单位px
>       duraion: 2, //显示持续时间，单位秒
>       maxCount: 1 //最多显示条数，超过就立即隐藏多出的最早的一条
>   })
>   ```
>

copy-to-clipboard

```javascript
//yarn add copy-to-clipboard
copy(variation)
```

vmax

> * 相对于可视窗口的宽度或高度中较大的那个。类比于 vh， vw
>
>   ```css
>   p {
>       font-size: 8vmax;
>   }
>   ```

font & Font Format

> * woff2 不适用于IE、IE mobile、UC for Android
>
> * woff 最新客户端全兼容
>
> * svg 适用于Safari、iOS Safari
>
> * eot 仅仅适用于IE
>
> * ttf / otf 不适用于IE
>
>   ```css
>   /*引用外部字体文件，写入css命名，定义模板输出*/
>   @font-face {
>       font-family: 'Font name string'; /*定义字体名称*/
>       src: url('fonts/hanshand-webfont.eot');
>       src: url('fonts/hanshand-webfont.eot') format('embedded-opentype'),
>            url('fonts/hanshand-webfont.woff') format('woff'),
>            url('fonts/hanshand-webfont.ttf') format('truetype'),
>            url('fonts/hanshand-webfont.svg') format('svg');
>       font-weight: normal;
>       font-style: normal;
>   }
>   ```

overflow

> * css 中 overflow 属性。在多层嵌套的布局环境下，内部元素（常见的是modal弹出框之类的元素），会超出屏幕边界，原本不显示的滚动条会被迫出现，为了撑开页面显示超出边界的元素。
> * 此时，overflow 属性需要配合 position:relative; 一起使用。

react router <params / query / state>

> * params 传参方式会直接体现在地址栏中，只允许传递字符串。
>
> * query方式和state方式一致，可传递对象数据，传递数据不会体现在地址栏中。
>
>   ```js
>   let queryData = {
>       pathname: '/tonextpage',
>       query: <...>
>   }
>   let stateData = {
>       pathname: '/tonextpage',
>       state: <...>
>   }
>   
>   <Link to={queryData}></link>
>   <Link to={stateData}></link>
>   ```

exif-js

> * 读取图像元数据
>
> * yarn add exif-js
>
>   ```javascript
>   import Exif from 'exif-js'
>   
>   Exif.getData(fileObj, function(){
>       const allTags = Exif.getAllTags(this)
>   }
>   ```

antd-upload-customRequest

> * customRequest 方法不支持 async 函数
>
>   复现报错：
>
>   ```javascript
>   Uncaught TypeError: reqs[uid].abort is not a function
>   ```

react function transfer between father and son component

> * function transfer
>
>   ```javascript
>   // in father component
>   getName() {
>       ...
>   }
>   ...
>   <Son getName={this.getName.bind(this)}/>
>   
>   //to run geName function in son component
>   this.props.getName()
>   ```

css z-index   invalid

> * 父标签设置了position:relative
> * 当前标签未设置position:absolute
> * 当前标签设置了float属性

css z-index   valid

> * 当前标签设置position:absolute / relative

flutter from tody. mark - 2019/1/24

react native from today. mark - 2019/1/30 公司业务需求走上RN道路，原生APP你好！

> * ```javascript
>   RN 宽高样式支持 百分比：'100%'；像素：300，   并不支持屏幕比：'100vh'
>   ```
> ```
> 
>   * react-native-webviewla 依赖保，允许react-native中内嵌H5页面，通过跨域通讯
> 
>  ```javascript
>  import React, { Component } from "react"
>  import { StyleSheet, Text, View } from "react-native"
>  //react-native 中也包含同样名称和用途的组件，官方后续将剥离出来，最好使用react-native-webview
>  import { WebView } from "react-native-webview"
>  
>  class MyWebComponent extends Component {
>    render() {
>      return (
>        <WebView
>          source={{ uri: "https://facebook.github.io/react-native/" }}
>        />
>      )
>    }
>  }
> ```


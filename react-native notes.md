react native from today. mark - 2019/1/30

clean build folder

> 

height & width

> ```javascript
> RN 宽高样式支持 百分比：'100%'；像素：300，   并不支持屏幕比：'100vh'
> ```

react-native-webviewla 依赖保，允许react-native中内嵌H5页面，通过跨域通讯

> ```javascript
> import React, { Component } from "react"
> import { StyleSheet, Text, View } from "react-native"
> //react-native 中也包含同样名称和用途的组件，官方后续将剥离出来，最好使用react-native-webview
> import { WebView } from "react-native-webview"
> class MyWebComponent extends Component {
> 	render() {
> 		return (
> 			<WebView
> 				source={{ uri: "https://facebook.github.io/react-native/" }}
> 			/>
> 		)
> 	}
> }
> ```

react-native-navigation

> stoped

Error: `React/RCTBundleURLProvider.h' file not found`

> Xcode -v10.1
>
> 1. 如果 Scheme 中有 React，选择 React
>
>    Menu => Product => Scheme => React
>
> 2. 如果 Scheme 中没有 React，新建 Scheme 中选择 React
>
>    Menu => Product => Scheme => Manage Schemes => React
# react + cesium

### 环境配置（脚手架create-react-app环境下）

1. node_modules中手动添加cesium包

2. 在项目根目录下的 index.js 设置baseurl，链接静态资源

   ```javascript
   // index.js
   import React from 'react'
   import ReactDOM from 'react-dom'
   import App from './App'
   
   // cesium setBaseUrl
   import "cesium/Source/Widgets/widgets.css"
   import buildModuleUrl from "cesium/Source/Core/buildModuleUrl"
   buildModuleUrl.setBaseUrl('/cesium/')
   
   ReactDOM.render(<App />, document.getElementById('root'))
   ```

3. 静态资源配置

   cesium/Source 中包含的资源如下：

   ```javascript
   Assets/   copyrightHeader.js   DataSources/   Renderer/   Shaders/   Widgets/   Cesium.js   Core/   main.js   Scene/   ThirdParty/   Workers/
   ```

   在项目根目录下的 public 文件中需要添加的cesium静态资源如下：

   ```javascript
   Assets/   ThirdParty/   Widgets/   Workers/   Cesium.js
   ```

4. 初始化布局显示

   ```javascript
   // App.js
   import React, { Component } from 'react'
   import Cartesian3 from 'cesium/Source/Core/Cartesian3'
   import WrappedCesiumApp from './cesium/cesium'
   
   export default class App extends Component {
   	componentDidMount() {
       	//load cesium map
           //这里需要三个数据，经度，唯独，高度 用来定义 cesium camera 的试图位置
       	let defaultCenter = Cartesian3.fromDegrees(121.604848, 31.178455, 10000)
       	this.refs.map.setViewer(defaultCenter)
   	}
   	render() {
       	return (
           	<WrappedCesiumApp ref="map"/>
       	)
   	}
   }
   ```

5. 启动项目，正常显示

### 接口方法 / 封装方法

```javascript
import CesiumViewer from "cesium/Source/Widgets/Viewer/Viewer"
import Cartesian3 from 'cesium/Source/Core/Cartesian3'
import CesiumMath from 'cesium/Source/Core/Math'
//新建视图，并挂载到选定到 dom 元素上(this.refs.map)
this.viewer = new CesiumViewer(this.refs.map, configOptions)


//设定默认视图显示点
let defaultCenter = Cartesian3.fromDegrees(longitude, latitude, height)


//设定初始视图显示位置
this.viewer.camera.setView({
    destination: defaultCenter,
    orientation: {
        heading : CesiumMath.toRadians(90.0), // east, default value is 0.0 (north)
        pitch : CesiumMath.toRadians(-90),    // default value (looking down)
        roll : 0.0                             // default value
    }
})


//添加点
this.viewer.entities.add({
    
})
//点击事件添加

```
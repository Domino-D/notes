# fabric

#### 安装使用

`yarn add fabric`

#### 官方链接

[fabric文档](http://fabricjs.com)

```javascript
import React, { Component } from 'react'
import { fabric } from 'fabric/dist/fabric'
import imgurl from './DJI_0004_R.JPG'

export default class Demo extends Component {
  componentDidMount() {
    this.initializeFabric()
  }

  initializeFabric() {
    let canvas = new fabric.Canvas('canvasmap'),
      mouseFrom = {},
      mouseTo = {},
      moveCount = 1,
      doDrawing = false,
      drawingObject = null,
      canDetection = true
    //顶级全局变量，屏幕缩放
    window.zoom = window.zoom ? window.zoom : 1
    // 设置北京图片
    canvas.setBackgroundImage(imgurl, canvas.renderAll.bind(canvas), {
      originX: "left",
      originY: "top",
    })
    // 初始状态下，不可获取，不可编辑
    canvas.skipTargetFind = true
    canvas.selection = false
    // 坐标转换
    function transformMouse(mouseX, mouseY) {
      return { x: mouseX / window.zoom, y: mouseY / window.zoom }
    }
    // 绘制功能函数
    function drawing() {
      if (drawingObject) {
        canvas.remove(drawingObject)
      }
      let canvasObject = null,
        path = [
          ["M", mouseFrom.x, mouseFrom.y],
          ["L", mouseTo.x, mouseFrom.y],
          ["L", mouseTo.x, mouseTo.y],
          ["L", mouseFrom.x, mouseTo.y],
          ["L", mouseFrom.x, mouseFrom.y],
          ["z"]
        ] // 路径绘制，二维数组
      canvasObject = new fabric.Path(path, {
        stroke: "red",
        strokeWidth: 2,
        fill: "transparent",
      })
      if (canvasObject) {
        canvas.add(canvasObject)
        drawingObject = canvasObject
      }
    }
    // 链式编程绑定事件
    canvas
      .on("mouse:down", (options) => {
        let xy = transformMouse(options.e.offsetX, options.e.offsetY)
        mouseFrom.x = xy.x
        mouseFrom.y = xy.y
        doDrawing = true
      })
      .on("mouse:up", (options) => {
        let xy = transformMouse(options.e.offsetX, options.e.offsetY)
        mouseTo.x = xy.x
        mouseTo.y = xy.y
        drawingObject = null
        moveCount = 1
        doDrawing = false
      })
      .on("mouse:move", (options) => {
        if (moveCount % 2 && !doDrawing) {
          return
        }
        moveCount++
        let xy = transformMouse(options.e.offsetX, options.e.offsetY)
        mouseTo.x = xy.x
        mouseTo.y = xy.y
        if (canDetection) {
          drawing()
        }
      })
      .on("mouse:over", (e) => {
        let target = e.target
        if (target) {
          console.log(target)
          target.set({ "fill": "white", "opacity": 0.4 })
          canvas.renderAll()
          console.log(target.type)
        }
      })
      .on("mouse:out", (e) => {
        let target = e.target
        if (target) {
          target.set("fill", "transparent")
          canvas.renderAll()
        }
      })
      .on("mouse:dblclick", (e) => {
        canDetection = !canDetection
        canvas.remove(e.target)
        console.log(canvas)
        let arr = canvas._objects
        console.log(arr)
      })
  }

  render() {
    return (
      <canvas id="canvasmap" width="640px" height="512px"></canvas>
    )
  }
}
```


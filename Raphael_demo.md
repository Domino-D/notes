# Raphael

##### 安装使用

`yarn add raphael`

##### 官方链接

[raphael文档](http://dmitrybaranovskiy.github.io/raphael/)

```javascript
import React, { Component, Fragment } from 'react'
import Raphael from 'raphael'
import imgurl from './DJI_0004_R.JPG'
// 初始界面矩形参数
const rects = [
  {
    id: 1,
    rx: 35,
    ry: 45,
    rw: 20,
    rh: 20,
  }, {
    id: 2,
    rx: 75,
    ry: 45,
    rw: 20,
    rh: 20,
  }, {
    id: 3,
    rx: 115,
    ry: 45,
    rw: 20,
    rh: 20,
  }
]

export default class App extends Component {
  state = {
    targetLegend: null,
    legendId: 1,
    paper: null,
  }

  componentDidMount() {
    let paper = Raphael("raphaelmap", 640, 512)
    const _this = this
    this.setState({
      paper,
    }, () => {
      _this.paintingReady()
      _this.paintRects()
    })
  }
  // 首屏加载，根据参数绘制矩形
  paintRects() {
    const { paper } = this.state
    const _this = this
    let legendId = rects.length + 1
    this.setState({
      legendId,
    })
    rects && rects.forEach(el => {
      let ele = paper.rect(el.rx, el.ry, el.rw, el.rh)
      let ew, eh, ex, ey
      console.log(ele)
      ele.id = el.id
      ele.attr({
        "fill": "transparent",
        "stroke": "red",
        "title": "标记 " + ele.id,
      })
        .drag(
          // 拖动状态中
          (dx, dy, x, y, event) => {
            if (event.shiftKey) {
              // 临界边界判定
              let boundrayW1 = ew + dx > 0,
                boundrayW2 = ex + ew + dx < 640,
                boundrayH1 = eh + dy > 0,
                boundrayH2 = ey + eh + dy < 512
              ele.attr({
                "width": boundrayW1 ? boundrayW2 ? ew + dx : 640 - ex : 3,
                "height": boundrayH1 ? boundrayH2 ? eh + dy : 512 - ey : 3,
                "cursor": "nwse-resize",
              })
            } else {
              // 临界边界判定
              let boundrayX1 = ex + dx > 0,
                boundrayX2 = ex + dx < 640 - ele.attrs.width,
                boundrayY1 = ey + dy > 0,
                boundrayY2 = ey + dy < 512 - ele.attrs.height
              ele.attr({
                "x": boundrayX1 ? boundrayX2 ? ex + dx : 640 - ele.attrs.width : 0,
                "y": boundrayY1 ? boundrayY2 ? ey + dy : 512 - ele.attrs.height : 0,
                "cursor": "move",
              })
            }
          },
          // 拖动状态初始化
          (x, y, event) => {
            const { pretarget } = this.state
            ele.attr({
              "fill": "#ffcdd2",
              "fill-opacity": 0.5,
            })
            pretarget && pretarget !== ele && pretarget.attr({
              "fill": "transparent",
              "fill-opacity": 0,
            })
            ew = ele.attrs.width
            eh = ele.attrs.height
            ex = ele.attrs.x
            ey = ele.attrs.y
            _this.setState({
              pretarget: ele,
            })
          },
          // 拖动状态结束
          () => {
            ele.attr({
              "cursor": "default"
            })
          }
        )
    })
  }
	// 初始化画板
  paintingReady() {
    const { paper } = this.state
    let x1, y1, x2, y2, set, cando = false, _this = this
    let element = paper.rect(0, 0, 640, 512)
    // 链式编程，绑定事件
    element.attr({ "fill": "transparent" })
      .mousedown((e) => {
        const { pretarget } = this.state
        x1 = e.layerX
        y1 = e.layerY
        cando = true
        pretarget && pretarget.attr({
          "fill": "transparent",
          "fill-opacity": 0,
        })
        _this.setState({
          pretarget: null,
        })
      })

      .mousemove((e) => {
        set && set.remove()
        let _x = e.layerX, _y = e.layerY, _width = _x - x1, _height = _y - y1
        if (cando && _width > 0 && _height > 0) {
          paper.setStart()
          paper.rect(x1, y1, _width, _height)
          set = paper.setFinish()
          set.attr({
            "fill": "transparent",
            "stroke": "red",
          })
        }
      })

      .mouseup((e) => {
        const { legendId } = this.state
        cando = false
        x2 = e.layerX
        y2 = e.layerY
        let width = x2 - x1, height = y2 - y1, ex, ey, ew, eh
        if (width > 3 && height > 3) {
          set && set.remove()
          let ele = paper.rect(x1, y1, width, height)
          console.log(ele)
          ele.id = legendId
          _this.setState({
            legendId: legendId + 1,
          })
          ele.attr({
            "fill": "transparent",
            "stroke": "red",
            "title": "标记 " + ele.id,
          })
            .drag(
              // 拖动状态中
              (dx, dy, x, y, event) => {
                if (event.shiftKey) {
                  // 临界边界判定
                  let boundrayW1 = ew + dx > 0,
                    boundrayW2 = ex + ew + dx < 640,
                    boundrayH1 = eh + dy > 0,
                    boundrayH2 = ey + eh + dy < 512
                  ele.attr({
                    "width": boundrayW1 ? boundrayW2 ? ew + dx : 640 - ex : 3,
                    "height": boundrayH1 ? boundrayH2 ? eh + dy : 512 - ey : 3,
                    "cursor": "nwse-resize",
                  })
                } else {
                  // 临界边界判定
                  let boundrayX1 = ex + dx > 0,
                    boundrayX2 = ex + dx < 640 - ele.attrs.width,
                    boundrayY1 = ey + dy > 0,
                    boundrayY2 = ey + dy < 512 - ele.attrs.height
                  ele.attr({
                    "x": boundrayX1 ? boundrayX2 ? ex + dx : 640 - ele.attrs.width : 0,
                    "y": boundrayY1 ? boundrayY2 ? ey + dy : 512 - ele.attrs.height : 0,
                    "cursor": "move",
                  })
                }
              },
              // 拖动状态初始化
              (x, y, event) => {
                const { pretarget } = this.state
                ele.attr({
                  "fill": "#ffcdd2",
                  "fill-opacity": 0.5,
                })
                pretarget && pretarget !== ele && pretarget.attr({
                  "fill": "transparent",
                  "fill-opacity": 0,
                })
                ew = ele.attrs.width
                eh = ele.attrs.height
                ex = ele.attrs.x
                ey = ele.attrs.y
                _this.setState({
                  pretarget: ele,
                })
              },
              // 拖动状态结束
              () => {
                ele.attr({
                  "cursor": "default"
                })
              }
            )
        }
      })
  }

  render() {
    return (
      <Fragment>
        <img src={imgurl} alt="pic" />
        <div id="raphaelmap" style={{ position: "absolute", top: 0, left: 0 }}></div>
      </Fragment>
    )
  }
}
```


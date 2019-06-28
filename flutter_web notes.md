#### Flutter web

###### Font and Icons

Icon 在 flutter web 项目初始状态下是没有效果的，未配置时只显示一个框。

配置方法如下：

项目根目录下做一下配置，添加 MaterialIcons，之后使用 `Icons` 就可以正常展示了。

其它项目中需要的字体也可以在 FontManifest.json 中进行配置。

```json
// 'web/assets/FontManifest.json'
[
  {
    "family": "MaterialIcons",
    "fonts": [
      {
        "asset": "https://fonts.gstatic.com/s/materialicons/v42/flUhRq6tzZclQEJ-Vdg-IuiaDsNcIhQ8tQ.woff2"
      }
    ]
  },
  {
    "family": "Raleway",
    "fonts": [
      {
        "asset": "Raleway-Regular.ttf" // 'web/assets/Raleway-Regular.ttf'
      }
    ]
  }
]
```



###### Router

fluro 只适用于 flutter app，不适用于flutter web app。

目前没有找到类似好的路由库，原生写路由




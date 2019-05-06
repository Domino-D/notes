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

React - setState(prevState => {})

> ```javascript
> //...
> constructor(props) {
>  super(props)
>  this.state = {
>      num: 1,
>  }
> }
> //...
> this.setState(
>   prevState => ({
>  		num: prevState.num + 1, //通过调用 prevState 形参，获取上一个状态组件中的 state 值
> 	})
> )
> ```

git stash

> ```shell
> //暂存挂起到工作区，回到当前分支最近一次提交状态
> git stash
> 
> //显示暂存列表
> git stash list
> 
> //回到挂起前状态，应用到所在分支，并同时删除暂存列表
> //回归到挂起前状态与所在分支无关
> git stash pop
> 
> //删除暂存列表中某一项
> git stash drop stash@{0}
> ```

CSS calc()

> ```css
> .example{
>   //尺寸计算，支持 加减乘除
>   width: calc(100% - 20px);
>   height: calc(100% = 1em);
> }
> ```

React component ref attribute

> ```javascript
> // 调用 dom 方法1
> ...
> let targetDom = this.refs.target
> ...
> <Children ref="target"/>
> 
> // 调用 dom 方法2
> ...
> let targetDom = this.target
> ...
> <Children ref={c => this.target = c}
> ```

Use functions of children component in parent component

> ```javascript
> // Parent.js
> ...
> getChildComponent(ref) {
>   this.child = ref // 获取子组件class，这里的ref即是子组件
> }
> ...
> this.child.getSomething()// 调用子组件函数方法
> ...
> <Child foo={this.foo.bind(this)}/>
> 
> 
> // Child.js
> ...
> componentDidMount() {
>   this.props.getChildComponent(this) // 这里的 this 指向子组件
> }
> 
> getSomething() {
>   console.log('Got it')
> }
> ...
> ```

reduce()

> `reduce(callback(accumulator, currentValue, currentIndex, array))`
>
> ```js
> let arr = [0, 1, 2, 3, 4]
> arr.reduce(
>   (accumulator, currentValue, currentIndex, array) => accumulator + currentValue
> )
> ```
>
> 回调状态变更历程
>
> | `callback`  | `accumulator` | `currentValue` | `currentIndex` | `array`           | `return value` |
> | :---------- | :-----------: | :------------- | :------------- | :---------------- | :------------- |
> | first call  |      `0`      | `1`            | `1`            | `[0, 1, 2, 3, 4]` | `1`            |
> | second call |      `1`      | `2`            | `2`            | `[0, 1, 2, 3, 4]` | `3`            |
> | third call  |      `3`      | `3`            | `3`            | `[0, 1, 2, 3, 4]` | `6`            |
> | fourth call |      `6`      | `4`            | `4`            | `[0, 1, 2, 3, 4]` | `10`           |
>
> 
>
> `reduce(callback(accumulator, currentValue, currentIndex, array), initialValue)`
>
> ```javascript
> let arr = [0, 1, 2, 3, 4]
> arr.reduce(
>   (accumulator, currentValue, currentIndex, array) => accumulator + currentValue,
>   10
> )
> ```
>
> 回调状态变更历程
>
> | `callback`  | `accumulator` | `currentValue` | `currentIndex` | `array`           | return value |
> | :---------- | :------------ | :------------- | :------------: | :---------------- | :----------- |
> | first call  | `10`          | `0`            |      `0`       | `[0, 1, 2, 3, 4]` | `10`         |
> | second call | `10`          | `1`            |      `1`       | `[0, 1, 2, 3, 4]` | `11`         |
> | third call  | `11`          | `2`            |      `2`       | `[0, 1, 2, 3, 4]` | `13`         |
> | fourth call | `13`          | `3`            |      `3`       | `[0, 1, 2, 3, 4]` | `16`         |
> | fifth call  | `16`          | `4`            |      `4`       | `[0, 1, 2, 3, 4]` | `20`         |

context

> ```javascript
> // define
> const {Provider, Consumer} = React.createContext(defaultValue)
> // or
> const contentContext = React.createContext(defaultValue)
> 
> 
> // provider
> <Provider value={/* some value */}>
> // or
> <contentContext.Provider value={/* some value */}>
> 
> 
> // consumer
> <Consumer>
>   {value => /* render something based on the context value */}
> </Consumer>
> // or
> <contentContext.Consumer>
>   {value => /* render something based on the context value */}
> </contentContext.Consumer>
> ```

grid - CSS

> ```css
> /* 父元素申明 grid 布局*/
> .container {
>   display: grid;
>   grid-template-columns: 100px 100px 100px 100px; /*均匀排列4列，每列100px*/
>   grid-template-rows: 100px 100px 100px 100px; /*均匀排列4行，每行100px*/
>   grid-gap: 2px; /*定义行列固定间距 2px*/
>   /* 等价拆分写法
>   grid-row-gap: 2px;
>   grid-column-gap: 2px;
>   */
> }
> 
> .item1 {
>   grid-row-start: 2; /*栅格单元，从栅格行的第2栅格线开始；单独出现，补全单个栅格单元*/
>   grid-row-end: 3; /*栅格单元，到栅格行的第3栅格线结束；单独出现，补全单个栅格单元*/
>   grid-column-start: 2; /*栅格单元，从栅格列的第2栅格线开始；单独出现，补全单个栅格单元*/
>   grid-column-end: 3; /*栅格单元，到栅格列的第3栅格线结束；单独出现，补全单个栅格单元*/
> }
> 
> .item2 {
>   grid-row: 4 / 6; /*栅格单元，从栅格行的第4栅格线开始，到栅格行的第6栅格线结束*/
>   grid-column: 4 / 6; /*栅格单元，从栅格列的第4栅格线开始，到栅格列的第6栅格线结束*/
> }
> 
> .item3 {
>   grid-row: span 2; /*栅格单元，自身跨越两行*/
>   grid-column: span 2; /*栅格单元，自身跨越两列*/
> }
> 
> .item4 {
>   grid-area: -3 / 4 / -1 / 3; /*固定顺序，row-start / column-start / row-end / column-end ;对应的行或列的起始位置可对换*/
> }
> ```
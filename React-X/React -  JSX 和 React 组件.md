# React -  JSX 和 React 组件

> https://idea2app.feishu.cn/docx/THOEdTXzGopJnGxFlLocb8wVnkf



React 是一个流行的 JavaScript 库，用于为网页或应用程序构建可重用的组件驱动的用户界面。



## JSX 

在 React 中，可以使用它的的渲染 API（ReactDOM）将此 JSX 直接渲染到 HTML DOM。 JSX 是 JavaScript 的语法扩展，所以实际上可以直接在 JSX 中编写 JavaScript。浏览器不能解析 JSX，通过转换器 Babel 将 JSX 代码编译为 JavaScript。在 React 中，可以使用它的的渲染 API（ReactDOM）将此 JSX 直接渲染到 HTML DOM。



### JSX 用法

在 JSX 中，规则略有不同。 任何 JSX 元素都可以使用自闭合标签编写，并且每个元素都必须关闭。 

```
const JSX = (
  <div>
    <p> Hello React！！</p>
  </div>
);
```



### JSX 注释

```
{/* 这是代码注释 */}
```



### JSX 渲染到 DOM 树

```
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);
// 显示到HTML页面上
ReactDOM.render(JSX,document.getElementById('root'))
```

```
ReactDOM.render(componentToRender, targetNode)
```

- 第一个参数是要渲染的 JSX 元素

- 第二个参数是要在其中渲染该组件的 DOM 节点



### 组件渲染到 DOM 树

```
ReactDOM.render(<ComponentToRender />, targetNode)
```

- 第一个参数是要渲染的 React 组件

- 第二个参数是要在其中渲染该组件的 DOM 节点



```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Hello React!</h1>
      </div>
    );
  }
};

// 渲染组件到 DOM 树
ReactDOM.render(<MyComponent/>,document.getElementById('root'))
```



## React 创建组件

- React的函数名以大写字母开头
- 元素必须用 div 标签或者幽灵节点（<>...</>）包裹，幽灵节点不会被渲染，效率比div更高



### 函数组件

函数组件是无状态函数组件。

```
const MyComponent = function() {
 return (
		 <div>
		 		<h1>test</h1>
		 </div>
  )
};
```



### 类组件

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return(
      <>
     		<h1>Hello React!</h1>
      </>
    )
  }
};
```



### 嵌套组件

```
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
      <TypesOfFruit/>
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits/>
      </div>
    );
  }
};
```
# React -  组件通信

## props 属性

组件之间传输的属性

- props 是只读对象
- props 可以传递任意数据：数字、字符串、布尔值、数组、对象、**函数、JSX**



## 父组件传递子组件

App 组件通过 props 传递数据到 ChildComponentA 和 ChildComponentB。

- 父组件传递：this.state.message
- 子组件接收：props.msg 



### 传输字符串

```react
import React from 'react';

class ChildComponentA extends React.Component {
  render() {
    return (<div>A ,  recevie msg: {this.props.msg}</div>)
  };
}

function ChildComponentB(props) {
  return (<div>B , recevie msg: {props.msg} </div>)
}

class App extends React.Component {
  state = {
    message: "App data"
  }

  render() {
    return (
      <div>
        <ChildComponentA msg={this.state.message} />
        <ChildComponentB msg={this.state.message} />
      </div>
    );
  }
}

export default App;
```



```react
const List = (props) => {
  return <p>{props.tasks.join(',')}</p>;
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        <List tasks={["walk dog", "workout"]}/>
      </div>
    );
  }
};
```



### 传递函数

**子组件调用父组件函数**

```react
class ChildComponentA extends React.Component {
  render() {
    return (<div><button onClick={this.props.getMessag}>调用父组件方法</button></div>)
  };
}

function ChildComponentB(props) {
  return (<div> <button onClick={props.getMessag}>调用父组件方法</button></div>)
}

class App extends React.Component {
  getMessag = () => {
    alert("App function")
  }

  render() {
    return (
      <div>
        <ChildComponentA msg={this.state.message} getMessag={this.getMessag} />
        <ChildComponentB msg={this.state.message} getMessag={this.getMessag} />
      </div>
    );
  }
}
```



**对象的解构赋值** 

```react
// 写法一：
function ChildComponentB(props) {
  return (<div> <button onClick={props.getMessag}>调用父组件方法</button></div>)
}


// 写法二：
function ChildComponentB({getMessag}) {
  return (<div> <button onClick={getMessag}>调用父组件方法</button></div>)
}

// 写法三：
function ChildComponentB({getMessag}) {
  const {getMessag} = props
  return (<div> <button onClick={getMessag}>调用父组件方法</button></div>)
}
```



## 子组件传递父组件

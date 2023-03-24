# React - State

## State

State 状态就是指数据，通过State可以自动更新组件。状态更新是异步的，这意味着 React 可能会把多个 `setState()` 集中在一起批量更新。与props的区别就是 state 是私有的，并且完全受控于当前组件。State 完全是组件私有的。



### 更新State

#### 初始化 state

写法一

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    // 初始化state
    this.state = {
      name: 'Initial State'
    };
    
  }
 
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```



写法二（推荐这种写法）

```
class MyComponent extends React.Component {
  // 初始化state
	state = {
		name: 'Initial State'
	}
 
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```





#### 更新state数据

```
this.setState({
  name: 'update'
});
```

#### 示例

有时候需要更新数据，从State里面获取，不建议这样操作：

```
this.setState({
  // 这里获取的数据不准确，State是异步的
  counter: this.state.counter + this.props.increment
});
```



正确写法：

```
this.setState((state, props) => ({  // state 和 props 是组件的对象
  counter: state.counter + props.increment
}));
```



example

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    // 绑定上下文，将 this 绑定到 Class 方法上
    this.toggleVisibility = this.toggleVisibility.bind(this)
  }
 
  toggleVisibility(){
    const v = this.state.visibility
    this.setState(state=>{
      if(state.visibility==true){
        return {
          visibility:false
        }
      }else{
        return {
          visibility:true
        }
      }
    })
  }
 
  render() {
    if (this.state.visibility) {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
          <h1>Now you see me!</h1>
        </div>
      );
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
}
```

#### 计时器

```
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    this.increment = this.increment.bind(this)
    this.decrement = this.decrement.bind(this)
    this.reset = this.reset.bind(this)
  }
   
  increment(){
    this.setState(state=>({
      count:state.count+1
    }));
  }
  decrement(){
    this.setState(state=>({
      count:state.count-1
    }));
  }
  reset(){
    this.setState(state=>({
      count:0
    }));
  }
   
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```


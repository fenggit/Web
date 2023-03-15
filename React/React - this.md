# React - this

- 类方法通常需要使用 `this` 关键字，以便它可以访问方法中类的属性（例如 `state` 和 `props`）
- 类里面的标签，组件是没有this的，需要手动绑定到类



```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      text: "Hello"
    };
    // 绑定button的this到当前类
		this.handleClick = this.handleClick.bind(this)
  }
  handleClick() {
    this.setState({
      text: "You clicked!"
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.text}</h1>
      </div>
    );
  }
};
```


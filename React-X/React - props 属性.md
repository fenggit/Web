# React props 属性



## Props 的默认值

通过 XComponent.defaultProps 设置组件 props 默认值，后续可以修改。

```
class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

// 指定 props 的默认值：
Greeting.defaultProps = {
  name: 'Stranger'
};

```



## Props 的类型检查

React 组件之间，通过 props 对象传递任意数据，通过设置 PropTypes 设置传递的数据类型， 进行类型检查，当数据类型不匹配的时候，会抛出警告。

官方文档：

- [PropTypes类型](https://zh-hans.reactjs.org/docs/typechecking-with-proptypes.html#gatsby-focus-wrapper)

- [如何在 React 中使用 PropTypes](https://www.freecodecamp.org/chinese/news/how-to-use-proptypes-in-react/)



```
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

// 设置quantity参数是数字类型
Items.propTypes = {quantity:PropTypes.number.isRequired}
 
class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity={123}/>
  }
};
```


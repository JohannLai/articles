# React 用 JSX 描述 UI

> JSX，是一个 JavaScript 的语法扩展

这个有趣的标签语法既不是字符串也不是 HTML。
```js
const element = <h1>Hello world!</h1>;
```

## 为什么 React 要使用 JSX
React 认为渲染逻辑本质上与其他 UI 逻辑内在耦合，比如，在 UI 中需要绑定处理事件、在某些时刻状态发生变化时需要通知到 UI，以及需要在 UI 中展示准备好的数据。

## 在 JSX 中嵌入表达式
在下面的例子中，我们声明了一个名为 name 的变量，然后在 JSX 中使用它，并将它包裹在大括号中:

```js
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

在 JSX 语法中，你可以在大括号内放置任何有效的 JavaScript 表达式。例如，1 + 1.


## JSX 特定属性

你可以通过使用引号，来将属性值指定为字符串字面量：

```js
const element = <div tabIndex="0"></div>;
```

也可以使用大括号，来在属性值中插入一个 JavaScript 表达式：

```js
const element = <img src={user.avatarUrl}></img>;
```
>警告：
> 因为 JSX 语法上更接近 JavaScript 而不是 HTML，所以 React DOM 使用 camelCase（小驼峰命名）来定义属性的名称，而不使用 HTML 属性名称的命名约定。
**例如 class name 叫 ClassName**


## JSX 防止注入攻击

React DOM 在渲染所有输入内容之前，默认会进行转义。它可以确保在你的应用中，永远不会注入那些并非自己明确编写的内容。所有的内容在渲染之前都被转换成了字符串。这样可以有效地防止 XSS（cross-site-scripting, 跨站脚本）攻击。


```js
// 后端返回
const title = response.potentiallyMaliciousInput;
// 直接使用是安全的：
const element = <h1>{title}</h1>;
```

## JSX 表示对象 （重要）

Babel 会把 JSX 转译成一个名为 `React.createElement()` 函数调用。

以下两种示例代码完全等效：

```js

const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```


```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
`React.createElement()` 会预先执行一些检查，以帮助你编写无错代码，但实际上它创建了一个这样的对象：

```js
// 注意：这是简化过的结构
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```



## JSX 提案

FaceBook 对 JSX 提出了提案，但是要注意的是，JSX是 ECMAScript 的类似 XML 的语法扩展，没有任何定义的语义。 它不打算由引擎或浏览器实现。 并不是将 JSX 纳入 ECMAScript 规范本身的建议。 它打算由各种预处理器（编译器）用来将这些 token 转换为标准 ECMAScript。

详细可以查看：https://github.com/facebook/jsx


![](https://imgkr2.cn-bj.ufileos.com/2c8025f7-304b-4fc9-9cba-598ce74cc6f1.png?UCloudPublicKey=TOKEN_8d8b72be-579a-4e83-bfd0-5f6ce1546f13&Signature=A2i1SzQ81fZIr9FlHV%252Bs1E57Xuw%253D&Expires=1609126172)

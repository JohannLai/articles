# React JSX 具体用法

React.js 中一切皆组件，用 React.js 写的其实就是 React.js 组件。我们在编写 `React.js` 组件的时候，可以继承 `React.Component` 或者是用函数组件，那么我们无论用 `component` 的 `render` 方法还是 `函数组件` 都是需要返回一个 JSX，才能正确渲染组件

## 要用一个外层元素把内容进行包裹 || 用数组带上 key

### 外层包裹

```js

render(){
  return (
    <>
      <div>第一个</div>
      <div>第二个</div>
    </>
  )
}
```

### 数组

key 的具体作用后续会继续聊。

```js

render(){
  return [
      <div key="1">第一个</div>
      <div key="2">第二个</div>
  ]
}
```

## JSX 表达式插入
在 JSX 当中你可以插入 JavaScript 的表达式，表达式返回的结果会相应地渲染到页面上。表达式用 {} 包裹。例如:

```js
render(){
  const hideTitle = true;
  return(
     <>
        { hideTitle && <div>title</div> }
        <div>content</div>
     </>
  )
}
```

当然表达式也可以进行一些运算，例如：

```js
render(){
  return(
    <div>计算 1 + 1 = { 1 + 1}</div>
  )
}
```

还可以给 html 标签的 attr 加上表达式，例如：

```js
render(){
  return(
     <div className={style.fontColorRed}>红色</div>
  )
}
```

## JSX 条件渲染

我们可以常用用 && 来表示是否渲染一个组件，就像上文那个

```js
render(){
  const hideTitle = true;
  return(
     <>
        { hideTitle && <div>title</div> }
        <div>content</div>
     </>
  )
}
```

三目运算符也可以:

```js
render(){
  const hideTitle = true;
  return(
     <>
        { hideTitle ? "不允许显示title" :  <div>title</div> }
        <div>content</div>
     </>
  )
}
```

## JSX 列表渲染
我们经常会渲染一个信息流的列表，也就是我们常说的列表渲染，那我们经常会这样做：

```js
render(){
  const news = [
    {
      title: "好消息1",
      content: "好消息内容"
    }，
    {
      title: "好消息2",
      content: "好消息内容"
    }
  ]
  return(
     <>
        {
          news.map((item, index)=>{
              return <>
                <div>{item.title}</div>
                <div>{item.content}</div>
              </>
          })
        }
     </>
  )
}
```

# JSX 变量

把 jsx 放入一个变量中，也是可以的：

```js
render(){
  const title = <h1>这是标题</h1>;
  return(
     <>
        {title}
        <div>content</div>
     </>
  )
}
```

## 总结

JSX 让数据或者事件和 UI 更紧密地连接在一起，更加方便了开发者理解 React 的使用。

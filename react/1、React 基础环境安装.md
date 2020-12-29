​React.js 基础安装

# 方式一：UMD / CDN 方式

## 步骤 1：添加一个 DOM 容器到 HTML
首先，打开你想要编辑的 HTML 页面。添加一个空的
标签作为标记你想要用 React 显示内容的位置。例如：

```html
<!-- ... 其它 HTML ... -->

<div id="like_button_container"></div>

<!-- ... 其它 HTML ... -->
```

我们给这个<div>加上唯一的 id HTML 属性。这将允许我们稍后用 JavaScript 代码找到它，并在其中显示一个 React 组件。

## 步骤 2：添加 Script 标签

接下来，在 body 结束标签之前，向 HTML 页面中添加三个 script 标签：
```html
  <!-- ... 其它 HTML ... -->

  <!-- 加载 React。-->
  <!-- 注意: 部署时，将 "development.js" 替换为 "production.min.js"。-->
  <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>

  <!-- 加载我们的 React 组件。-->
  <script src="like_button.js"></script>
```
## 步骤 3：创建一个 React 组件
```js
// ... 你粘贴的组件代码 ...

const domContainer = document.querySelector('#like_button_container');
ReactDOM.render(e(LikeButton), domContainer);  
```
就是这么简单！

# 方式二：create-react-app（常用）

##安装 nodejs

首先要确认你的电脑是否安装了 nodejs，如果没有请前往 nodejs 官网下载安装。


## 安装 create-react-app
执行以下三个命令即可开启一个 react 项目

```bash
npm install create-react-app
npx create-react-app my-app
cd my-app
npm start
```

打开就可以直接看到 react 的一个 app 页面了.







# React简介

## 一、是什么

React是一个将数据渲染为HTML视图的开源JavaScript库

## 二、谁开发的

由Facebook开发，且开源。

## 三、为什么学

- 原生JavaScript操作DOM繁琐、效率低
- 使用JavaScript直接操作DOM，浏览器会进行大量的重绘重排
- 原生JavaScript没有组件化编码方案，代码复用率低

## 四、React的特点

- 采用***组件化***模式、***声明式***编码，提高开发效率及组件复用率
- 在**React Native**中可以使用React语法进行***移动端开发***
- 使用***虚拟DOM*** + 优秀的***Diffing算法***，尽量减少与真实DOM的交互

![image-20240612095643171](C:\Users\whz\AppData\Roaming\Typora\typora-user-images\image-20240612095643171.png)

![image-20240612095706591](C:\Users\whz\AppData\Roaming\Typora\typora-user-images\image-20240612095706591.png)

## 五、学习React之前要掌握的JavaScript基础知识

- 判断this的指向
- class（类）
- ES6语法规范
- npm包管理器
- 原型、原型链
- 数组常用方法
- 模块化

# React入门

## 一、简介

### 1、官网

1. 英文官网：[https://react.dev/](https://react.dev/)
2. 中文官网：[https://zh-hans.react.dev/](https://zh-hans.react.dev/)

### 2、介绍描述

1. 用于动态构建用户界面的JavaScript库（只关注视图）
2. 由Facebook开源

### 3、React的特点

1. 声明式编码
2. 组件化编码
3. React Native编写原生应用
4. 高效（优秀的Diffing算法）

### 4、React高效的原因

1. 使用虚拟(virtual)DOM不总是直接操作页面真实DOM
2. DOM Diffing算法、最小化页面重绘

## 二、React的基本使用

### 1、效果

![image-20240612135340760](C:\Users\whz\AppData\Roaming\Typora\typora-user-images\image-20240612135340760.png)

### 2、相关js库

1. react.js:React核心库
2. react-dom.js:提供操作DOM的react扩展库
3. babel.min.js:解析JSX语法代码转为JS代码的库

```html
<script src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
<!-- 生产环境中不建议使用 -->
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
```

> [!WARNING]
>
> 在script标签中type要写成babel
>
> ```html
>  <script type="text/babel"> /* 此处要写babel*/
>  </script>
> ```

### 3、创建虚拟DOM的两种方式

1. 纯js（一般不用）

 ```js
  // 创建虚拟dom
  const VDOM = React.createElement(
    "h1",
    { id: "title" },
    React.createElement("span", {}, "Hello, React")
  ); 
  // 渲染虚拟dom到页面
  ReactDOM.render(VDOM, document.querySelector("#test"));
 ```

2. jsx方式

```js
// 创建虚拟dom
const VDOM = (// 此处不需要引号，不是字符串
  <h1>
    <span>Hello, React</span>
  </h1>
); 
// 渲染虚拟dom到页面
ReactDOM.render(VDOM, document.querySelector("#test"));
```

> [!NOTE]
>
> 关于虚拟DOM：
>
> 1. 本质是一个Object对象（一般对象）
> 2. 虚拟DOM比较“轻”，真实DOM比较“重”，因为虚拟DOM时React内部再用，无需真实DOM上那么多属性
> 3. 虚拟DOM最终会被React转化为真实DOM，呈现在页面上

## 三、React JSX

### 1、效果

### 2、JSX

1. 全称：JavaScript XML

2. react定义的一种类似于XML的js扩展语法：JS + XML

3. 本质是React.createElement(component,props, ...children)

4. 作用：用来简化创建虚拟DOM

   1. 写法：`const VDOM = <h1>Hello, React</h1>`

   2. > 注意1： 它不是字符串，也不是HTML/XML标签 

   3. > 注意2：它最终产生的就是一个js对象

      

> [!NOTE]
>
> ### jsx语法规则：
>
> 1. 定义虚拟DOM时，不需要引号
> 2. 标签中混入JS***表达式***时要用{}
> 3. 样式的类名指定不要用class，要用className
> 4. 内联样式，要用style={{key:value}}的形式去写，**-** 链接要写成小驼峰的形式
> 5. 虚拟DOM必须只有一个根标签
> 6. 标签必须闭合
> 7. 标签首字母
>    1. 若小写字母开头，则将该标签转为html中同名元素，若html中无该标签对应的同名元素，则报错
>    2. 若大写字母开头，react就去渲染对应的组件，若组件没有定义，则报错
>
> 

> 一定注意区分：【js语句（代码）】与【js表达式】
>
> 1. 表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方，下面这些都是表达式：
>    1. a
>    2. a+b
>    3. dome(1)
>    4. arr.map()
>    5. function test() {}
> 2. 语句（代码）
>    1. if() {}
>    2. for() {}
>    3. switch() {case: }

## 四、模块与组件、模块化与组件化的理解

### 1、模块

1. 理解：向外提供特定功能的js程序，一般就是一个js文件
2. 为什么要拆成模块：随着业务逻辑增加，代码越来越多且复杂
3. 作用：复用js，简化js的编写，提高js运行效率

### 2、组件

1. 理解：用来实现局部功能效果的代码和资源的集合（html/css/image等等）
2. 为什么：一个界面的功能更复杂
3. 作用：复用编码，简化项目编码，提高运行效率

### 3、模块化

当应用的js都以模块来编写的，这个应用就是一个模块化应用

### 4、组件化

当应用是以多组件的方式实现，这个应用就是一个组件化的应用

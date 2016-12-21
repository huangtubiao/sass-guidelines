# Sass 规范

> Sass 这样描述自己：Sass 是 CSS 的一个扩展，它使 CSS 的使用起来更加优雅和强大。

然而 Sass 带给我们优雅和强大的同时也给我们带来了烦恼。关于 Sass 预处理器的具体优点，官方说得很清楚了，相信你们也感受到了，对吧？我就不赘述了，我们来一起说说缺点吧。

- *嵌套带来的副作用*：CSS选择符权重增加，HTML结构与样式挂钩耦合，以及预处理器层面需要增加规范（变量和mix模块放在什么地方定义、文件如何拆解以配合@import导入、什么时候定义新的class名、什么时候使用嵌套），以方便团队合作。

- *生成冗余的代码*：使用 **混合宏** 的时候，编译出来的 CSS 清晰告诉了大家，他不会自动合并相同的样式代码，如果在样式文件中调用同一个混合宏，会产生多个对应的样式代码，造成代码的冗余，这也是 CSSer 无法忍受的一件事情。对于 **继承**，如果是基类并不存在于HTML结构时，不管调用与不调用，在编译出来的 CSS 中都将产生基类对应的样式代码。

- *增加一定的学习成本和团队维护成本*：新的技术的引入必然会增加团队的学习成本，但如果没有规范好也必然会代码上的混乱和后期维护上的困难。

## 书写格式

``` python
.btn {
    position: relative;
    top: 0px;
    display: block;
    height: 40px;
    width: 80px;
}
```

## 变量、混合宏、扩展/继承、占位符

变量、混合宏、扩展/继承、占位符给予了 CSS 具有 js 的能力，让我们书写 CSS 更加灵活，但是，我们也要知道这些所谓的能力其实 CSS 也有对应的替代方案——让HTML标签挂多个class：

Sass 变量方案：
``` python
$heightLight: red;
.title {
    color: $heightLight;
    font-size: 20px;
}
.title2 {
    color: $heightLight;
    font-size: 16px;
}
<h1 class="title"></h1>
<h2 class="title2"></h2>
```

多 class 方案：
``` python
.height-light: {
    color: red;
};
.title {
    font-size: 20px;
}
.title2 {
    font-size: 20px;
}
<h1 class="title height-light"></h1>
<h2 class="title2 height-light"></h2>
```

Sass 继承方案：
``` python
.message {
    display: block;
    color: red;
}
.success {
    @extend .message;
    border-color: #fff;
}
.error {
    @extend .message;
    border-color: red;
}
<div class="success">成功</div>
<div class="error">失败</div>
```

多 class 方案：
``` python
.message {
    display: block;
    color: red;
}
.success {
    border-color: green;
}
.error {
    border-color: red;
}
<div class="message success">成功</div>
<div class="message error">失败</div>
```

## 选择器嵌套

## 命名约定

## 组件

## 结构

## 注释

# Ref

- [编写稳健、可维护和可扩展的 Sass](https://sass-guidelin.es/zh/)

# Sass - 成熟、稳定、强大的CSS扩展语言解析器

## 使用变量

- $符号标识变量 $highlighter-color

- 规则块内定义只能在规则块内应用
- 变量值也可以引用其他变量

- 推荐使用 - 分隔变量名，也可使用_

## 嵌套CSS规则

```scss
#content {
  article {
    h1 { color: #333 }
    p { margin-bottom: 1.4em }
  }
  aside { background-color: #EEE }
}

父选择器：&
article a {
  color: blue;
  &:hover { color: red }
}
#content aside {
  color: red;
  body.ie & { color: green }
}

群组选择器
.container {
  h1, h2, h3 {margin-bottom: .8em}
}
nav, aside {
  a {color: blue}
}

子组合选择器和同层组合选择器
article > section { border: 1px solid #ccc } article为直接父元素
header + p { font-size: 1.1em } 同层相邻组合选择器
article ~ article { border-top: 1px dashed #ccc } 同层全体组合选择器

嵌套属性
nav {
  border: {
  style: solid;
  width: 1px;
  color: #ccc;
  }
}
nav {
  border: 1px solid #ccc {
  left: 0px;
  right: 0px;
  }
}
```



# 导入SASS文件

![导入Sass](C:\Users\xuxingyu\Desktop\cloudStudy\css\导入Sass.png)

- 引用Sass部分文件，以_开头

- 默认变量值 !default
- 嵌套导入 `.blue-theme {@import "blue-theme"}`

## 混合器

```scss
@mixin rounded-corners {
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
notice {
  background-color: green;
  border: 2px solid #00aa00;
  @include rounded-corners;
}

给混合器传参
@mixin link-colors($normal, $hover, $visited) {
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
a {
  @include link-colors(blue, red, green);
}
a {
    @include link-colors(
      $normal: blue,
      $visited: green,
      $hover: red
  );
}

默认参数值
@mixin link-colors(
    $normal,
    $hover: $normal,
    $visited: $normal
  )
{
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
```



## 选择器继承

```scss
.error {
  border: 1px solid red;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```


- $定义变量，可以在规则块之外定义，在规则块中定义只能用于规则块中
- sass中划线和下划线相互兼容，但是在sass中纯css部分不互通，比如类名、ID或属性名。
### 嵌套选择器和嵌套属性
- 嵌套选择器：sass在解开一个嵌套规则时就会把父选择器通过一个空格连接到子选择器的前边；&符号被父选择器直接替换,可以应用于伪类。
- \>直接子元素选择器；\+相邻元素组合器；\~同层全体组合选择器:选择所有跟在article后的同层article元素。
- 嵌套属性：把属性名从中划线-的地方断开，在根属性后边添加一个冒号:，紧跟一个{ }块，把子属性部分写在这个{ }块中。
如：
```
border: {
  style: solid;
}
//等价于
border-style: solid;
```
### @import
- import可以省略scss后缀
- 局部文件名以下划线开头，专门用于import，import时不用写前面的下划线。
- 最后一处声明有效且它会覆盖前边的值，!default：如果这个变量被声明赋值了，那就用它声明的值，否则就用这个默认值。
- 嵌套导入：允许@import命令写在css规则内，导入的东西只在该规则范围内有效。
```
//_blue-theme.scss
aside {
  background: blue;
  color: white;
}
//导入
.blue-theme {@import "blue-theme"}
//等价于
.blue-theme {
  aside {
    background: blue;
    color: #fff;
  }
}
```
- 静默注释://不会出现在生成的css文件中，/**/会。
### 混合器
- @mixin定义，@include引入，不用加引号
```
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
//生成
.notice {
  background-color: green;
  border: 2px solid #00aa00;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```
- 混合器传参
```
@mixin link-colors($normal, $hover, $visited) {
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
a {
  @include link-colors(blue, red, green);
}
//Sass最终生成的是：
a { color: blue; }
a:hover { color: red; }
a:visited { color: green; }
//可以通过$name：value来指定值
a {
    @include link-colors(
      $normal: blue,
      $visited: green,
      $hover: red
  );
}
```
- 混合器可以赋默认参数值
### 选择器继承
- @extend 选择器，继承一个选择器的所有样式
- .seriousError不仅会继承.error自身的所有样式，任何跟.error有关的组合选择器样式也会被.seriousError以组合选择器的形式继承。
```
//.seriousError从.error继承样式
.error a{  //应用到.seriousError a
  color: red;
  font-weight: 100;
}
h1.error { //应用到hl.seriousError
  font-size: 1.2rem;
}
```
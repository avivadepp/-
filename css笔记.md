不需要显示元素时，不要忘了display:none
display inline会忽略width和height,默认是display inline
外层display:table,内层display:table-cell;vertical-align:middle;text-align:center;可实现居中
使用 margin:0 auto;的盒子,必须要有width,有明确的width;只有标准流中的盒子,才能使用 margin:0 auto; 居中。
vertical-align 只对行内元素、表格单元格元素生效：不能用它垂直对齐块级元素,使用vertical-align时可以加上height和line-height，并使二者相等。
clear:指定段落的左侧或者右侧不允许浮动的元素。
content 属性与 :before 及 :after 伪元素配合使用，来插入生成内容。
column-count：n，将div中的文本分为n列
1，word-break:break-all 都换行
2，word-wrap:break-word 例子与上面一样，但区别就是它会把congratulation整个单词看成一个整体，如果该行末端宽度不够显示整个单词，它会自动把整个单词放到下一行，而不会把单词截断掉的。但是如果整个单词的长度超过了width，还是会换行。
3，word-wrap：normal，只在
word-wrap对行内元素没有效果
z-index 进行定位元素(position:absolute, position:relative, or position:fixed)

文字超出部分使用省略号：
white-space:nowrap;
overflow:hidden;
text-overflow:ellipsis;

position的默认值是static，top属性在static时不起作用
relative是相对于自身原本位置进行偏移，而不是相对于父元素，absolute是相对于父元素。fixed 和 abosulte则会改变元素的文本流。
sticky:它的行为就像 position:relative; 而当页面滚动超出目标区域时，它的表现就像 position:fixed;，它会固定在目标位置。
border占据空间，outline不占空间
resize属性允许用户调整大小
visibility: hidden;占据空间，display:none不占空间
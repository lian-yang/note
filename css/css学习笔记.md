### fCSS 学习笔记

box-sizing:border-box; 定义盒子宽度高度行为 border-box 在已设定的宽度和高度内进行绘制 inherit继承

border: 边框样式 solid 实线 dotted 点线 dashed 虚线

border-radius: 左上角 右上角 右下角 左下角

background: transparent 透明的

background-color: 设置颜色作为对象背景颜色

background-image: 设置图片作为背景图片

background-repeat: 设置背景平铺重复方向 repeat no-repeat

background-attachment: 设置背景图像是随对象内容滚动或固定的 fixed scroll

background-position: 设置对象的背景图像位置。 letf top px

a:active 是超级链接的初始状态

a:hover 是把鼠标放上去时的状况

a:link 是鼠标点击时

a:visited 是访问过后的情况

font-family: "设置字体名称"

font-weight: normal 正常 bold 加粗 bolder 特粗 lighter 细体

font-style: italic 斜体 oblique 倾斜

text-transform: capitalize 首字母大写 uppercase 大写 lowercase 小写

text-shadow: left top 阴影范围 颜色值

box-shadow: left top 阴影范围 颜色值 inset 内阴影

display: none 隐藏 block 显示 inline 一行显示 table 表格 flex 布局

overflow: visible 可见 auto 自动 hidden 隐藏 scroll 滚动条

postion: static 默认 absolute 绝对 relative 相对 fixed 固定

text-align: left right center justify 两端对齐

text-indent 段落首行文字缩进

letter-spacing: 字与字之间的间距

text-overflow: clip 不显示省略号 ellipsis 显示省略号

white-space: normal 默认 nowarp 强制不换行

text-decoration: none 无 underline 下划线 blink 闪烁 overline 上划线 line-through 贯穿线

clear: none 允许浮动 left right both 清除左右浮动

cursor: pointer 手指 move 移动 url() …

nth-child(n) n从1开始算起  odd 基数 even 偶数

background: linear-gradient(direction, color-stop1, color-stop2, ...) 线性渐变

background: radial-gradient(center, shape size, start-color, last-color)  径向渐变

transition: 属性 时间 速度曲线 何时开始

transform: translate(x,y) 转换 scale(x,y) 缩放 rotate(angle) 旋转 skew(x,y) 倾斜

list-style: none 不显示列表项标记

￼

> css技巧参考 https://segmentfault.com/a/1190000020899202#articleHeader2
>

使用text-align-last对齐两端文本

text-align-last: justify;

通过:nth-child()筛选指定的元素设置样式

:nth-child(odd) 奇 :nth-child(even) 偶 :nth-child(n+6):nth-child(-n+10) 选中第6个开始到倒数10个

使用:not()去除无用属性

:not(:nth-child(-n+3)) 去除倒数3个

object-fit: cover; object-fit: contain; object-fit: fill; object-fit: scale-down;

使用overflow-x排版横向列表 通过flexbox或inline-block的形式横向排列元素，对父元素设置overflow-x:auto横向滚动查看

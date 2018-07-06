css
========
## 选择器
### 1.基础选择器
一些简单的选择器

##### 示例1

````
/*元素选择器*/
body{
    background-color:red;
}
````

##### 示例2

````
/*类选择器和ID选择器*/
#id{
    background-color:red;
}

.class{
    background-color:red;
}
````

##### 示例3

````
/*属性选择器*/
[src]{
    background-color:red;
}

[src=http://ronghui.pro]{
    background-color:red;
}

[src～=]{
    background-color:red; /*属性值以空格分割*/
}

[src^=http]{
    background-color:red;
}

[src$=.pro]{
    background-color:red;
}

[src*=ronghui]{
    background-color:red;
}

[src|=]{
    background-color:red; /*属性值以-链接*/
}
````

##### 示例4

````
/*结构选择器*/
div button{
    background-color:red;
}

.class>#id{
    background-color:red;
}

.class+#id{
    background-color:red;
}
.class~#id{
    background-color:red;
}
````

### 2.伪类选择器

##### 示例1

````
/*a标签伪类*/
a:link{
    background-color:red;
}

a:visit{
    background-color:red;
}
````

##### 示例2

````
/*动态伪类*/
div:hover{
    background-color:red;
}

div:active{
    background-color:red;
}

div:focus{
    background-color:red;
}
div:lang(){
    background-color:red;
}
````

##### 示例3

````
/*子元素匹配伪类*/
div:first-child{
    background-color:red;
}

div:last-child{
    background-color:red;
}

div:only-child{
    background-color:red;
}

div:nth-child(1){
    background-color:red;
}

div:nth-last-child(1){
    background-color:red;
}

div:empty{
    background-color:red;
}
````

##### 示例4

````
/*兄弟元素匹配伪类*/
div:first-of-type{
    background-color:red;
}

div:last-of-type{
    background-color:red;
}

div:only-of-type{
    background-color:red;
}

div:nth-of-type(1){
    background-color:red;
}

div:nth-last-of-type{
    background-color:red;
}
````

##### 示例5

````
/*状态匹配伪类*/
div:ochecked{
    background-color:red;
}

div:enabled{
    background-color:red;
}

div:disabled{
    background-color:red;
}
div:target{
    background-color:red;
}
````

### 3.伪元素

##### 示例1

````
p:first-letter{
    color:red;
}

p:first-line{
    color:red;
}
p:before{
    content:"ronghui";
    color:red;
}
p:after{
    content:"ronghui";
    color:red;
}
````

## 值和单位

### 1. 颜色

##### 示例1

````
/*RGB颜色*/
div{
    color:rgb(0,0,0);
}
/*十六进制颜色*/
div{
    color:#fff;
}
/*颜色名*/
div{
    color:red;
}
````

### 2.绝对长度

##### 示例1

````
/*英尺(in)|毫米(mm)|厘米(cm)|点(pt)|派卡(pc)*/
div{
    width:1in;
    width:1mm;
    width:1cm;
    width:1pt;
    width:1pc:
}
````

### 3. 相对长度

##### 示例1

````
/*em|ex|px*/
div{
    width:1px;
    width:1em;
    width:2ex;
}
````

### 4. 关键字

#### 示例1

````
/*none|inhert*/
div{
    color:inhert;
    list-style:none;
}
````

### 5. 角度值

##### 示例1

````
/*角度(deg)|梯度(grad)|弧度(rad)*/
````

## 字体

### 1.字体系列

##### 示例1

````
/*通用字体*/
a{
    font-family:sans-self;
}
````

##### 示例2

````
/*指定字体*/
a{
    font-family:heiti,sans-self;
}
````

### 2. 字体加粗

##### 示例1

````
/*normal|bold|bolder|lighter|inhert*/
p{
    font-weight:bold;
}
````

##### 示例2

````
/*数字值100-900*/
p{
    font-weight:500;
}
````

### 3. 字体大小

##### 示例1

````
/*关键字 十一个*/
p{
    font-size:narmal;
}
````

##### 示例2

````
/*数字值*/
p{
    font-size:20px;
}
````

### 4. 风格和变形

##### 示例1

````
/*风格*/
p{
    font-style:italic;
}
````

##### 示例2

````
/*变形*/
p{
    font-variant:small-caps;
}
````

### 5.字体匹配

##### 示例1

````
/*@font-face*/
@font-face{
    font-family:rong;
    url:http://ronghui.pro;
}
p{
    font-famliy:rong;
}
````
## 文本

### 1. 缩进

##### 示例1

````
/*text-indent*/
p{
    text-indent:5px;
}
````

### 2. 水平对齐

##### 示例1

````
/*text-align*/
p{
    text-align:center;
}
````

### 3. 行高

##### 示例1

````
/*line-height*/
p{
    line-height:2px;
}
````

### 4. 垂直对齐文本

##### 示例1

````
/*vertical-align*/
p{
    vertical-align:center;
}
````

### 5. 间隔

##### 示例1

````
/*word-spaceing|letter-spaceing*/
p{
    word-spaceing:2px;
    letter-spaceing:2px;
}
````

### 6. 文本装饰

##### 示例1

````
/*text-decoration*/
p{
    text-decoratin:none;
}
````

### 7. 文本转换

##### 示例1

````
/*text-translate*/
p{
    text-translate:upercase;
}
````

### 8. 文本阴影

##### 示例1

````
/*text-shadow*/
p{
    text-shadow:5px;
}
````

### 9. 空白符处理

##### 示例1

````
/*write-space*/
p{
    write-space:normal;
}
````

### 10. 文本方向

##### 示例1

````
/*direction*/
p{
    direction:rtl;
}
````

##### 示例2

````
/*unicode-bdi*/
p{
    unicode-bidi:bidi-override;
}
````

## 框

### 1.基本框
由内容、内边距、边框、外边距组成的矩形

##### 示例1

````
p{
    margin:0px;
    padding:0px;
    border:solid,5px;
    width:20px;
    height:50px;
}
````

### 2. 包含块
元素相对于包含块摆放

##### 示例1

````
/*div的包含块是body*/
<body>
    <div></div>
</body>
````

### 3. 块级元素

##### 示例1

````
/*水平格式化*/
/*水平居中*/
p{
    margin:auto;
    padding:0px;
    width:30px;
}
````

##### 示例2

````
/*垂直格式化*/
/*不会垂直居中*/
p{
    margin:auto; /*auto=0*/
    padding:0px;
    width:30px;
}
````
##### 示例3

````
/*外边距合并*/
li{
    margin-top:10px;
    margin-bottom:15px
}
````

### 4. 行内元素

##### 示例1

````
/*行布局*/
````

##### 示例2

````
/*垂直对齐对行的影响*/
````

### 5. 改变元素显示

````
/*display*/
````

### 6. 行内块元素

## 外边距、边框、内边距

### 1. 外边距

##### 示例1

````
/*margin*/
p{
    margin:10px;
}
span{
    margin:10px; //仅左右有效
}
````

##### 示例2

````
/*重复*/
p{
    margin:10px;
}
p{
    margin:10px 15px;
}
p{
    margin:10px 0.2em 10px;
}
````

##### 示例3

````
/*单个外边距*/
p{
    margin-top:10px;
    margin-right:10px;
    margin-bottom:10px;
    margin-left:10px;
}
````

### 2. 边框

##### 示例1

````
/*边框样式*/
p{
    bolder-style:solid;
}
````

##### 示例2

````
/*边框大小*/
p{
    bolder-left-width:10px;
}
````

##### 示例3

````
/*边框颜色*/
p{
    bolder-top-color:red;
}
````

### 3. 内边距

##### 示例1

````
/*内边距*/
p{
    padding:10px;
}
````

##### 示例2

````
/*单边内边距*/
p{
    padding-top:10px;
    padding-right:15px;
    pading-bottom:12px;
    padding-left:8px;
}
````

## 颜色和背景

### 1.前景色

##### 示例1

````
/*前景色*/
p{
    color:red;
}
````

### 2.背景

##### 示例1

````
/*背景颜色*/
p{
    background-color:red;
}
````

##### 示例2

````
/*背景图像*/
p{
    background-image:url();
}
````

##### 示例3

````
/*背景图像重复*/
p{
    background-rapet:rapet-y;
}
````

##### 示例4

````
/*背景定位*/
p{
    background-position:center;
}
````

##### 示例1

````
/*背景关联*/
p{
    background-attachment:fixed;
}
````

## 浮动和定位

### 1.float

##### 示例1

````
/*浮动*/
p{
    float:left;
}
````

### 2. 定位

##### 示例1

````
/*定位的类型*/
p{
    position:relative|static|absolute|fixed|flex;
}
````

##### 示例2

````
/*偏移属性*/
p{
    position:relative;
    top:5px;
    right:5px;
    bottom:5px;
    left:5px;
}
````

##### 示例3

````
/*限制高度和宽度*/
p{
    min-widht:10px;
    min-height:10px;
    max-width:50px;
    max-height:50px;
}
````

##### 示例4

````
/*内容溢出裁剪*/
p{
    overflow:hidden;
}
p{
    clip:rect(2px,2px,2px,2px);
}
````

##### 示例5

````
/*元素可见性*/
p{
    visibility:hidden;
}
````

##### 示例6

````
/*绝对定位*/
p{
    position:absolute;
}
````

##### 示例7

````
/*相对定位*/
p{
    position:relative;
}
````

##### 示例8

````
/*固定定位*/
p{
    position:fixed;
}
````

##### 示例9

````
/*层叠*/
p{
    z-index:999;
}
````
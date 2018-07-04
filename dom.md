DOM
==========

## DOM
### 1. 节点层次
DOM将html等描绘成一个由多层节点构成的结构，节点分为不同的类型。

#### Node类型

js中所有节点类型都继承自Node类型

##### 示例1

````
//每一个节点都有一个nodeType属性，表明节点的类型共有12个数字常量对应
/*Node.ELEMENT_NODE(1)
Node.ATTRIBUTE_NODE(2)
Node.TEXT_NODE(3)
Node.CDATA_SCETION_NODE(4)
Node.ENTITY_REFERENCE_NODE(5)
Node.ENTITY_NODE(6)
Node.PROCESSING_INSTRUCTION(7)
Node.COMMENT_NODE(8)
Node.DOCUMENT_NODE(9)
Node.DOCUMENT_TYPE_NODE(10)
Node.DOCUMENT_FRAGMENT_NODE(11)
Node.NATION_NODE(12)
nodeName值是标签名
nodeValue null*/
````

##### 示例2

````
//节点关系
//子节点
var child=someNode.childNodes
var firstChild=someNode.childNodes[0]
child[0]==firstChild //true
//父节点
var parent=someNode.parentNode //唯一
//同胞节点
var firstNode=someNode.previousSibling
if(firstNode === null){
    alert("someNode is firstChildNode");
};
var lastNode=someNode.nextSibling
if(lastNode === null){
    alert("someNode is lastChildNode");
};
````

##### 示例3

````
//操作节点
var add=someNode.appendChild(node);
var insert=someNode.insertNode(newNode,node); //前入
var rep=someNode.replaceNode(newNode,node);
var rem=someNode.replaceNode(node);
var cloneNode=someNode.cloneNode(true); //true深复制,false潜复制
````

#### Document类型
js中Document类型表示文档

##### 示例1

````
//子节点
var son = documentElement //指向html标签
var body = document.body
````

##### 示例2

````
//文档信息
var title = document.title 
var url = document.URL //https://ronghui.pro/blog
var domain = document.domain //ronghui.pro
var referrer = document.referrer //null
````

##### 示例3

````
//查找元素
var id = document.getElementById("name");
var tag = document.getElementByTagName("name")
````

##### 示例4

````
//特殊集合
var a = document.anchors //返回带name特性的<a>元素
var forms = document.forms //返回文档所有的<from>
var images = document.images //返回所有的<img>
var link = document.links
````

##### 示例5

````
//文档写入
document.write("<p>ronrhui<\/p>") //写入
document.writeln("<p>ronrhui<\/p>")  //自动在结尾添加换行符
document.close;document.open //打开和关闭网页的输出流
````

#### Element类型
用于表现xml和html元素

##### 示例1

````
//html元素
var div = document.getElementById("myDiv");
div.id="mydiv";
````

##### 示例2

````
//取得特性
var div = document.getElementById("myDiv");
alert(div.getAttribute("id")); //myDiv
````

##### 示例3

````
//设置特性
div.setAttribute("id","mydiv");
````

##### 示例4

````
//创建属性
var element = document.createElement("div");
````

#### Text类型
表示文本节点

##### 示例1

````
//创建文本节点
var textNode = document.createTextNode;
````

##### 示例2

`````
//规范化文本节点，合并文本节点
var element = document.createElement("div");
var textNode = document.createTextNode("rong");
element.appendChild(textNode);
var anotherNode = document.createTextNode("hui");
element.appendChild(anotherNode);

document.body.appendChild(element);

element.normalize(); //合并文本节点
`````

##### 示例3

````
//分割文本节点
var element = document.createElement("div");
var textNode = document.createTextNode("rong");
element.appendChild(textNode);
document.body.appendChild(element);
element.firstChild.splitText(2);
````

### 2. DOM扩展

#### 选择符API
根据css选择符匹配DOM元素

##### 示例1

`````
//querySelect()
var body =document.querySelect("body");
`````

##### 示例2

````
//querySelectAll()
var select=document.getElementById("navigate").querySelectorAll(".list")
````

##### 示例3

````
//matchesSelect()
var boo = document.body.matchesSelect("body.class"); //true or false
````

#### 元素遍历

##### 示例1

````
// 五个属性
````

#### HTML5

##### 示例1

````
//与类相关的扩充
var class = document.getElementClassName("rong")

class.classList.add("hui");
var contains = class.classlist.contains("hui"); // true
class.classList.remove("hui");
class.classList.toggle("hui")
````

##### 示例2

````
//焦点管理
var button = document.getElementById("myButton");
button.focus();
alert(document.activeElement === button); //true;
````

##### 示例3

````
//HTMLDocument的变化
var state = document.readyState; //loading complete
var compat = document.compatMode;  //CSS1Compat BackCompat
var head = document.head
````

##### 示例4

````
//字符集属性
document.charset="UTF-8";
````

##### 示例5

````
//自定义数据属性
var div = document.getElementById("myDiv")
div.dataset.selfData=233;
````

##### 示例6

````
//插入标记
var div = document.getElementById("myDiv);
var element = document.createElement("div");
var btn = document.createElement("button");
div.appendChild(btn);
div.innerHTML(element);

div.outerHTML="<artical>this is div</artical>";

div.insertAdiacentHTML("beforebegin","<p>this is div</p>");
div.insertAdiacentHTML("beforeend","<p>this is div</p>");
div.insertAdiacentHTML("afterbegin","<p>this is div</p>");
div.insertAdiacentHTML("afterend","<p>this is div</p>");
````


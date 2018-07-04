事件
=====

## 1. 事件流
描述从页面接收事件的顺序

### 事件冒泡
从具体元素到不具体的节点

### 事件捕获
从不具体节点到具体的元素

### DOM事件流
三个阶段，事件捕获阶段、处于目标阶段、事件冒泡阶段

## 2. 事件处理程序

### HTML事件处理程序
使用与事件处理程序同名的HTML特性来实现事件

##### 示例1

````
//将脚本写入标签中
<input type="button" value="click me" onclick="alert("clicked")"></input>
//也在标签中引用脚本
````

### DOM0级事件处理程序

##### 示例1

````
//元素的事件处理属性
var btn =document.getElementById("myDiv");
btn.onclick = function(){
    alert("click");
};
````

### DOM2级事件处理程序

##### 示例1

````
//addEventListener
var btn = document.getElementById("myDiv");
btn.addEventListener("click",function(){
    alert(this.id);
},false);
````

##### 示例2

````
//removeEventListener
var btn = document.getElementById("myDiv");
function handler(){
    alert(this.id);
};
btn.addEventListener("click",handler,false);
btn.removeEventListener("click",hander,false);
````

### IE事件处理程序

##### 示例1

````
//attachEvent() detachEvent()
var btn = document.getElementById("myDiv");
function handlera(){
    alert(this.id);
};
btn.attachEvent("onclick",handler);
btn,detachEvent("onclick",handler);
````

### 跨浏览器事件处理

##### 示例1

````
var EventUtil = {
    addHandler:function(element,type,handler){
        if(element.addEventListener){
            element.addEventListener(type,handler,false);
        }else if(element.attachEvent){
            element.attachEvent("on"+type,handler);
        }else{
            element["on"+type] = handler;
        };
    },
    removeHandler:function(element,type,handler){
        if(element.removeEventListener){
            element.removeEventListener(type,handler,false);
        }else if(element.detachEvent){
            element.detachEvent("on"+type,handler);
        }else{
            element["on"+type] = unll;
        };
    }
};
````

## 3. 事件类型

### UI事件

##### 示例1

````
//load事件
var btn = document.getElementById("myDiv");
btn.load=function(){
    alert("btnLoaded");
};
````

##### 示例2

````
//unload事件
var btn = document.getElementById("myDiv"){
    alert("binUnloaded");
};
````

##### 示例3


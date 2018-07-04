js函数与对象
==========
## 函数
### 1. 定义
    1.1函数声明
    1.2函数表达式

#### 示例

````
function name(){} //函数声明
var name=function(){}//函数表达式，匿名函数作用域为全局作用域
````
### 2. 递归
函数在函数中调用自己

#### 示例

````
var recursive =(function f(num){
    if(num <= 1){
        return 1;
    }else{
        return num * f(num-1);
    }
});
//利用递归函数实现简单的阶乘，使用命名函数表达式的方法来实现
````
### 3. 闭包
有权访问另一个函数作用域中的变量的函数

#### 示例1

````
//创建简单闭包
function createComparisonFunction(porpertyName){
    return function(object1,object2){
        var value1 = object1[propertyName];
        var value2 = object2[propertyName];

        if(value<value2){
            return -1;
        }eles if(value1>value2){
            return 1;
        }else{
            return 0;
        }
    };
}
````

#### 示例2

````
//闭包只能取得包含函数中任何变量的最后一个值
function createFunctions(){
    var result=[]

    for (var i=0;i<10;i++){
        result[i]=function(){
            return i;
        };
    }
    return result;
}
//修改 创建匿名函数来使函数复合预期
function createFunctions(){
    var result=[]

    for (var i=0;i<10;i++){
        result[i]=function(num){
            return function(){
                return num;
            }
        };
    }
    return result;
}
//匿名函数的参数num储存了i 因此能返回不同的值
````

#### 示例3

````
//闭包中使用this对象会导致一些问题
var name = "the window";

var object = {
    name : "my object",

    getNameFunc : function(){
        return function(){
            return this.name;
        };
    }
};

alert(object.getNameFunc()()); //the window 非严格模式下
//修改 将外部作用域的this对象保存在闭包能够访问的变量中
var name = "the window";

var object = {
    name : "my object",

    getNameFunc : function(){
        var that =this  //将外部的this对象保存到变量that里
        return function(){
            return that.name;
        };
    }
};

alert(object.getNameFunc()()); //my object
````

#### 示例4

````
//闭包会导致函数执行后一些变量不会被销毁，因此以将变量设置为null的方式来解除引用
function assignHandler(){
    var element = document.getElementById("someElement");
    var id = element.id

    element.onclick = function(){
        alert(id);
    };

    element = null; //解除对DOM对象的引用，回收其占用的内存
}
````

### 4. 模仿块级作用域
语句中的变量不会随语句结束而被销毁

#### 示例

````
//将语句放入函数中 模仿块级作用域
function outputNumbers(count){
    (function(){
        for(var i=0;i< count;i++){
            alert(i);
        }
    })();
}
````

### 5. 私有变量
js私有变量，即不能在函数外部访问的变量是为此函数的私有变量
特权方法，用于访问私有变量的公有方法

#### 示例1

````
//在构造函数中创建特权方法
function MyObject(){
    var privateVariable = 10;//私有变量

    function privateFunction(){
        return false;
    } //私有函数

    //特权方法
    this.publicMethod = function(){
        privateVariable++;
        return privateFunction();
    };
}
````

#### 示例2

````
//在私有作用域中定义私有变量或函数，也可以创建特权方法
(function(){

    //私有变量和私有函数
    var privateVirable = 10;
    function privateFunction(){
        return false;
    };

    //构造函数,无var在严格模式下会报错
    MyObject = function(){};

    //特权方法
    myObject.prototype.publicMethod= function(){
        privateVirable++;
        return privateFunction();
    };
}
)();
````

#### 示例3

````
//模块模式为只有一个对象的实例(单例)创建私有变量和特权方法
var singLeton=function(){
    //私有变量和函数
    var privateVirable = 10;

    function privateFunction(){
        return false;
    }

    //特权方法
    return{
        publicProperty:true;

        publicMethod:function(){
            privateVirable++
            return privateFunction();
        }
    };
}();
````

#### 示例4

````
//增强模块模式，为单例添加属性和方法
var singLeton=function(){
    //私有变量和函数
    var privateVirable = 10;

    function privateFunction(){
        return false;
    }

    //创建对象
    var object=new CustomType();

    //添加特权方法
    object.publicProperty=true;
        
    publicMethod:function(){
        privateVirable++;
        return privateFunction();
    };

    //返回对象
    return object
}();
````

### 6. 总结

- 函数表达式和函数声明可以定义一个函数
- 递归为函数在函数中调用自己，应避免直接使用函数名
- 返回一个匿名函数即为简单的闭包，使用闭包要注意变量、this、内存
- 将一些变量和语句放入函数中来模仿块级作用域
- 函数内部的变量、方法为私有，利用特权方法可以实现访问内部数据

## 对象

### 1. 理解对象
定义一个对象，并定义和读取函数特性

#### 示例1

````
//定义一个对象
var person ={
    name : "Ronghui",
    age : "23",
    ability:"strat",

    sayName: fuction(){
        alert(this.name);
    }
}
````

#### 示例2

````
//对象的数据特性
/*
[[Configurable]] 能否重新定义属性 默认ture
[[Enumerable]]  能否通过for in迭代属性 默认ture
[[Writable]]    能否修改属性的值
[[Value]]       保存属性的数据值
Object.defineProperty()方法可以修改函数的数据特性

var person ={
    name : "ronghui"
}
Object.defineProperty(person,"name",{
    writable:false;
    value:"ronghui2"
})

alert(person.name)
````

#### 示例3

````
//访问器属性
/*
[[Get]] 读取属性时调用的函数，默认值为undefined
[[Set]] 写入属性时调用的函数，默认值为undefined
Object.defineProperty()方法来定义访问器属性
*/
var person ={
    _birth:1995,
    old:0
};

Object.defineProperty(person,"year",{
    get: function(){
        return this._birth;
    },
    set: function(newValue){
        if(newValue>1995){
            this.old=newValue-1995
        }
    }
});

person.year=2018;
alert(person.old);
````

#### 例4

````
//定义多个属性 Object.defineProperties()方法
var book ={};

Object.defineProperties(book,{
    _year:{
        value:2004
    },
    edtion:{
        value:1
    },

    year:{
        get:function(){
            return this._year
        },
        set:function(newValue){
            if(newValue>2004){
                this._year=newValue;
                this.edtion+=newValue -2004;
            }
        }
    }
})
````

### 2. 创建对象
构造函数和对象字面量都可以创建单个对象，但有明显缺点

#### 示例1

````
//工厂模式 抽象创建对象的具体过程，以函数封装创建对象的细节
function createPerson(name,age,job){
    o.name=name;
    o.age=age;
    o.job=job;
    o.sayName=function(){
        alert(this.name);
    }
    return o;
}
//工厂模式下无法识别对象
````

#### 示例2

````
//构造函数模式
function Person(name,age,job){
    this.name=name;
    this.age=age;
    this.job=job;
    this.sayName=function(){
        alert(this.name);
    };
}
````

#### 示例3

````
//原型模式
function Person(name,age,job){
    Person.prototype.name="ronghui";
    Person.prototype.age="23";
    Person.prototype.job="font-end"
    person.prototype.sayName=function(){
        alert(this.name);
    }
}
````

#### 示例4

````
//组合使用构造函数模式和原型模式
function Person(name,age,job){
    this.name=name;
    this.age=age;
    this.job=job;
    this.friebds=["xu","yi"];
}
Person.propertype={
    constructor:Person,
    sayName:function(){
        alert(this.name);
    }
}
````

#### 示例5

````
//动态原型模式
function Person(name.age,job){
    this.name=name;
    this.age=age;
    this.job=job;

    if(typeof this.sayName !="function"){
        Person.propertype.sayName=function(){
            alert(this.name);
        }
    }
}
````

#### 示例6

````
//寄生构造函数模式
function Person(name,age,job){
    var o=new Object();
    o.name=name;
    o.age=age;
    o.job=job;
    o.sayName=function(){
        alert(this.name);
    };
    return o;
}
````

#### 示例7

````
//稳妥构造模式
function Person(name,age,job){
    //创建要返回的对象
    var o =new Object();
    //在此定义私有变量和函数

    //添加方法
    o.sayName=function(){
        alert(name);
    }

    //返回对象
    return o;
}
````

### 3. 继承
ECMAscript只支持依靠原型链实现的继承

#### 示例1

````
//原型链

//定义构造函数
function superType(){
    this.property=true;
}
//添加原型
superType.prototype.getSuperValue=function(){
    return this.property
};
//定义继承函数
function subType(){
    this.subproperty=false;
}
//继承superTYpe
subType.prototype=new superType();

subType.prototype.getSubValue=function(){
    return this.subproperty;
}

var instance = new SubType()
alert(instance.getSuperValue())
````

#### 示例2

````
//借用构造函数实现继承
function superType(){
    this.colors=["red","green","blue"];
}
function subType(){
    superType.call(this);
}
````

#### 示例3

````
//组合继承
function superType(name){
    this.name=name;
    this.colors=["red","blue","green"]
}
superType.prototype.sayName=function(){
    alert(this.name);
}
//继承属性
function subType(name,age){
    superType.call(this,name)
    this.age=age;
};
//继承方法
subType.prototype=new superType;
subType.prototype.constructor=superType;
subType.prototype.sayAge=function(){
    alert(this.age);
};
````

#### 示例4

````
//原型式继承
function object(o){
    function f(){};
    f.prototype=o;
    return new f();
};
````

#### 示例5

````
//寄生式继承
function createAnother(original){
    var clone=Object(original);
    clone.sayHi=function(){
        alert("hi");
    };
    return clone;
}
````

#### 示例6

````
//寄生组合式继承
function inhertPrototype(subType,superType){
    var prototype=object(superType.prototype);
    prototype.constructor=subType;
    subType.prototype=prototype;
};
````
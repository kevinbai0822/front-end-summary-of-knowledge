### 前端之javascript篇
1. 
```
null == undefined //true(undefined派生自null，所以返回true)

```
null和undefined的区别
null表示没有对象，即该处不应该有值。
undefined表示“缺少值”，就是此处应该有一个值，但是还没有定义。
typefof(undefined)的返回结果为undefined,typeof(null)的返回结果为Object
如果声明一个值但是不对它进行赋值的话，它为undefined;

2. 可以对元素的margin设置百分数，百分数是相对于父元素的width计算，不管是margin-top/margin-bottom还是margin-left/margin-right。（padding同理）;

3. 获取原型上的自定义属性，使用hasOwnProperty();

4. 空字符串判断为false

```
'' == false //true
'' === false //false
```


5. " " null在Number()默认转换为0;

6. 短路与`&&`如果第一项为true直接返回第二项，第二项不需要进过计算  
短路或`||`，如果第一项为true，则返回true，如果第一项为false，则直接返回第二项，第二项不需要经过计算;

7. 只有实例对象上不存在的属性方法，才会去原型对象上查找，如果原型对象还没有这个属性方法，就查找原型对象的原型对象，直至找到Object.prototype.__proto__;(原型链的概念);

8. preventDefault()用于阻止默认的事件;

9. js中数字跟字符串进行算术运算时，js会先将字符串转换成数字，如果字符串无法转换成数字（比如字符串中包含非数字字符），则返回结果为NaN;

10. a标签的onclick事件会先于href跳转,IE8以上的版本可以不写href直接使用onclick调用js函数，但是IE6对此不支持;

11. isNaN方法会将字符串转换成数字，当字符串中含有非数字时，isNaN返回true，否则返回false;

12. 如果事先声明了一个变量并且赋值，再次声明该变量时，它的值不变，变量均为对象，当你声明一个变量时，就是创建了一个对象;未声明的变量被赋值之后，它会自动变为全局变量;

13. 函数及变量的声明都会被提升到函数的最顶部;(变量提升)

14. use strict指令只运行出现在脚本或者函数的开头。严格模式：不允许使用未声明的变量、不允许删除变量或对象、不允许删除函数、不允许变量重名、不允许使用八进制、不允许使用转义字符、不允许对只读属性赋值、不允许对一个使用getter()方法读取的属性进行赋值、不允许删除一个不允许删除的值、变量名不能使用“eval”“arguments”字符串、禁止this关键字指向全局对象、新增保留关键字，此外严格模式也有作用域，函数里的严格模式只针对局部;

15. call()和apply()的区别  
两者都是将函数绑定到另外一个对象上去运行，不同的是apply的第二个参数是一个数组，它将多个参数组合成一个数组传入;

16. js中所有函数都能访问它们上一层的作用域，js支持嵌套函数，嵌套函数支持访问上一层的函数变量，如果想访问一个函数的局部变量，可以在内部再定义一个函数并且返回，返回的函数称为闭包，闭包可以使局部变量始终保存在内存中，不会因为函数执行完就被清除;

17. 事件冒泡和事件捕获  
事件捕获先发生，从document开始最后再到document
addEventListener(event,fn,useCapture)；第三个参数用来设置事件是在事件捕获时执行还是在事件冒泡时执行 ;

18. hasOwnProperty：是用来判断一个对象是否有你给出名称的属性或对象。不过需要注意的是，此方法无法检查该对象的原型链中是否具有该属性，该属性必须是对象本身的一个成员。
isPrototypeOf:是用来判断要检查其原型链的对象是否存在于指定对象实例中，是则返回true，否则返回false;

19. 当一个值为false的Boolean对象放到条件语句当中的时候，Boolean对象的值会被当作true来计算，但是它本身的值并没有改变，依然是false，字符串在if判断里是true，空字符串为false;

20. Javascript中，由于其变量内容不同，变量被分为基本数据类型变量和引用数据类型变量。基本类型变量用八字节内存，存储基本数据类型(数值、布尔值、null和未定义)的值，引用类型变量则只保存对对象、数组和函数等引用类型的值的引用(即内存地址)。

21. 原型与原型链  
原型：在js中，每当定义一个对象(函数)，对象中都会包含一些预定义的属性。其中函数对象的一个属性就是原型对象prototype，普通对象没有prototype，但是有__proto__属性。原型对象其实就是普通对象。原型对象都有一个constructor属性，用来引用它的函数对象。  
原型链：js在创建对象的时候，都会有一个叫做__proto__的内置属性，用于指向创建它的函数对象的原型对象prototype，由这个__proto__串起来的直到Object.prototype.__proto__为null的链叫做原型链。

22. js的设计模式  
1) 工厂模式  
工厂模式类似于生活中的工厂，可以生产大量相似的商品，去做同样的事情、实现同样的效果。
```
function person(name, age) {
    var o = new Object();
    o.name = name;
    o.age = age;
    o.getMsg= function() {
        alert(this.name + this.age);
    }
    return o;
}
 
var el = person('kevin',25);
```
工厂模式为了解决多个需要重复实例化的对象的问题，但是工厂对象不能识别对象的类型，无法知道他们是哪个对象的实例。可以将具体的业务逻辑放到子类中重写，父类只作为一个抽象类定义一般的处理方法。

2) 
I.构造函数模式  

构造函数模式和工厂模式的区别:  
1.函数名首字母为大写
2.没有显示的创建对象，直接将属性和方法赋值给this对象
3.没有return语句
4.能够识别对象（这是构造函数模式和工厂模式最大的区别）
```

function Person(name,age){
    this.name = name;
    this.age = age;
    this.getMsg = function(){
        alert(this.name + this.age);
    }
}

var people1 = new Person('mike',18);
var people2 = new Person('kevin',23);
console.log(people1.name); //mike
console.log(people2.name); //kevin
```
构造函数模式每次创建实例的时候都要重新创建一次方法，而对象的方法是相同的。

II.原型模式

```
function Person(){
    Person.prototype.name = 'kevin';
    Person.prototype.age = 25;
    Person.prototype.getMsg = function(){
        alert(this.name + this.age);
    }
}

var man = new Person();
```
原型模式省略了传递初始化参数，所有实例默认取得相同的值，由于共享属性，如果一个实例修改了引用，其他的实例也会跟着变化。

III.组合构造函数和原型模式
```
function Person(name,age){
    this.name = name;
    this.age = age;
}

Person.prototype.getMsg = function(){
    alert(this.name + this.age);
};
```
其中构造函数模式用于定义实例属性，原型模式用于定义方法和共享属性，每个实例都有自己的实例属性，同时又共享方法，最大程度节省内存空间。

IV.动态原型模式
```
function Person(name,age){
    this.name = name;
    this.age = age;
    
    if(typeof this.getMsg != 'function'){
        Person.prototype.getMsg = function(){
            alert(this.name + this.age);
        }
    }
}

var man  = new Person('kevin',25);
```
动态原型模式将所有信息封装在构造函数中，第一个对象实例化时初始化原型，通过判断该方法是否有效选择是否需要初始化原型。

V.寄生构造函数模式
```
function Person(name, age) {
    var o = new Object();
    o.name = name;
    o.age = age;
    o.getMsg= function() {
        alert(this.name + this.age);
    }
    return o;
}
 
var el = new Person('kevin',25);
```
构造函数在不返回值的情况下默认返回新实例对象。

VI.稳妥构造函数模式  
```
function Person(name, age) {
    var o = new Object();
    o.getMsg= function() {
        alert(this.name + this.age);
    }
    return o;
}
```
稳妥对象指的是没有公共属性，而且其方法也不引用this的对象，适合在安全的环境或者防止数据被更改的时候使用。

3) 单体模式（单例模式）  
单体模式是一个用来划分命名空间并将一批属性和方法组织在一起的对象，如果它可以被实例化，那么只能实例化一次。
```

var Singleton = function(name){
    this.name = name;
    this.instance = null;
};
Singleton.prototype.getName = function(){
    return this.name;
}
// 获取实例对象
function getInstance(name) {
    if(!this.instance) {
        this.instance = new Singleton(name);
    }
    return this.instance;
}
// 测试单体模式的实例
var a = getInstance("aa");
var b = getInstance("bb");

console.log(a.getName());// aa
console.log(b.getName());// aa
```
单体模式更多的专注于功能性代码，如编写一个弹窗组件，不用每次都去实例化，这样可以节省性能。

4) 模块模式  
模块模式是为单体模式添加私有属性和方法，能够减少全局变量的使用。
```
var singleMode = (function(){
    // 创建私有变量
    var privateNum = 112;
    // 创建私有函数
    function privateFunc(){
        // 实现自己的业务逻辑代码
    }
    // 返回一个对象包含公有方法和属性
    return {
        publicMethod1: publicMethod1,
        publicMethod2: publicMethod1
    };
})();
```
模块对象使用一个返回对象的匿名函数，在这个函数内部先定义私有变量和属性，供内部函数使用，然后将一个对象字面量作为函数值返回，返回的对象字面量中只包含可以公开的属性和方法。这样的话，可以提供外部使用该方法；由于该返回对象中的公有方法是在匿名函数内部定义的，因此它可以访问内部的私有变量和函数。(类似于闭包)

5) 代理模式  
在代理对象中实例化本体对象，代理独享的属性和方法与本体对象一致，代理对象可以控制何时实例化本体对象，本体对象只需要负责处理传给他的对象，代理来控制传哪个对象，什么时候实例化。
```
var myImage = (function(){
    var imgNode = document.createElement("img");
    document.body.appendChild(imgNode);
    return function(src){
        imgNode.src = src; 
    }
})();
// 代理模式
var ProxyImage = (function(){
    var img = new Image();
    img.onload = function(){
        myImage(this.src);
    };
    return function(src) {
                myImage("http://img.lanrentuku.com/img/allimg/1212/5-121204193Q9-50.gif");
        img.src = src;
    }
})();
// 调用方式
ProxyImage("https://img.alicdn.com/tps/i4/TB1b_neLXXXXXcoXFXXc8PZ9XXX-130-200.png");
```

6) 职责链模式  
发送者发送一个请求给接收者，接收者在链中对这个请求进行处理或者传递给下一个接收对象，即接收者要么处理这个请求要么把它交给下一个接收者对象，所以接收者在链中知道的其他对象只有一个，就是下一个接收者对象，如果所有的接收者都不能处理这个请求，那么请求就会从链中离开。它消除了发送者和接收者之间的耦合性。
链中的节点可以灵活的拆分重组，但是可能大部分的节点都是不起作用的，所以要避免太长的职责链。

7) 命令模式
```
var command = function(receiverObj){
    this.receiver = receiverObj;
};
command.prototype = {
    exec:function(){
        this.receiver.doSomthing();//接收者的具体操作
    },
    undo:function(){
        this.reciver.backout();//撤销操作
    }
};

var invoker = function(cmdObj){
    this.command = cmdObj;
}
invoker.prototype = {
    handle:function(){//调用者的一个操作
        this.command.exec();
        //不需要知道操作的对象是谁，有接收者负责，仅执行操作即可，
        //这样可以随意更改command参数，只要它实现了exec方法；
    }
};
```
命令者模式降低了代码之间的耦合性，实现将一组命令定义好供接收者调用执行，提高了代码的模块化程度，但是降低了代码的可读性，从接收者到调用者。

8) 模板方法模式  
模板方法模式由二部分组成，第一部分是抽象父类，第二部分是具体实现的子类，一般的情况下是抽象父类封装了子类的算法框架，包括实现一些公共方法及封装子类中所有方法的执行顺序，子类可以继承这个父类，并且可以在子类中重写父类的方法，从而实现自己的业务逻辑。

9) 策略模式
定义一组方法，把它们逐个封装起来，并且使他们可以相互替换
```
var obj = {
        "A": function(salary) {
            return salary * 4;
        },
        "B" : function(salary) {
            return salary * 3;
        },
        "C" : function(salary) {
            return salary * 2;
        } 
};
var calculateBouns =function(level,salary) {
    return obj[level](salary);
};
console.log(calculateBouns('A',10000)); // 40000
```
10) 发布-订阅模式（观察者模式）  
发布订阅模式定义了一种一对多的关系，订阅者对象同时监听一个发布者对象，当一个对象发生改变时，所有依赖对象都能得到通知。
优点：支持简单的广播通信，发布者和订阅者耦合性降低，发布者不必关心订阅者如何使用消息。
缺点：创建订阅者需要消耗一定的时间和内存，过度使用会不利于代码的维护。
```

var event = {
    list: [],
    listen: function(key,fn) {
        if(!this.list[key]) {
            this.list[key] = [];
        }
        // 订阅的消息添加到缓存列表中
        this.list[key].push(fn);
    },
    trigger: function(){
        var key = Array.prototype.shift.call(arguments);
        var fns = this.list[key];
        // 如果没有订阅过该消息的话，则返回
        if(!fns || fns.length === 0) {
            return;
        }
        for(var i = 0,fn; fn = fns[i++];) {
            fn.apply(this,arguments);
        }
    }
};

//取消订阅
event.remove = function(key,fn){
    var fns = this.list[key];
    // 如果key对应的消息没有订阅过的话，则返回
    if(!fns) {
        return false;
    }
    // 如果没有传入具体的回调函数，表示需要取消key对应消息的所有订阅
    if(!fn) {
        fn && (fns.length = 0);
    }else {
        for(var i = fns.length - 1; i >= 0; i--) {
            var _fn = fns[i];
            if(_fn === fn) {
                fns.splice(i,1); // 删除订阅者的回调函数
            }
        }
    }
};

var initEvent = function(obj) {
    for(var i in event) {
        obj[i] = event[i];
    }
};
```

11) 中介者模式  
暂缓

23. js实现继承的方式  
实现继承，我们首先要有个父类
```
function Person(){
    this.name = name || 'kevin';//属性
    this.sayName = function(){
        alert('my name is' + this.name);
    } //实例方法
}

Person.prototype.sayAge = function(age){
    alert(this.name + 'is' + age);
} //原型方法
```
1) 原型链继承
将父类的实例作为子类的原型
```
function Man(){

}
Man.prototype = new Person();
Man.prototype.name = 'peter';
var man = new Man();
```
优点：  
实例是子类的实例，也是父类的实例；  
父类新增原型方法和属性，子类都能访问到；  

缺点：  
必须实例化之后才能为子类添加属性和方法，不能放在构造器中；  
无法实现多继承；  
来自原型对象的引用属性是所有实例共享的；  
创建子类实例时，无法向父类构造函数传参；

2) 构造函数继承  
复制父类的实例属性给子类
```
function Man(name){
    Person.call(this);
    this.name = name || 'peter';
}
var man = new Man();
```
优点：  
创建子类实例时，可以向父类传递参数；  
可以实现多继承（call多个父类对象）；

缺点：  
实例不是父类的实例，只是子类的实例；  
只能继承父类的属性和方法，不能继承原型的属性和方法；  
无法实现函数复用，每个子类都是父类实例函数的副本，影响性能；

3) 实力继承
给父类实例添加新特性，作为子类实例返回
```
function Man(name){
    var item = new Person();
    item.name = name;
    return item;
}

var man = new Man();
```
优点：  
不限制调用方式

缺点：  
实例是父类的实例，不是子类的实例；
不支持多继承；

4) 拷贝继承
```
function Man(name){
    var person = new Person();
    for(var i in person){
        Man.prototype[i] = person[i];
    }
    Man.prototype.name = name || 'peter';
}
var man = new Man();
```
优点：  
支持多继承

缺点：  
效率较低，内存占用高；  
无法获取父类不可枚举的方法（即无法通过for in访问到的方法）；  

5) 组合继承
调用父类构造，继承父类属性并保留了传参的优点，然后通过将父类实例作为子类原型实现函数复用。
```
function Man(name){
    Person.call(this);
    this.name = name;
}
Man.prototype = new Person();

var man = new Man();
```
优点：  
可以继承实例属性方法，也可以继承原型属性方法；  
既是子类的实例，也是父类的实例；  
不存在引用属性共享问题；  
可传参；  
可复用；  

缺点：  
调用两次构造函数，生成两份实例；  

6) 寄生组合继承
通过寄生方式，去掉父类的实例属性，不必初始化两次实例方法。
```
function Man(name){
    Person.call(this);
    this.name = name;
}

(function(){
    var Super = function(){};//创建一个没有实例方法的超类
    Super.prototype = new Person();
    Man.prototype = new Super();//将其实例作为子类的原型
})();

var man = new Man();
```
寄生组合继承实现较为复杂

24. js异步编程的实现  
js任务的执行模式分为同步和异步，同步就是程序的执行顺序和任务的排列顺序是一致的，前一个任务执行完成再执行后一个任务，可能会造成阻塞。异步就是每个任务都有一个或多个回调，前一个任务执行完之后执行其回调，后一个任务不必等到前一个程序执行完，所以程序的执行顺序和任务的排列顺序是不一致的。

1) 回调函数
```
function f1(callback){
    setTimeot(function({
        callback();
    },1000);
}

f1(f2);
```
将f2作为f1的回调函数来执行，程序不会发生阻塞。回调函数简单易于理解，但是不利于代码的阅读和维护（可能会出现回调函数层层嵌套的问题，即所谓的"回调地狱"），并且各个部分之间高度耦合，一个任务只能指定一个回调函数。

2) 事件监听  
采用事件驱动的模式，任务的执行不取决于程序是否执行完，而取决于某个事件是否发生。  
```
f1.on('done',f2);//监听到done事件发生之后，执行f2

function f1(){
    setTimeout(function(){
        f1.trigger('done');//f1执行完触发done事件
    },1000);
}
```
可以绑定多个事件，每个事件可以指定多个回调函数，结构上实现了解耦，但是流程上会变得不清晰。

3) 发布订阅模式
参照第22条第10小节。

4) Promise对象（重点理解Promise）  
Promise的实现标准有很多，我们这里理解的是ES6的Promise对象  

###### 简单的栗子
```
var p = new Promise(function (resolve, reject) {
    // ...
    if(/* 异步操作成功 */){
        resolve(ret);
    } else {
        reject(error);
    }
});

p.then(function (value) {
    // 完成态
}, function (error) {
    // 失败态
});
```
我们在通过Promise构造函数实例化一个对象时，会传递一个函数作为参数，这个函数会被立即执行。
```
let promise = new Promise(function(resolve,reject){
    console.log('执行1');
});
console.log('执行2');

//执行顺序为先输出"执行1",再输出"执行2"
```
Promise操作只会处理3种状态
![image](https://user-gold-cdn.xitu.io/2017/1/18/84cb777c7a080fc583ed145b288184f0)  
状态的改变只会从未完成态向完成态或者失败态转化，过程不可逆并且状态不能被更改，完成态和失败态间不能相互转化。传入的两个参数

`resolve`就对应着完成态之后的操作  
`reject`对应着失败态之后的操作

在一个Promise对象实例化之后，我们调用该对象实例的`then()`方法，其传递两个参数，第一个参数对应完成态的操作，第二个参数对应失败态的操作。

###### 一个引用的栗子
```
function loadImageAsync(url) {
    return new Promise(function (reslove, reject) {
        var img = new Image();
        img.onload = function () {
            reslove();
        }
        img.onerror = function () {
            reject();
        }
        console.log("loading image");
        img.src = url;
    });
}
var loadImage1 = loadImageAsync("http://image.beekka.com/blog/201212/bg2012122101.jpg");
loadImage1.then(function success() {
    console.log("success");
}, function fail() {
    console.log("fail");
});
var loadImage2 = loadImageAsync("1.png");
loadImage2.then(function success() {
    console.log("success");
}, function fail() {
    console.log("fail");
});
```

`resolve`对象的参数也有可能是另一个Promise实例，等作为参数的那个Promise实例状态更改之后，才会执行外层Promise。  

此外，`then()`方法会返回一个新的Promise实例，这样就可以使用链式写法，链式中的then方法后一个resolve的参数是前一个then方法中resolve的返回值。

###### 再举一个栗子
```
var p1 = new Promise( (resolve, reject) => {
    setTimeout(() => resolve('p1'), 10);
});
p1.then( ret => {
    console.log(ret);
    return 'then1';
}).then( ret => {
    console.log(ret);
    return 'then2';
}).then( ret => {
    console.log(ret);
});
```

Promise对象的Error对象具有冒泡性质，会一直向后传递，只要被捕获为止。也就是说，错误总是会被下一个catch语句捕获，catch语句用于指定发生错误时的回调。
###### catch的栗子
```
var p = new Promise( (resolve, reject) => {
    setTimeout(() => resolve('p1'), 10);
});
p.then( ret => {
    console.log(ret);
    throw new Error('then1');
    return 'then1';
}).then( ret => {
    console.log(ret);
    throw new Error('then2');
    return 'then2';
}).catch( err => {
    // 可以捕抓到前面的出现的错误。
    console.log(err.toString());
});

//输出then1
```
> 跟传统的try/catch不同的是，如果没有使用catch方法指定错误处理回调函数，则Promise对象抛出的错误不会传递到外层代码（在chrome会报错）  

##### catch之后还可以接着使用then.

#### Promise对象方法

##### Promise.all()
Promise.all()方法用于将多个Promise实例，包装成一个新的Promise实例，例如

```
var p = Promise.all([p1, p2, p3]);
```
新的Promise实例p的状态由`p1, p2, p3`决定：

当`p1, p2, p3`的状态都为完成态时，p为完成态。  
`p1, p2, p3`中任一一个状态为失败态，则p为失败态。

##### Promise.race()
Promise.race方法同样是将多个Promise实例，包装成一个新的Promise实例。
```
var p = Promise.all([p1, p2, p3]);
```
不同的是，只要`p1, p2, p3`中任意一个实例率先改变状态，则p的状态就跟着改变，而且状态由率先改变的实例决定。

##### Promise.resolve()
Promise.resolve()可以将现有的对象转为Promise对象。
```
var p = Promise.resolve('p');
// 相当于
var p = new Promise(resolve => resolve('p'));
```
Promise.resolve()会根据参数类型进行相应的处理,参数为Promise实例时直接返回；参数具有then方法时将该对象转成Promise对象并且立即执行then方法；参数是一个原始值的时候，Promise返回一个状态为resolve的新Promise实例，并将改参数传递给resolve方法；不带参数时直接返回一个resolve状态的Promise对象。

#####  Promise.reject()
处理方式跟resolve类似，状态都为reject

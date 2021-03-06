由于近期项目终于进入到了不那么忙的时候，终于有空闲时间可以继续撸自己的东西了。前段时间因为项目很赶，所以始终处在一个每天赶进度的状态中，也没时间好好整理一下项目中踩到的各种坑。今天在回来的地铁上，突然想起来今年面试的时候被问到的一个很有趣的问题：javascript是不是一个面向对象的语言？ 

在没有入前端坑之前，我跟大多数人的印象一样，认为js只是一个用来操纵dom的网页端脚本语言，那时候的我还停留在所有代码嵌入在jsp中的时代（以前做过一段时间java web开发）。后来，前端技术瞬息万变，前后端分离的概念日益主流，javascript能做的事情也变得越来越多，这时候我们才会思考，js到底是不是面向对象呢。答案显而易见——是。  

众所周知，面向对象有三个特征：
- 封装
- 继承
- 多态  

像java、c#等oop语言，是通过类的形式来组织函数和变量，使其形成对象的概念。但是面向对象仅仅是一个编程思想或一种软件开发方法。任何一门语言可能实现面向对象的方法都不是一致的。js在实现面向对象的方面不同于java语言（当然，在ES6标准中已经有class的概念了。），它是通过`原型(prorotype)`来实现面向对象的。

我们类比一下java的类继承，类继承是在函数对象内调用父类的构造函数，从而获得父类的属性和方法。但是原型继承，继承不在对象本身，而是在对象的`原型链`上，子类的构造函数中没有父类的属性和方法。

举个栗子
```
\\创建一个对象
var people = {
    name: 'kevin',
    age: '24',
    work: function(){
        //do somthing
    }
}
```
以上我们就创建了一个对象，它有自己的属性和方法。如果我们要创建对象，可以采用构造函数模式。
```
function Person(name, age){
    this.name = name;
    this.age = age;
    this.work = function(){
        //do something
    }
}
var kevin = new Person("kevin", 24);
console.log(kevin.__proto__.constructor)
//
```
上面的构造函数可以类比成是一个普通类，它可以直接产生实例化对象。而对象`kevin`的__proto__属性的构造器直接指向`Person`的原型。
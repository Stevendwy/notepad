##ES6

##ES6 基础特性
**基础语法**

>let, const, class, extends, super, arrow functions, template string, destructuring, default, rest anguments
>
>这些是最常用的语法

*let , const*

> 和var类似，用来声明变量
>

    var name = 'zach' while (true){
        var name = "obama"
        console.log(name)//obama
        break
    }
    console.log(name)//obama
    
>两次都是输出obama ，因为ES5 只有全局和函数作用域，没有块级作用
>域，而let 实际上为js新增块级作用域，用它声明的变量，只在let 命令
>所在的代码块内有效

    let name = "zach" while (true){
        let name = 'obama'
        console.log(name)//obama
        break
    }
    console.log(name)//zach
    
>var 带来不合理的计数循环变量泄露为全局变量

    var a = [];
    for (var i = 0;i<10;i++){
        a[i] = function(){
            console.log(i)
        }
    }
    a[6]();//10
    
>每次的循环都是将原有值覆盖，导致最后输出为最后的值，而使用let 不会

    var a = [];for (let i = 0; i < 10; i++) {
      a[i] = function () {    console.log(i);
      };
    }
    a[6](); // 6
    
>const 也用来声明变量，当时声明的变量，一旦声明就不能修改

    const PI = Math.PI
    PI = 23//Module build failed:SystaxError:/es6/app.js:"PI" is read-only
    
>我们尝试用const 改变常量时候，会报错，可以来声明第三方库时候的变量，避免重命名的 bug


*class , extends , super*

    class Animal {
    constructor(){ 
           this.type = 'animal'
        }
    says(say){ 
           console.log(this.type + ' says ' + say)
        }
    }
    let animal = new Animal()
    animal.says('hello') //animal says helloclass Cat extends Animal {constructor(){
            super()        this.type = 'cat'
        }
    }
    let cat = new Cat()
    cat.says('hello') //cat says hello
    
>上面代码用class 定义了一个类，可以看到里面有一个constructor 方法，这是构造方法，而this关键字代表实例对象，constructor内定义的方法和属性是实例对象自己的，而constructor 外定义的方法和属性则是所有实例对象可以共享的
>
>class 之间可以通过extends 关键字实现继承，上面定义了一个cat 类，该类通过extends 关键字，继承了Animal类的所有属性和方法。
>
>super关键字，指代父类的实例，子类必须在constructor 方法中调用super方法，否则新建实例会报错。
>
>ES6 继承机制，实质是先创造父类的实例对象 this ，然后用子类的构造函数修改this。


*arrow function*

>用它来写function 比原来的写法要简洁清晰

    function (i){
        return i+1;
    }

>如果方程比较复杂，需要用{}把代码包起来

    function(x,y){
        x++;
        y--;
        return x+y;
    }
    (x,y)=>{x++;y--;return x+y}
    
>解决this指向

    class Animal{
        constructor(){
            this.type = 'animal'
        }
        says(say){
            setTimeout (()=>{
                console.log(this.type+'says'+say)
            },1000)
        }
    }
    var animal = new Animal()
    animal.says('hi')//animal says hi
    
>当我们使用箭头函数时，函数体内this对象，就是定义时所在的对象，并不是因为箭头函数内部有绑定this 的体制，实际原因是箭头函数根本没有自己的this，它的this是继承外面的，因此内部this就是外层代码块的this

*template string*

>传统插入大段 html内容到文档时，传统方法麻烦，用ES6 新特性模板字符串后 直接写

    $("#result").append(`
      There are <b>${basket.count}</b> items
       in your basket, <em>${basket.onSale}</em>
      are on sale!
    `);
    
>用反引号（\）来标识起始，用${}来引用变量    

*destructuring*

>ES6允许按照一定模式，从数组和对象中提取值，对变量赋值，这被称为 解构(Destructuring)

    let cat = 'ken'let dog = 'lili'
    let zoo = {cat: cat, dog: dog}            console.log(zoo)  //Object 
    {cat: "ken", dog: "lili"}
    ES6 可以写为：
    let cat = 'ken'
    let dog = 'lili'
    let zoo = {cat, dog}
    console.log(zoo)  //Object
     {cat: "ken", dog: "lili"}
    反过来写
    let dog = {type: 'animal', many: 2}
    let { type, many} = dog
    console.log(type, many)   //animal 2
    
*default , rest*

>default 理解为默认值，例子：调用animal()方法时候忘记传参数，传统做法是加上这一句type = type || ‘cat’ 来指定默认值。

    function animal(type){   
     type = type || 'cat'  
    console.log(type)
    }
    animal()
    
>用ES6 可以直接写
    
    function animal(type = 'cat'){
    console.log(type)
    }
    animal()    

>rest 语法

    function animals(...types){    console.log(types)
    }
    animals('cat', 'dog', 'fish') //["cat", "dog", "fish"]
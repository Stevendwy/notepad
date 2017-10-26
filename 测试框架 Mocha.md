##测试框架 Mocha
参看：http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html

1、测试脚本的写法
    Mocha 作用是运行测试脚本，测试脚本就是用来测试代码的脚本。
    下面是一个加法模块 add.js 的代码。
        
        //add.js
        function add(x,y){
        return x+y;
    }
    module.exports = add;
要测试这个加法模块是否正确，就要写测试脚本。

通常 测试脚本和所要测试的源码脚本同名， 后缀名 .test.js (表示测试) 或者 .spec.js （表示规格） 比如：add.js 测试脚本名称就是 add.test.js.

   
// add.test.js
var add = require('./add.js');
var expect = require('chai').expect;

describe('加法函数的测试', function() {
  it('1 加 1 应该等于 2', function() {
    expect(add(1, 1)).to.be.equal(2);
  });
});

上面的代码 就是测试脚本，可以单独执行。测试脚本应该包含一个或者多个describe 块，每个describe 块应该包含一个或者多个it块。

describe 块称为’测试套件’（test suite），表示一组相关的测试。它是一个函数，第一个参数是测试套件的名称（’加法函数的测试’），第二个参数是一个实际执行的函数。

it块称为‘测试用例’（test case）表示一个单独的测试，是测试的最小单元。他也是一个函数，第一个参数是名称 第二个参数是实际执行的函数。

2、断言库的用法
    上面测试脚本中有一句断言
    expect(add(1,1).to.be.equal(2))

    ‘断言’ 就是判断执行结果是否与预期一致，如果不一致就抛出错误。上面断言的意思： 调用 add（1，1） 结果应该等于2

    所有的测试用例 都应该含有一句或者多句断言，是测试用例的关键。 Mocha 本身不带断言库，先引入
    var expect = require(‘chai’).expect;

    断言库有很多种，上面引入的是 chai

    下面是一些例子
    
// 相等或不相等
expect(4 + 5).to.be.equal(9);
expect(4 + 5).to.be.not.equal(10);
expect(foo).to.be.deep.equal({ bar: 'baz' });

// 布尔值为true
expect('everthing').to.be.ok;
expect(false).to.not.be.ok;

// typeof
expect('test').to.be.a('string');
expect({ foo: 'bar' }).to.be.an('object');
expect(foo).to.be.an.instanceof(Foo);

// include
expect([1,2,3]).to.include(2);
expect('foobar').to.contain('foo');
expect({ foo: 'bar', hello: 'universe' }).to.include.keys('foo');

// empty
expect([]).to.be.empty;
expect('').to.be.empty;
expect({}).to.be.empty;

// match
expect('foobar').to.match(/^foo/);

基本上 expect 断言的写法都一样，头部是 expect 方法，尾部是断言方法， 比如 equal、a\an 等 两者用 to 或 to.be 连接
如果断言不成立就抛出一个错误。

3、Mocha 基本用法
    有了测试脚本后 用Mocha 运行它，执行
    $mocha add.test.js
    
    加法函数的测试
           √1加1 应该等于2
    1 passing （8ms）
    
    上面的运行结果表示、测试脚本通过 了测试
    mocha 命令后面紧跟测试脚本的路径和文件名 可以指定多个测试脚本
    
    $mocha file1 file2 file3

    mocha 默认运行test 子目录里面的测试脚本  
    添加 —recursive 参数 这时候 test 目录下测试用例不管多深都会执行
    $ mocha —recursive

4、通配符
    $mocha 
    
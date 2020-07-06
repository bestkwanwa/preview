# 第十三章 ECMAScript 6 基础
## ECMAScript 6 简介
- JavaScript 三大组成部分
    - ECMAScript 
    - DOM
    - BOM 
- ECMAScript 发展历史 https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Language_Resources
- ECMAScript 包含内容：JS 中的数据类型及相关操作，流程控制，运算符及相关运算……
## ECMAScript 6 
- let 和 const
    - let 和 var 的差异
        - let 允许声明一个在作用域限制在块级中的变量、语句或者表达式
          
            - 块级作用域
            
              ```javascript
              let lis=document.querySelectorAll('li');
              for(let i=0;i<lis.length;i++){
                lis[i].onclick=function(){
                  console.log(i);
                }
              }
              //因为每个i都是独立的作用域，所以不存在事件绑定不上每个li，如果用var声明i，则只给最后一个li绑定事件
              //等价于下面代码
              {
                let i=0;
              	lis[i].onclick=function(){
                  console.log(i);
                }
              }
              {
                let i=1;
              	lis[i].onclick=function(){
                  console.log(i);
                }
              }
              {
                let i=2;
              	lis[i].onclick=function(){
                  console.log(i);
                }
              }
              ```
            
        - var 声明的变量只能是全局或者整个函数块的
        - let 不能重复声明
        - let 不会被预解析
        - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/let
    - const 常量
        - 常量不能重新赋值
        - 不能重复声明，声明时必须赋值
        - 块级作用域
        - const 不会被预解析
        - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const
    
- 解构赋值
    - 对象的解构赋值
    
    - 数组的解构赋值--顺序会保持一致
    
      ```javascript
      //快速交换两个值
      [a,b]=[b.a]
      ```
    
      
    
    - 字符串的解构赋值
    
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment
    
- 展开运算符
    - 对象展开
    
    - 数组展开
    
      ```javascript
      //obj展开后放入一个新对象中
      let obj2={...obj};
      ```
    
      
    
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_syntax
    
- 剩余参数

    ```javascript
    //解构赋值+展开运算符
    //剩余参数放到一个数组或对象中
    let arr = [1,2,3,4,5];
    let [a,...b] = arr;
    console.log(a,b);
    ```

    

- Set 对象---去重    
  
    - Set 对象的数据结构
    - Set 相关属性与方法
        - size 属性 ---length
        - clear()---清空所有值、delete()---传入具体值，删除成功返回true、has()、add()---返回set本身，可以链式操作    
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set
    
- Map 对象---保存键值对
    - Map 对象的数据结构
    - Map 相关属性与方法
    - size 属性
    - clear()---清空所有值、delete()---传入具体值，删除成功返回true、get()---获取某项key对应的值、has()、set(key,value)---返回set本身
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map
    
- 函数新增扩展
    - 箭头函数
        - 箭头函数的各种写法
        - 箭头函数的 this 问题---this指向箭头函数定义时所在的作用域的this
        - 箭头函数的不定参问题---箭头函数没有不定参，用展开运算符可以拿到所有参数
        - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions
        
    - rest 参数设置
    
    - 参数默认值设置
    
        ```javascript
        // ES6前默认值设置
        a = typeof a === 'undefined' ? 10 : a ;
        ```
    
        ```javascript
        // ES6默认参数设置
        let fn = (nub=0,nub2=0)=>{
            console.log(nub+nub2);
        }
        fn();
        ```
    
        
    
- 新增数组扩展---见 数组方法.md
    - Array.from()---把一个类数组转变成数组，返回转换后的新数组、Array.of() ---将参数转成一个数组
    - isArray()
    - find()、findIndex()、includes()
    - flat()、flatMap()
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array
    
- 新增字符串扩展
    - includes(), startsWith(), endsWith()
    - repeat()
    - 模版字符串   
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String
    
- 新增对象扩展
    - 属性简洁表示法
    - 属性名表达式
    - 手册地址：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object
    
- babel 使用
    - Babel 是一个 JavaScript 编译器

    - 手册地址：https://www.babeljs.cn/

    - Babel 基本使用方法

      浏览器环境下：

      - 引入

      - <script type:"text/babel">



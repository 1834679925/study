### 4.3 函数的参数

在JavaScript中函数的关键词后面跟随的小括号,是参数列表,调用时,表达式的括号中传入实际参数,函数的参数在function内可以用arguments对象来获取

形参和实参是一 一对应的,都可以用arguments获取到实参的内容

        function aaa(x,y,z){
            console.log(arguments[1]);
        }
        aaa('a','b','c');

### 4.4 this

this是JavaScript语言的一个关键字,他代表函数运行时,自动生成的一个内部对象,只能在函数内部使用,随着函数适用场合的不同,this的值回发生变化,但有一个原则,就是this指的是,调用函数的那个对象
绑定事件,this代表制定调用函数的对象

### 4.5 函数的返回值

返回值是一个函数的处理结果,如果我们需要在程序中拿到函数的处理结果,做进一步处理,则需要函数必须由返回值,函数的返回值用return定义

            function b(){
				return 1;
			}
			console.log(b());

注意:
return是一个函数结束的标志,只要执行一次,整个函数就会结束运行
使用return之后,跟在return后面的值就是整个函数的返回值
如果函数没有使用return语句,那么函数的默认返回值是undefined

### 4.6 全局变量和局部变量

作用域是数据可以在哪个范围使用,在ES5中,只有全局作用域和函数作用域,在ES6中出现了块级作用域

4.6.1 全局作用域

在任何地方都能访问,函数外定义的变量拥有全局作用域,不使用var定义的变量拥有全局作用域,也是所有window对象上的属性

4.6.2 函数作用域

声明在函数内部,和全局作用域相反,局部作用域,一般只会在固定的代码片段内访问,如函数作用域,所以在一些地方有人把这种作用域称为函数作用域

4.6.3 全局变量

在函数外声明的变量叫全局变量,在函数内外都可以访问到

4.6.4 局部变量

在函数内部创建,在函数外访问不到,在函数内部如果局部变量和全局变量名称相同时,优先使用局部变量,当在函数内部找不到需要的变量时,则去全局寻找,但如果有参数名称符合要求时,则会选择参数作为需要的变量

4.6.5 作用域链

作用域链决定了那些数据能被访问,当一个函数创建后,它的作用域链会被创建在次函数的作用域中,从而访问数据
可以把它理解成一个链接房间的链条,当局部变量缺失时,就会顺着这个链条到全局,去寻找想要的变量

#第五章 JavaScript语句

### 5.1 分支语句

5.1.1 if语句

           var a=10;
			//小括号里一定要是true
			if(a<20){
				alert('yes');
			}


5.1.2 if...else语句

         if(a<10){
				alert('yes');
			}else{
				alert('no');
			}

5.1.3 if...else if语句

      if(a<60){
				alert('D');
			}else if(a>=60&&a<75){
				alert('C');
			}else if(a>=75&&a<85){
			     alert('B');
			}else if(a>=85&&a<=100){
			      alert('A');
			}else{
				alert('缺考')
			}

5.1.4 switch语句

switch小括号中一般情况是一个变量名,这个变量可能会有不同的取值,所有的case都是"或"的关系,case后面的值会与变量值做比对,满足后就执行case后面的代码,不写break就会将所有的比对进行一遍

           var a=10;
			//将判断的内容写在括号里
			switch (a){
				case 值1:
				//执行代码
			    break;
			    case 值3:
				//执行代码
			    break;
			    case 值3:
				//执行代码
			    break;
			    case 值n:
				//执行代码
			    break;
			    default
				//执行代码
			  
			}

### 5.2 循环语句

5.2.1 while循环

while语句是一种前测试语句(先判断以下在执行),循环的目的是为了反复执行语句或代码块,只要表达式为true就继续循环,一旦为假的时候,循环退出

        var a=10;
        while(a<15){
            //10
            //11
            //12
            //13
            //14
            alert('你好');
            a++;
            //11
            //12
            //13
            //14
            //15
        }

5.2.2 do...while循环

do...while语句是一种后测试语句,就是在循环体中的代码执行之后,才开始判断条件,也就是说,在表达式判断之前,循环体内的代码至少会被执行一次

        var a=0;
        do{
            alert('你好');
            a++;

        }while(a<5);

5.2.3 for循环

for语句是一种前测试语句,一般情况下,有三个基础表达式语句,每一个要用分号隔开

    //初始化     判断     更新
     for(var x=0;x<y;x++){
        //执行循环体
          alert(x);
	 }
	 //顺序为:初始化-->判断-->执行循环体-->更新




## 练习

需求:
1 做一个1+2+3+4+5+6+7+8+9+10的和
2 计算1~100的累加和,显示在页面上


###9.21
作业
1 只做一个模拟的银行取款机
2 设置一个银行卡号,密码和一个余额
3 用户输入卡号和密码后输入要取得金额
4 前提不能大于卡内余额
5 取完后显示取后余额
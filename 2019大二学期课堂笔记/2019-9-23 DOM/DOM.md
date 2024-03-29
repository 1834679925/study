#第六章 DOM

### 6.1 DOM概述

6.1.1 DOM的概念

DOM文档对象模型,DOM对象不仅仅是一个普通的内置对象,它还是一个巨大的API的核心对象,它将文档内容呈现在js面前,并赋予了js操作文档的能力

6.1.2 DOM和JavaScript的关系

一个web页面是一个文档,则文档可以在浏览器窗口或者作为html源代码显示出来,但上述两种情况都是同一个文档,DOM提供了对同一份文档的另一种表现,储存和操作的方式,DOM能够使用JavaScript脚本语言进行修改

6.1.3 DOM节点

加载html页面是,web浏览器生成一个树形结构,用来表示页面的内部结构,DOM将这种结构理解为节点组成,根据w3c的html DOM标准,html文档找那个的所有内容都是节点
>整个文档是一个文档节点
>每个html元素是元素节点
>html元素内的文本是文本节点
>每个html属性都是属性节点
>注释也是节点,叫注释节点

6.1.4 DOM树

DOM树体现着html页面的层级结构,而DOM树有DOM文档树和DOM元素树两种,DOM元素树包含的只有元素节点,而DOM文档树则包括DOM文档中的所有内容

### 6.2 获取元素

6.2.1 用id获取元素

getElementById()的方法,接受一个参数:获取元素的id,如果找到相应元素,则返回该元素的,否则返回null

        //用变量接 在文档中  找  元素  用id  'd'
         var d=document.getElementById('d');

6.2.2 用标签名获取元素

getElementsByTagName()可以获取该元素名称下所有的元素,返回一个伪数组,或者说是一个节点列表

    var lis=document.getElementsByTagName('li');
        //伪数组
        console.log(lis);

在某一个元素中,并不是在全局文档中利用标签获取元素,这样更加精准

    var ul=document.getElementByTagName('ul');
        var list=document.getElementsByTagName('li');
        console.log(list);

当元素只有一个的时候,返回的也依然是一个列表,而不是一个元素.可以通过数组的下标找到该元素.

        var div = document.getElementsByTagName('div');
        console.log(div[0]);

6.2.3 用类名获取元素

    var a =document.getElementsByClassName('a');
        console.log(a);

6.2.4 用选择器获取元素
querySelector()和querySelectorAll()可以依靠选择器找到元素,但是前者只能找到元素列表的第一个元素,而后者可以全部找到,注意,该方法性能没有直接利用标签寻找到.

        var ul = document.getElementById('ul')
        var x = document.querySelector('#div>div a');
        var lis = ul.querySelectorAll('li');
        console.log(lis);


### 6.3 获取元素中的其他信息

6.3.1 获取元素名

当我们使用id获取元素的时候,元素名称会和整个元素一起显示出来,如果想要拿到该元素的元素名,也就是标签名则需要用tagName属性,该属性只能获取,不能设置

     var div=document.getElementById('mydiv');
        conaole.log(div.tagName);//DIV


6.3.2 获取元素节点里的内容

当获取了元素之后,如果我们需要拿到元素中的内容,则需要用另一种方法得到,元素里的内容(所有)可能包括:文本或元素,需要用innerHTML属性

     var div=document.getElementById('mydiv');
        console.log(div.innerHTML);

innerHTML属性除了可以获取标签内的内容外,还可以设置标签内的内容

    var div=document.getElementById('mydiv');
      div.innerHTML='你好';

6.3.3 获取元素节点中的文本

利用innerText属性获取的只能是文本节点,不能是其他,当然innerText属性除了获取,也可以设置元素中的文本

        var div=document.getElementById('mydiv');
         console.log(div.innerText);

         div.innerText='hello';

6.3.4 获取元素的类名

利用className属性来获取元素的类名,以字符串的形式返回,可以设置新的class类名,需要注意的是,返回值是一个字符串,如果更换其中一个类,则需要考虑该字符串中其他类是否应该一起设置

    var div=document.getElementById('mydiv');
        console.log(div.className);

6.3.5 获取元素样式

style属性可以获取元素内联样式的所有属性,当然如果继续在style中找属性名如:backgroundColor,就可以得到该属性的值,以字符串的形式返回,同时也可以设置该属性,从而达到增加或更改样式,需要注意的是,以js形式增加的样式的优先级大于css优先级





##练习
需求1:
1 随便用一个标签,给它一个id属性
2 获取这个元素的标签名
3 如果这个元素是加粗的,就把它变成不加粗显示

    <body>
    <h2 id="mytag">这是一个h2标签</h2>
    <script>
        var mytag=document.getElementById('mytag');
        console.log(mytag.tagname);
        //方法一:
        //那些标签是加粗的h1~h6 b strong
        //H1||H2||H3||H4||H5||H6||B||STRONG
        if(mytag.tagName=='H1'||mytag.tagName=='H2'||mytag.tagName=='H3'||mytag.tagName=='H4'||mytag.tagName=='H5'||mytag.tagName=='H6'||mytag.tagName=='B'||mytag.tagName=='strong'){
            mytag.style.fontWeight=200;
        }

        //方法二:
        //不管是不是粗体,统一变为粗体
        mytag.style.fontWeigth=200;

        //方法三:

        var arr= ['H1','H2','H3','H4','H5','H6','B','STRONG'];
        //console.log(arr.indexOf('DIV'));
        //检测数组里是否有粗体的标签名,返回-1以外的都是粗体
        var isTrue=arr.indexOf(mytag.tagName);
        console.log(isTrue);
        //判断如是粗体标签名  就改变样式
        if(isTrue!=-1){
            mytag.style.fontWeight=200;
            mytag.style.color='red';
        }

        mytag.tagName='DIV';
        alert('d');
    </script>
    </body>


需求2:
1 在一个列表标签中,插入三个无序内容块
2 内容分别为:苹果 西瓜 草莓

    <body>
    <ul id="ul">
        
    </ul>
    <script>
        var ul=document.getElementById('ul');
        ul.innerHTML='<li>苹果</li><li>西瓜</li><li>草莓</li>';
    </script>
    </body>


需求2:
1 一个200*200的红色方框,一个按钮
2 点击按钮,让红色方框变成蓝色
3 必须用className的赋值方法变化

    <style>
        .a{
            width: 200px;
            height: 200px;
        }
        .b{
            background-color: red;
        }
        .c{
            background-color: blue;
        }
    </style>
    </head>
    <body>
    <div id='mydiv' class="a b"></div>
    <button id="btn">点击变颜色</button>
    <script>
        btn.onclick=function(){
            var  div=document.getElementById('mydiv');
            div.className='a c'
        }
    </script>
    </body>


# DOM作业

##9.23
需求:
1.
在html上创建6个div元素
2.利用js赋予"所有"div样式,样式内容为:50*50,背景红色,间距20px,并横向排列
3.请不要添加任何id或class类
4.给第三个div用js增加一个"blue"类,在css中定义blue类的背景颜色为蓝色
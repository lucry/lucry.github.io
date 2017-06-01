---
layout:     post
title:      javascript对象篇
author:     葱葱
tags: 		javascript 笔记
subtitle:   To learn how to use a jekyll blog model and push it on the github.
category:  project1

---
## 面向过程与面向对象
* 面向过程是将能完成特定任务的程序段独立起来做成函数，整个系统通过函数相互调用处理数据，系统以数据流为中心。
* 面向对象的语言至少提供以下功能：封装、聚合、继承、多态。对象应具备属性和方法。
##javascript的对象
>* 当要废除一个对象时，可将其指向null
>* javascript是动态语言，对象类型在运行时才能确定，不存在早期绑定。
>* **javascript对象模型**：语言核心、基本内置语句（String、Date、Math等）、浏览器对象（window、Navigator、Location等）、文档对象（Document、Form、Image等）
>* **浏览器对象模型**(window)：document、frames、history、location、navigator
##事件驱动与事件处理
>* 常用输入事件：
1、onload、onunload（卸载某网页）、
2、onMousemove、onMouseOut、onMouseOver、onMousedown、onMouseup、
3、onClick、oncontextmenu（鼠标右键单击事件）、ondblclick、
4、onkeydown、onkeyup、onkeypress、
5、onfocus、onBlur（对象失去焦点）、onchange、onselect、
6、onsubmit（提交表单）、onreset（重置）
>* 事件后可调用代码
>```python
<input type="submit" name="Submit" value="查看密码和姓名" onclick="javascript:alert('姓名：'+form1.textfield.value+'\n 密码：'+form1.password.value);"/>
>```

>* 设置对象事件的方法
>```python
      function HandleAllLinks(){
        for (var i = 0; i < document.links.length; i++) {
          document.links[i].onclick = HandleAllLink;
        }
      }
      function HandleAllLink(){
        alert("即将离开此页！");
      }
>```
>* 显式调用事件处理程序
>```python
    <script type="text/javascript">
      function clickHandler(){
        alert("即将提交表单！");
        return turn;
      }
      myform.mybutton.onclick();
    </script>
  </head>
  <body>
    <form name="myform" action="" method="post">
      <input type="submit" name="mybutton" value="提交" onclick="return clickHandler()">
    </form>
  </body>
>```
>* 事件处理程序的返回值为false时会阻止浏览器进行下一步操作。
>* **其它常用事件**
   弹出警告框：alert()
   弹出询问框：confirm()
   弹出对话框：prompt()
   打开新窗口：open("url","name","replace")
   关闭窗口：close();
   改变大小：resizeBy(x,y);resizeTo(x,y)
   自动滚动文档：window.scrollBy(左右,上下);
   设置定时器（周期性执行代码）：setInterval("函数",时间);
   停止周期性执行代码：clearInterval(timer);
   延迟代码执行：window.setTimeout("code",time);
   取消延迟执行：clearTimeout(延时器);
 >* open 方法可打开非HTML文件，只需在第一个参数加上文件类型即可。
## 屏幕对象
> *      屏幕实际高度：screen.availHeight
        屏幕实际宽度：screen.availWidth
        屏幕色盘深度：screen.colorDepth
        屏幕区域高度：screen.height
        屏幕区域宽度：screen.width
        屏幕分辨率：screen.width*screen.height
        网页可见区域宽：document.body.clientWidth
        网页可见区域高：document.body.clientHeight
        网页可见区域宽（包括边线和滚动条）：document.body.offsetWidth
        网页可见区域高（包括边线的宽）：document.body.offsetHeight
        网页正文全文宽：document.body.scrollWidth
        网页正文全文高：document.body.scrollHeight
        网页被卷去的高：document.body.scrollTop
        网页被卷去的左：document.body.scrollLeft
        网页正文部分上：window.screenTop
        网页正文部分左：window.screenLeft
## 浏览器对象（navigator）
>* 浏览器代码：navigator.appCodeName
   浏览器名称：navigator.appName
   浏览器版本：navigator.appVersion
   浏览器语言：navigator.language
   浏览器编译平台：navigator.platform
   浏览器用户表头：navigator.userAgent1
>* MimeType对象以数组形式保存浏览器所支持MIME类型信息，Plugin主要管理当前浏览器已安装的插件或外挂程序信息。
>```python
     //例：列表输出MIME信息
      var count = navigator.mimeTypes.length;
      with(document){
        write("当前浏览器支持"+count+"种MIME类型：");
        write("<TABLE BORDER>")
        write("<CAPTION>MIME type 清单</CAPTION>")
        write("<tr><th><th>名称<th>描述<th>扩展名<th>附注")
        for (var i = 0; i < count; i++) {
          write("<tr><td>"+i+"<td>"+
          navigator.mimeTypes[i].type+
          "<td>"+navigator.mimeTypes[i].description+"<td>"+
          navigator.mimeTypes[i].suffixes+"<td>"+
          navigator.mimeTypes[i].enabledPlugin.name);
        }
      }
>```
>* navigator.javaEnabled() 可检查浏览器是否已启用Java支持功能。
## 文档对象
>* 设置链接：document.location="";
   查看文档最后修改时间：document.lastModfied;
   设置标签value值：document.表单名(form[i]).element[j].value
   按照标签ID引用标签：document.getElementByID();
   设置已访问过的超链接的颜色：document.vlinkColor=""
   设置访问中的超链接的颜色：document.alinkColor=""
   设置背景颜色：document.bgColor=""
   设置字体颜色：document.body.text=""
   显示标题：document.title
   显示URL：document.URL
   设置滚动：setInterval("函数",speed)
   防止盗链：referrer 属性
   锚链接对象：anchors属性（保存锚链接的数组，具有length属性）
 >```python
    //防止盗链
    var frontURL = document.referrer;
    var host = location.hostname;
    if(frontURL != ""){
        var frontHost = frontURL.substring(7,host.length+7);
        if(host == frontHost){
            alert("没有盗链！");
        }
        else{
            alert("您是非法链接，请通过本部访问");
        }
    }
    else{
         alert("您是直接打开该文档的，没有盗链！")   
        }    
 >```
>* **document.write**和**document.writeln**的区别：
在js标签之间，必须用document.writeln()在网页中写HTML。
>* **all和children**
document.all[]是文档中所有标签组成的一个数组变量，可通过document.all[i]、document.all[name]、document.all.tags[tagName]三种方式引用文档中的HTML元素。children可获得某一元素的子元素数组。
## 图像对象
>* 可通过new Image()的方法新建一个图像对象。
>* **属性** 
src：设置图像链接
>```python
//当鼠标在图片上时，改变图片
<img src="background.jpg" name="image" alt="" onmouseover="javascript:document.image.src='blue.jpg'"/>
>```
    alt：设置加载图片时显示的信息
    border：设置图像的边框信息
    complete：设置图像是否载入的信息
    height：设置图像高度
    width：设置图像宽度
    hspace：设置图像与左右边文字的间距（以像素为单位）
    vspace：设置图像与上面边文字的间距（以像素为单位）
    lowsrc：设置图片指向低分辨率版本的链接
    name：设置图像名称信息
>* onerror事件：当图片无法显示时将图片src设为已存在特定有效图片。
## 历史对象和地址对象
>* 移至前一页：history.back()
   移至后一页：history.forward()
   设置相对数字，移动页面：history.go(number,URL)
   装入URL中包含字符串的最近一个文档：history.go("characters")
>* 实现页面跳转可以通过history.go()也可通过window.location.href()，此方法可以实现通过点击按钮等方法跳转页面
>* 取得整个URL字符串：location.href
   地址的协议：location.protocol
   地址的主机名：location.hostname
   地址的主机和端口号：location.host
   取得路径名：location.pathname
   取得整个地址：url
>* **assign、replace、reload**
    * assign方法跳转至新页面可通过返回上一步返回原页面；
    * replace方法使用新的URL替换原URL，即不可通过返回上一步返回原页面；
    * reload方法有一个bool参数，当参数为true时才会跳转页面，该参数默认为false，此时有刷新页面的作用。
>* 刷新页面的方法：
    * location.reload()
    * location=location
    * location.navigate(location)
    * location.replace(location)
    * history.go(0)
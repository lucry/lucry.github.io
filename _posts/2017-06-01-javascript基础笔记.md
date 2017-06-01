---
layout:     post
title:      javascript基础注意点
author:     葱葱
tags: 		javascri 笔记
subtitle:   To learn how to use a jekyll blog model and push it on the github.
category:  project1

---

## 真假值判定(boolean)
* true:非零值，空对象(empty object)，空数组(empty array)
* false:数字零，undefined(没有值)，null(没有对象)，NaN，''
## 查看元素类型
* typeof:直接显示变量的数据类型
* instanceof:判断变量是否为通过Constr构造器构造的对象
## 运算符/操作符
* 常规（宽松）的相等：== ，！= 
* 严格的相等：=== ， ！== 
* 严格是指不但值相等，数据类型也相同；宽松意义的相等只需值相等即可。
* javscript中没有比较对象的方法(用new构造的对象(类)之间无法进行比较)
* 异或的异或为原始数据（该性质可用于数据的加密解密）
* 左移时空缺处补0，右移时若为带符号数则补为符号位，若无符号则补为0
* javascript可以运用delete运算符删除对象的某一属性或数组的某一元素
* “,”运算符的作用为从左到右执行表达式，最后返回最右边的表达式的结果
* call 运算符：改变函数当前this指针的指向，可更改当前执行上下文

```python
//例：showStudentInfo为一种函数方法

      var stu1=new Student("Tom",20);
      var stu2=new Student("Lily",21);
      showStudentInfo.call(stu1); //对stu1调用方法
      showStudentInfo.call(stu2); //对stu2调用方法
      }
```
## 数字
* javascript 中的数字全为float型，可通过math.ceil(向上) math.floor(向下) 对数字进行取整
* NaN表示not a number
* 强制类型转换为int用parseInt，强制转换为float型用parseFloat
##函数
* 格式：
```python
    function 函数名（参数）{
        [语句组];
        [return [表达式] ];
    }
```
* 函数可作为参数直接传递给另外的函数
* 函数的参数通过arguments变量使参数可用，arguments具有长度和值，但是没有数组的方法
* 参数太多会忽略额外的参数（arguments除外），丢失的参数会得到undefined
* 函数的返回值类型包括值类型，引用类型和函数类型。值类型返回的使数据的副本，用于返回非对象数据；引用类型返回的是数据的地址，通常返回复合类型数据；返回函数返回函数指针（外部函数不能调用私有函数）。
* 公有函数指定义在全局作用域的函数，可被所有代码调用的函数；私有函数是指处于局部作用域（嵌套函数的子级函数），外部函数不可调用。
##变量名及书写
* javascript区分大小写，大小写不同的变量为不同变量执行不同操作，变量命名以字母和下划线开头
* 多余的空格会被忽略，同一语句可以分多行书写，而字符串若分行则需用+连接
* 用new创建的对象要删除时必须对引用对象的变量赋值为null
* 创建日期对象时要先用new构造一个Date对象，然后可对该对象进行取（设）年/月/日的操作
```python
      var time=new Date(); //新建一个日期对象
      var year=time.getYear(); //新建一个变量
      document.write(year);
```
## 字符串
* 字符串的字符索引从0开始
* 一字符串类型变量与一数字类型变量相加时，数字变量会先被强制转换为字符串类型，然后执行字符串连接操作
* javascript可直接写入HTML代码，输出时该HTML代码会被执行

```python
//例：对数组进行由小到大排列

  var oMyArray=new Array(13,55,37,33,45,9,60,21,10);
      document.write("排序前："+oMyArray);
      for (index in oMyArray) {
        for (i in oMyArray) {
          if (oMyArray[index]<oMyArray[i]) {
            nTemp=oMyArray[index];
            oMyArray[index]=oMyArray[i];
            oMyArray[i]=nTemp;
            document.write("<br>排序后："+oMyArray);
          }
        }
      }
```

## 数组
* 对数组进行排序时，操作对象为数组本身，执行交换操作会实时对数组本身进行操作从而更改原数组数据顺序
* **in**操作符：检查对象中是否有特定属性，可以取得数组索引集合
* 数组的索引也从0开始
* **push**属性可将某值加入数组中
* 删除数组元素：**delete**
```python
      var Ary = [1,3,5,7,9,12,16,34]; //新建一个数组变量
      document.write(Ary);
      document.write("<br>");
      delete Ary[5]; //删除数组下标为5的元素
      document.write(Ary);
```
* 采用toString将数组转换成字符串分隔符只能为“，”若想要自定义分隔符则应使用join
```python
      var Ary = ["lily","andy","tim","max","jone"];
      document.write(Ary);
      document.write("<br>");
      document.write(Ary.join("*")); //用*连接元素
```
* pop函数和shift函数的返回值分别为数组最后一个元素和数组第一个元素，对原数组执行删除尾元素和删除头元素的操作。
* unshift可在数组头部添加元素，concat可以连接多个数组。
* splice可以删除数组从某一位置起的一个或多个元素并可将其替换为其它元素,函数返回被删除的元素。
```python
    /*删除数组Ary从下标为1的元素起的3个元素，并在删除位置上插入"red","yellow","green","blue" */    
      Ary3=Ary.splice(1,3,"red","yellow","green","blue"); 
      document.write(Ary3); //被删除的元素
      document.write("<br>");
      document.write(Ary); //被替换之后的原数组
      document.write("<br>");
```
> ***数组的其它操作***

> * 颠倒数组顺序：reverse();
> * 对数组进行排序：sort(); //默认为ASCLL码升序
> * 将对象转换为本地字符串：toLocaleString();
## 异常处理
* try-catch语句
```python
try{
    tryStatements; //必选项，可能发生错误的语句
}
catch(exception){ //exception用于引用错误发生时的对象
    catchStatements; //可选项，错误处理语句
}

```
* try-catch-finally语句
```python
try{
    tryStatements; //必选项，可能发生错误的语句
}
catch(exception){ //exception用于引用错误发生时的对象
    handleStatements; //可选项，错误处理语句
}
finally{
    finallyStatements; //可选项，在其他过程执行结束后无条件执行的语句
}
```
* throw语句：多个异常处理结构嵌套时，处于里层的try-catch语句可将异常抛出，父级try-catch语句可以接收子级抛出的异常
```python
      try {
        var total = 100;
        var parts = 0;
        if (parts == 0) {
          throw "Error:parts is zero"; //抛出异常信息
        }
        alert("每人" + total/parts + "份")
      } catch (e) {
        alert(e); //输出异常信息
      }
```







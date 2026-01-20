# 1.反射相关

### 1.获取Type

- #### 三种方法

- ##### 一、 通过万物之父Object中的GetType()获取对象的Type
![](pic/CSharp基础知识_images_1.png)

- ##### 二、通过typeof关键字 传入类名
![](pic/CSharp基础知识_images_2.png)
![](pic/CSharp基础知识_images_3.png)
![](pic/CSharp基础知识_images_4.png)
![](pic/CSharp基础知识_images_5.png)
- ##### 三、通过类名获取类型(必须包含命名空间)
![](pic/CSharp基础知识_images_6.png)
![](pic/CSharp基础知识_images_7.png)
![](pic/CSharp基础知识_images_8.png)
### 2.获取类的程序集信息
![](pic/CSharp基础知识_images_9.png)

### 3.获取类中所有公共成员
![](pic/CSharp基础知识_images_10.png)

### 4.获取类的公共构造函数并调用
![](pic/CSharp基础知识_images_11.png)
![](pic/CSharp基础知识_images_12.png)

### 5.获取公共成员变量
![](pic/CSharp基础知识_images_13.png)

### 6.获取类的公共成员方法

![](pic/CSharp基础知识_images_14.png)

### 其它
![](pic/CSharp基础知识_images_15.png)

### Assembly和Activator用法
![](pic/CSharp基础知识_images_16.png)

# 2.委托/事件相关

### ①.委托相关

#### 1.委托是什么

![](pic/CSharp基础知识_images_17.png)

#### 2.自定义委托

![](pic/CSharp基础知识_images_18.png)

````ad-warning

委托==默认修饰符为public ==

声明委托==相当于制定了一个规则==  但是并未使用 


### 同一语句块中 委托的==命名不能重复== ==即使参数不一样==

# 可以有参有返回值 并且 支持泛型

````

#### 3. 使用委托
![](pic/CSharp基础知识_images_19.png)
![](pic/CSharp基础知识_images_20.png)

![](pic/CSharp基础知识_images_21.png)
![](pic/CSharp基础知识_images_22.png)
````ad-warning

# 委托函数和要装载的函数 格式必须一致 

比如此处如果用MyFun f = new MyFun(Fun2)/ ,MyFun f = Fun2; 会报错 

````


#### 知识点六 系统定义好的委托 

- 使用系统自带委托 需要引用using System; 
- 无参无返回值 
- *Action action = Fun;* 
- *action += Fun3;* 
- *action();* 
  
- 可以指定返回值类型的 泛型委托 
- *Func<\string> funcString = Fun4;* 
- *Func<\int> funcInt = Fun5;* 
  
- 可以传n个参数的  系统提供了 1到16个参数的委托 直接用就行了 
- *Action<int, string> action2 = Fun6;* 
  
- 可以穿n个参数的 并且有返回值的 系统也提供了 16个委托 
- *Func<int, int> func2 = Fun2;*

### ②事件相关

#### 1. 事件是什么

- 事件是基于委托的存在 
- 事件是委托的安全包裹 
- 让委托的使用更具有安全性 
- 事件 是一种特殊的变量类型

#### 2. 事件的使用 

- 申明语法： 
- 访问修饰符 event 委托类型 事件名; 
- 事件的使用： 
- 1.事件是作为 成员变量存在于类中 
- 2.委托怎么用 事件就怎么用 
- 事件相对于委托的区别: 
- 1.==不能在类外部 赋值 ==
- 2.==不能再类外部 调用 ==
- 注意： 
- 它==只能作为成员存在于类和接口以及结构体中==
- ==不能作为临时变量在函数中使用==
- class Test 
- { 
- 委托成员变量 用于存储 函数的 
- public Action myFun; 
- 事件成员变量 用于存储 函数的 
- public event Action myEvent; 
  
-     *public Test()* 
-     *{* 
- 事件的使用和委托 一模一样 只是有些 细微的区别 
-         *myFun = TestFun;* 
-         *myFun += TestFun;* 
-         *myFun -= TestFun;* 
-         *myFun();        myFun.Invoke();* 
-         *myFun = null;* 
  
-        *myEvent = TestFun;* 
-         *myEvent += TestFun;* 
-         *myEvent -= TestFun;* 
-         *myEvent();        myEvent.Invoke();* 
-         *myEvent = null;* 
- *}* 

-     *public void DoEvent()* 
-     *{*
-         *if(myEvent != null)* 
-         *{* 
-             *myEvent();* 
-         *}*
-     *}* 

-     *public void TestFun()* 
-     *{*
-         *Console.WriteLine("123");* 
-     *}*
- *}*

#### 3.为什么有事件 

- 1.防止外部随意置空委托 
- 2.防止外部随意调用委托 
- 3.事件相当于对委托进行了一次封装 让其更加安全


#### 4. EventHandler

![](pic/CSharp基础知识_images_23.png)
#### 5.EventArgs

![](pic/CSharp基础知识_images_24.png)









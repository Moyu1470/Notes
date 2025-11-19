## Unity跨平台的基本原理

### ①.了解.Net相关知识

![](static/CSharp进阶知识补充_images_1.png)
![](static/CSharp进阶知识补充_images_2.png)
![](static/CSharp进阶知识补充_images_3.png)
![](static/CSharp进阶知识补充_images_4.png)
![](static/CSharp进阶知识补充_images_5.png)
![](static/CSharp进阶知识补充_images_6.png)
![](static/CSharp进阶知识补充_images_7.png)
![](static/CSharp进阶知识补充_images_8.png)
![](static/CSharp进阶知识补充_images_9.png)
![](static/CSharp进阶知识补充_images_10.png)
![](static/CSharp进阶知识补充_images_11.png)
![](static/CSharp进阶知识补充_images_12.png)![](static/CSharp进阶知识补充_images_13.png)
![](static/CSharp进阶知识补充_images_14.png)
![](static/CSharp进阶知识补充_images_15.png)
![](static/CSharp进阶知识补充_images_16.png)
![](static/CSharp进阶知识补充_images_17.png)
![](static/CSharp进阶知识补充_images_18.png)



### ②.Unity跨平台的基本原理

![](static/CSharp进阶知识补充_images_19.png)
![](static/CSharp进阶知识补充_images_20.png)
![](static/CSharp进阶知识补充_images_21.png)
![](static/CSharp进阶知识补充_images_22.png)
![](static/CSharp进阶知识补充_images_23.png)
![](static/CSharp进阶知识补充_images_24.png)
![](static/CSharp进阶知识补充_images_25.png)
![](static/CSharp进阶知识补充_images_26.png)
![](static/CSharp进阶知识补充_images_27.png)
![](static/CSharp进阶知识补充_images_28.png)


### ③Unity跨平台的基本原理(IL2CPP)

#### Unity跨平台的基本原理(IL2CPP)

![](static/CSharp进阶知识补充_images_29.png)
![](static/CSharp进阶知识补充_images_30.png)
![](static/CSharp进阶知识补充_images_31.png)
![](static/CSharp进阶知识补充_images_32.png)
![](static/CSharp进阶知识补充_images_33.png)
![](static/CSharp进阶知识补充_images_34.png)
![](static/CSharp进阶知识补充_images_35.png)
![](static/CSharp进阶知识补充_images_36.png)
![](static/CSharp进阶知识补充_images_37.png)
![](static/CSharp进阶知识补充_images_38.png)
![](static/CSharp进阶知识补充_images_39.png)
![](static/CSharp进阶知识补充_images_40.png)

### ③IL2CPP模式可能存在的问题处理

#### IL2CPP模式可能存在的问题处理

##### 知识点一 ——安装Unity IL2CPP打包工具

- 在Unityhub中下载 IL2CPP打包相关工具
![](static/CSharp进阶知识补充_images_41.png)
![](static/CSharp进阶知识补充_images_42.png)




##### 知识点二 ——IL2CPP打包存在的问题——类型裁剪

- IL2CPP在打包时会自动对Unity工程的DLL进行裁剪，将代码中没有引用到的类型裁剪掉，
- 以达到减小发布后包的尺寸的目的
- 然而在实际使用过程中，很多类型有可能会被意外剪裁掉，
- 造成运行时抛出找不到某个类型的异常
- 特别是通过反射等方式在编译时无法得知的函数调用，在运行时都很有可能遇到问题

- ### 解决方案：
![](static/CSharp进阶知识补充_images_43.png)
- 1.IL2CPP处理模式时，将PlayerSetting -> Other Setting -> Managed Stripping Level(代码剥离)设置为Low
- Disable:Mono模式下才能设置为不删除任何代码
- Low:默认低级别，保守的删除代码，删除大多数无法访问的代码，同时也最大程度减少剥离实际使用的代码的可能性
- Medium:中等级别，不如低级别剥离谨慎，也不会达到高级别的极端
- Hight:高级别，尽可能多的删除无法访问的代码，优先优化尺寸减小。如果选择该模式一般需要配合link.xml使用

- 2.通过Unity提供的link.xml方式来告诉Unity引擎，哪些类型是不能够被剪裁掉的
- 在Unity工程的Assets目录中（或其任何子目录中）建立一个叫Link.xml的XML文件


##### 知识点三 ——IL2CPP打包存在的问题——泛型问题


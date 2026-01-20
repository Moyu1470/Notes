## 一、ScriptableObject概述

![](pic/Unity进阶之ScriptableObject_images_1.png)
![](pic/Unity进阶之ScriptableObject_images_2.png)
![](pic/Unity进阶之ScriptableObject_images_3.png)
![](pic/Unity进阶之ScriptableObject_images_4.png)
![](pic/Unity进阶之ScriptableObject_images_5.png)
![](pic/Unity进阶之ScriptableObject_images_6.png)
![](pic/Unity进阶之ScriptableObject_images_7.png)
## 二、数据文件的创建

#### 数据文件的创建

##### 知识点一 自定义ScriptableObject数据容器 

- 1.继承ScriptableObject类 
- 2.在该类中声明成员（变量、方法等） 
  
- 注意：声明后，我们边可以在Inspector窗口中看到变化 
-      我们可以在其中进行设置，但是这些设置都是默认数据，并没有真正使用他们 
-      这些关联信息都是通过脚本文件对应的Unity配置文件meta进行记录的 
-      目前该数据只是一个数据容器模板 
-      有了它我们之后才能根据它的信息创建对应的数据资源文件

##### 知识点二 根据自定义的ScriptableObject数据容器创建数据文件 

- 注意： 
- 该创建功能，其实就是根据自定义数据容器类创建了一个配置文件 
- 该文件中记录了对应的数据容器类信息，以及其中变量关联的信息 
- 之后我们在使用它时，本质上也是通过反射创建对象进行使用 
  
- 具体的方法有两种： 
- 1.为类添加CreateAssetMenu通过菜单创建资源特性 
- [CreateAssetMenu(fileName = "默认文件名", menuName = "在Asset/Create菜单中显示的名字", order = 再Asset/Create菜单中的位置(多个时可以通过它来调整顺序))] 
  
- 2.利用ScriptableObject的静态方法创建数据对象 
-   然后将数据对象保存在工程目录下

##### 知识点三 ScriptableObject好处的体现 

- 1.更方便的配置数据,我们可以直接在Inspector当中配置数据 
- 2.项目之间的复用,我们可以拷贝继承ScriptableObject的脚本到任何工程中

##### 总结 

- 创建ScriptableObject数据类非常简单 
- 1.继承它 
- 2.声明需要的数据变量 
- 3.添加对应的特性，让我们可以在Unity中真正的创建出数据资源文件
![](pic/Unity进阶之ScriptableObject_images_8.png)
![](pic/Unity进阶之ScriptableObject_images_9.png)

##### 练习题
![](pic/Unity进阶之ScriptableObject_images_10.png)

![](pic/Unity进阶之ScriptableObject_images_11.png)

## 三、ScriptableObject数据文件的使用

#### 数据文件的使用

##### 知识点一 ScriptableObject数据文件的使用 

- 1.通过Inspector中的public变量进行关联 
- 1-1.创建一个数据文件 
- 1-2.在继承MonoBehaviour类中申明数据容器类型的成员 
-     在Inspector窗口进行关联 
- data.PrintInfo(); 
  
- 2.通过资源加载的信息关联 
- 加载数据文件资源 
- 注意：Resources、AB包、Addressables都支持加载继承ScriptableObject的数据文件 
- data = Resources.Load\<MyData>("MyDataTest");  
- data.PrintInfo(); 
  
- 注意：如果多个对象关联同一个数据容器文件，他们共享的是一个对象 
-      因为是引用对象，所以在其中任何地方修改后，其它地方也会发生改变

##### 知识点二 ScriptableObject的生命周期函数 

- ScriptableObject和MonoBehavior很类似 
- 它也存在生命周期函数 
- 但是生命周期函数的数量更少 
- 主要做了解，一般我们使用较少 
  
- Awake 数据文件创建时调用 
  
- OnDestroy ScriptableObject 对象将被销毁时调用 
- OnDisable ScriptableObject 对象销毁时、即将重新加载脚本程序集时 调用 
- OnEnable ScriptableObject 创建或者加载对象时调用 
  
- OnValidate 编辑器才会调用的函数，Unity在加载脚本或者Inspector窗口中更改值时调用

##### 知识点三 ScriptableObject好处的体现 

- 1.编辑器中的数据持久化 
- 通过代码修改数据对象中内容，会影响数据文件 
- 相当于达到了编辑器中数据持久化的目的 
- (该数据持久化 只是在编辑模式下的持久,发布运行时并不会保存数据) 
- data.i = 9999; 
- data.f = 5.5f; 
- data.b = false; 
  
- 2.复用数据 
- 如果多个对象关联同一个数据文件 
- 相当于他们复用了一组数据，内存上更加节约空间

##### 总结 

- 其实创建出来的数据资源文件，你可以把它理解成一种记录数据的资源 
- 它的使用方式，和我们以前使用Unity当中的其它资源规则是一样的 
- 比如：预设体、音频文件、视频文件、动画控制器文件、材质球等等 
- 只不过通过继承ScriptableObject类生成的数据资源文件，它主要是和数据相关的

##### 练习题

![](pic/Unity进阶之ScriptableObject_images_12.png)
![](pic/Unity进阶之ScriptableObject_images_13.png)

## 四、ScriptableObject非持久数据

#### 非持久数据

##### 知识点一 ScriptableObject的非持久化数据指的是什么 

- 指的是不管在编辑器模式还是在发布后都 不会持久化的数据 
- 我们可以根据自己的需求随时创建对应数据对象进行使用 
- 就好像直接new一个数据结构类对象

##### 知识点二 如何利用ScriptableObject生成非持久化的数据 

- 利用ScriptableObject中的静态方法 CreateInstance<>() 
- 该方法可以在运行时创建出指定继承ScriptableObject的对象 
- 该对象只存在于内存当中，可以被GC 
- 调用一次就创建一次 
  
- 通过这种方式创建出来的数据对象 它里面的默认值 不会受到脚本中设置的影响 
- *data = ScriptableObject.CreateInstance("MyData") as MyData;* 
- *data = ScriptableObject.CreateInstance\<MyData>();* 
  
- *data.PrintInfo();*

##### 知识点三 ScriptableObject的非持久化数据存在的意义 

- 只是希望在运行时能有一组唯一的数据可以使用 
- 但是这个数据又不太希望保存为数据资源文件浪费硬盘空间 
- 那么ScriptableObject的非持久化数据就有了存在的意义 
- 它的特点是 
- 只在运行时使用，在编辑器模式下也不会保存在本地

##### 练习题

![](pic/Unity进阶之ScriptableObject_images_14.png)

![](pic/Unity进阶之ScriptableObject_images_15.png)

## 五、ScriptableObject让其真正意义的持久

#### 让其真正意义上的持久

##### 知识点一 回顾通过ScriptableObject创建非持久化数据 

- MyData data = ScriptableObject.CreateInstance\<MyData>();

##### 知识点二 回顾数据持久化 

- 硬盘<=>内存 
- 使用数据时从硬盘中读取 
- 数据改变后保存到硬盘上 
- 游戏退出程序关闭后，数据信息会被存储到硬盘上，达到持久化的目的 
  
- 我们讲授过的数据持久化相关知识 
- PlayerPrefs 
- XML 
- Json 
- 2进制 
  
- ScriptableObject并不适合用来做数据持久化功能 
- 但是我们可以利用我们学过的数据持久化方案 让其持久化

##### 知识点三 利用Json结合ScriptableObject存储数据 

- data.PrintInfo(); 
  
- data.i = 9999; 
- data.f = 6.6f; 
- data.b = true; 
- 将数据对象 序列化为 json字符串 
- string str = JsonUtility.ToJson(data); 
- print(str); 
- - 把数据序列化后的结果 存入指定路径当中 
- File.WriteAllText(Application.persistentDataPath + "/testJson.json", str); 
- print(Application.persistentDataPath);


##### 知识点四 利用Json结合ScriptableObject读取数据 

- 从本地读取 Json字符串 
- string str = File.ReadAllText(Application.persistentDataPath + "/testJson.json"); 
- 根据json字符串反序列化出数据 将内容覆盖到数据对象中 
- JsonUtility.FromJsonOverwrite(str, data); 
- data.PrintInfo();

##### 总结 

- 对于ScriptableObject的数据 
- 由于它在游戏发布运行过程中无法被持久化 
- 我们可以利用 PlayerPrefs、XML、Json、2进制等等方式 
- 让其可以达到被真正持久化的目的 
  
- 但是我个人并不建议大家利用ScriptableObject来做数据持久化 
- 有点画蛇添足的意思了

##### 练习题

![](pic/Unity进阶之ScriptableObject_images_16.png)

![](pic/Unity进阶之ScriptableObject_images_17.png)
![](pic/Unity进阶之ScriptableObject_images_18.png)

## 六、ScriptableObjcet的应用

#### 1.配置数据

##### 知识点一 ScriptableObject数据文件为什么非常适合用来做配置文件? 

- 1.配置文件的数据在游戏发布之前定规则 
- 2.配置文件的数据在游戏运行时只会读出来使用，不会改变内容 
- 3.在Unity的Inspector窗口进行配置更加的方便

##### 知识点二 举例制作 

- 以前我们的常规配置方式 
- 都是利用之前学习过的 数据持久化四部曲当中的内容进行配置的 
- 比如 xml配置 json配置 excel配置 
  
- for (int i = 0; i < info.roleList.Count; i++) 
- { 
-     info.roleList[i].Print(); 
- }

##### 总结 

- 只用不改 
- 并且经常会进行配置的数据 
- 非常适合使用ScriptableObject 
  
- 我们可以利用ScriptableObject数据文件 来制作编辑器相关功能 
- 比如：Unity内置的技能编辑器、关卡编辑器等等 
-       我们不需要把编辑器生成的数据生成别的数据文件，而是直接通过ScriptableObject进行存储 
-       因为内置编辑器只会在编辑模式下运行，编辑模式下ScriptableObject具备数据持久化的特性

![](pic/Unity进阶之ScriptableObject_images_19.png)

#### 2.复用数据

##### 知识点一 使用预设体对象可能存在的内存浪费问题 

- 对于只用不变的数据 
- 以面向对象的思想去声明对象类是可能存在内存浪费的问题的 
  
- 我们以子弹对象为例

![](pic/Unity进阶之ScriptableObject_images_20.png)
![](pic/Unity进阶之ScriptableObject_images_21.png)
##### 知识点二 举例说明 利用ScriptableObject数据对象 更加节约内存

````ad-tip

ScriptableObject数据能够复用 多个不同对象 提取的都是里面的同一个数据或对象

而其他对象声明数据都得新建对象或者数据
````

##### 总结 

- 对于不同对象，使用相同数据时 
- 我们可以使用ScriptableObject来节约内存

#### 3.数据带来的多态行为

##### 知识点一 什么是数据带来的多态行为 

- 某些行为的变化是因为数据的不同带来的 
- 我们可以利用面向对象的特性和原则，以及设计模式相关知识点 
- 结合ScriptableObject做出更加方便的功能 
  
- 比如随机音效，物品拾取，AI等等等 
  
- 随机音效（里氏替换原则和依赖倒转原则） 
- 播放音乐时，可能会随机播放多个音效当中的一种 
  
- 物品拾取（里氏替换原则和依赖倒转原则） 
- 比如拾取一个物品，物品给玩家带来不同的效果 
  
- AI 
- 不同数据带来的不同行为模式 
  
- 为了方便我们使用，我们可以利用ScriptableObject的可配置性来制作这些功能

##### 知识点二 举例说明

![](pic/Unity进阶之ScriptableObject_images_22.png)

![](pic/Unity进阶之ScriptableObject_images_23.png)

![](pic/Unity进阶之ScriptableObject_images_24.png)

![](pic/Unity进阶之ScriptableObject_images_25.png)

![](pic/Unity进阶之ScriptableObject_images_26.png)

![](pic/Unity进阶之ScriptableObject_images_27.png)

![](pic/Unity进阶之ScriptableObject_images_28.png)

#### 4.单例模式化的获取数据

##### 知识点一 为什么要单例模式化的获取数据 

- 对于只用不变并且要复用的数据 
- 比如配置文件中的数据 
- 我们往往需要在很多地方获取他们 
- 如果我们直接通过在脚本中 public关联 或者 动态加载 
- 如果在多处使用，会存在很多重复代码，效率较低 
- 如果我们将此类数据通过单例模式化的去获取 
- 可以提升效率，减少代码量

##### 知识点二 实现单例模式化获取数据 

- 知识点 
- 面向对象、单例模式、泛型等等 
  
- 我们可以实现一个ScriptableObject数据单例模式基类 
- 让我们只需要让子类继承该基类 
- 就可以直接获取到数据 
- 而不再需要去通过 public关联 和 资源动态加载 
  
- *print(RoleInfo.Instance.roleList[0].id);* 
- *print(RoleInfo.Instance.roleList[1].tips);* 
  
- *print(TestData.Instance.i);* 
- *print(TestData.Instance.b);*

##### 总结 

- 这种基类比较适合 配置数据 的管理和获取 
- 当我们的数据是 只用不变，并且是唯一的时候，可以使用该方式提高我们的开发效率 
- 在此基础上你也可以根据自己的需求进行变形 
- 比如添加数据持久化的功能，将数据从json中读取，并提供保存数据的方法 
- 但是不建议大家用ScriptableObject来制作数据持久化功能 
- 除非你有这方面的特殊需求

![](pic/Unity进阶之ScriptableObject_images_29.png)

![](pic/Unity进阶之ScriptableObject_images_30.png)

![](pic/Unity进阶之ScriptableObject_images_31.png)

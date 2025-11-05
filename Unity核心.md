## 一、Unity核心概述
![](static/Unity核心_images_1.png)
![](static/Unity核心_images_2.png)
![](static/Unity核心_images_3.png)
![](static/Unity核心_images_4.png)
![](static/Unity核心_images_5.png)





## 二、认识模型的制作流程
### 模型制作流程

#### 第一步：建模
![](static/Unity核心_images_6.png)
#### 第二步：展UV
![](static/Unity核心_images_7.png)
#### 第三步：材质和纹理贴图
![](static/Unity核心_images_8.png)
#### 第四步：骨骼绑定
![](static/Unity核心_images_9.png)
#### 第五步：动画制作
![](static/Unity核心_images_10.png)





















## 三、2D相关

### ①. 图片导入设置

#### 1.图片导入概述

##### 知识点一 Unity支持的图片格式

- Unity支持的图片格式有很多 
- BMP:是Windows操作系统的标准图像文件格式，特点是几乎不进行压缩，占磁盘空间大 
- TIF:基本不损失图片信息的图片格式，缺点是体积大 
- JPG:一般指JPEG格式，属于有损压缩格式，能够让图像压缩在很小的存储空间，一定程度上会损失图片数据，无透明通道 
- PNG:无损压缩算法的位图格式，压缩比高，生成文件小，有透明通道 
- TGA:支持压缩，使用不失真的压缩算法，还支持编码压缩。体积小，效果清晰，兼备BMP的图像质量和JPG的体积优势，有透明通道 
- PSD:是PhotoShop（PS）图形处理软件专用的格式，通过一些第三方工具或自制工具可以直接将PSD界面转为UI界面 
- 其它还支持 
- EXR、GIF、HDR、IFF、PICT等等 
- 其中Unity最常用的图片格式是 
- JPG、PNG、TGA三种格式

##### 知识点二 图片设置的6大部分

- 1.纹理类型 
- 2.纹理形状 
- 3.高级设置 
- 4.平铺拉伸 
- 5.平台设置 
- 6.预览窗口
![](static/Unity核心_images_11.png)

#### 2.纹理类型设置

##### 知识点一 纹理形状主要是设置什么？ 

- 纹理不仅可以用于模型贴图 
- 还可以用于制作天空盒和反射探针 
- 纹理形状设置 主要就是用于在两种模式之间进行切换

##### 知识点二 设置讲解

![](static/Unity核心_images_12.png)
![](static/Unity核心_images_13.png)

![](static/Unity核心_images_14.png)
![](static/Unity核心_images_15.png)
#### 3. 参数设置——纹理形状

##### 知识点一 纹理形状主要是设置什么？ 

- 纹理不仅可以用于模型贴图 
- 还可以用于制作天空盒和反射探针 
- 纹理形状设置 主要就是用于在两种模式之间进行切换

##### 知识点二 参数讲解

![](static/Unity核心_images_16.png)

#### 4. 纹理高级设置

##### 知识点一 高级设置是设置什么？ 

- 高级设置主要是纹理的一些尺寸规则、读写规则、以及MipMap相关设置

##### 知识点二 参数讲解

![](static/Unity核心_images_17.png)

##### 知识点三 MipMap是什么？ 
- 在三维计算机图形的贴图渲染中有一个常用的技术被称为Mipmapping。 
- 为了加快渲染速度和减少图像锯齿，贴图被处理成由一系列被预先计算和优化过的图片组成的文件 
- 这样的贴图被称为mipmap 
-  Mipmap 需要占用一定的内存空间 

- Mipmap中每一个层级的小图都是主图的一个特定比例的缩小细节的复制品 
- 虽然在某些必要的视角，主图仍然会被使用，来渲染完整的细节。 
- 但是当贴图被缩小或者只需要从远距离观看时，mipmap就会转换到适当的层级 
  
- 因为mipmap贴图需要被读取的像素远少于普通贴图，所以渲染的速度得到了提升。 
- 而且操作的时间减少了，因为mipmap的图片已经是做过抗锯齿处理的，从而减少了实时渲染的负担。 
- 放大和缩小也因为mipmap而变得更有效率。 
  
- 如果贴图的基本尺寸是256x256像素的话,它mipmap就会有8个层级。 
- 每个层级是上一层级的四分之一的大小 
- 依次层级大小就是：128x128;64x64;32x32;16x16;8x8;4x4;2x2;1x1(一个像素) 
  
- 说人话，开启MipMap功能后，Unity会帮助我们根据图片信息生成n张不同分辨率的图片 
- 在场景中会根据我们离该模型的距离选择合适尺寸的图片用于渲染，提升渲染效率

#### 5. 纹理平铺拉伸设置

##### 知识点一 平铺拉伸主要是做什么？ 

- 平铺拉伸主要设置纹理的平铺规则以及拉伸规则

##### 知识点二 参数讲解

![](static/Unity核心_images_18.png)

#### 6. 纹理平台打包相关设置

##### 知识点一 平台设置主要设置什么？ 

- 平台设置主要设置纹理最终打包时在不同平台的尺寸、格式、压缩方式 
- 它非常的重要，因为它影响了你的包大小和读取性能方面的问题

##### 知识点二 参数相关
![](static/Unity核心_images_19.png)


![](static/Unity核心_images_20.png)


![](static/Unity核心_images_21.png)
### ②.Sprite

#### 1. Sprite Editor——Single图片编辑

##### 知识点一 SpriteEditor是什么？ 
- 顾名思义，SpriteEditor就是 精灵图片编辑器 
- 它主要用于编辑2D游戏开发中使用的Sprite精灵图片 
- 它可以用于编辑 图集中提取元素，设置精灵边框，设置九宫格，设置轴心（中心）点等等功能

##### 知识点二 安装 2D Sprite

- 新版本Unity 需要安装 2D Sprite包才能使用SpriteEditor

##### 知识点三 Single图片编辑 功能讲解 
- Single图片编辑主要讲解的就是在设置图片时 
- 将精灵图片模式（Sprite Mode）设置为Single的精灵图片在Sprite Editor窗口中如何编辑 
  ![](static/Unity核心_images_22.png)
- 1.Sprite Editor 
-   基础图片设置（右下角窗口） 
-  主要用于设置单张图片的基础属性 
  
- 2.Custom Outline（决定渲染区域） 
- 自定义边缘线设置，可以自定义精灵网格的轮廓形状 
-  默认情况下不修改都是在矩形网格上渲染,边缘外部透明区域会被渲染，浪费性能 
-  使用自定义轮廓，可以调小透明区域，提高性能 
  
- 3.Custom Physics Shape（决定碰撞判断区域） 
-   自定义精灵图片的物理形状，主要用于设置需要物理碰撞判断的2D图形 
-  它决定了之后产生碰撞检测的区域 
  
- 4.Secondary Textures(为图片添加特殊效果) 
-  次要纹理设置，可以将其它纹理和该精灵图片关联 
-  着色器可以得到这些辅助纹理然后用于做一些效果处理 
-  让精灵应用其它效果


#### 2.Sprite Editor ——Multiple 图片编辑

##### 知识点一 Multiple图集元素分割 

- 当我们的图片资源是图集时 
-  我们需要在设置时将模式设置为Multiple 
- 这时我们可以使用Sprite Editor自带的功能进行图集元素分割

##### 知识点二 参数讲解

![](static/Unity核心_images_23.png)

#### 3. Sprite Wditor——Polygon图片编辑

##### 知识点一 Polygon多边形编辑

- 如果我们使用的资源是多边形资源
- 我们可以在设置时将设置模式设置为Polygon
- 然后可以在Sprite Editor 中进行快捷设置

- 但是一般这种模式在实际开发中使用较少

##### 知识点二 参数详解

![](static/Unity核心_images_24.png)

````ad-warning

如果从多边形切换回Single，需要重新生成渲染范围

````
![](static/Unity核心_images_25.png)

#### 4.SpriteRenderer精灵渲染器

##### 知识点一 Sprite Renderer是什么 

- 顾名思义，Sprite Renderer是精灵渲染器 
- 所有2D游戏中游戏资源（除UI外）都是通过Sprite Renderer让我们看到的 
- 它是2D游戏开发中的一个极为重要的组件

##### 知识点二 2D对象创建 

- 1.直接拖入Sprite图片 
- 2.右键创建 
- 3.空物体添加脚本

##### 知识点三 参数讲解

![](static/Unity核心_images_26.png)
##### 知识点四 代码设置 

- *GameObject obj = new GameObject();* 
- *SpriteRenderer sr = obj.AddComponent\<SpriteRenderer>();* 
- 动态的改变图片 
- *sr.sprite = Resources.Load\<Sprite>("dead1");* 
- 动态的加载 图集中的图 
- *Sprite[] sprs = Resources.LoadAll\<Sprite>("RobotBoyIdleSprite");* 
- *sr.sprite = sprs[10];* 
  
- *print(sprs[10].name);*

##### 练习题一 
```C#
using System.Collections;  
using System.Collections.Generic;  
using UnityEngine;  
  
public class MultipleMgr  
{  
    private static MultipleMgr instance = new MultipleMgr();  
    public static MultipleMgr Instatnce => instance;  
  
    //存储 大图对应的小图资源的信息  
    private Dictionary<string, Dictionary<string, Sprite>> dic = new Dictionary<string, Dictionary<string, Sprite>>();  
    private MultipleMgr()  
    {  
    }  
    /// <summary>  
    /// 获取Multiple图集中的某一张小图  
    /// </summary>  
    /// <param name="multipleName">图集名</param>  
    /// <param name="spriteName">单张图片名</param>  
    /// <returns></returns>    public Sprite GetSprite(string multipleName, string spriteName)  
    {        //判断是否加载过该大图  
        if( dic.ContainsKey(multipleName) )  
        {            //判断大图中是否有该小图的信息  
            if (dic[multipleName].ContainsKey(spriteName))  
                return dic[multipleName][spriteName];  
        }        else  
        {  
            Dictionary<string, Sprite> dicTmp = new Dictionary<string, Sprite>();  
            Sprite[] sprs = Resources.LoadAll<Sprite>(multipleName);  
            for (int i = 0; i < sprs.Length; i++)  
            {                dicTmp.Add(sprs[i].name, sprs[i]);  
            }  
            dic.Add(multipleName, dicTmp);  
            //判断 是否有该名字的小图  
            if( dicTmp.ContainsKey(spriteName) )  
                return dicTmp[spriteName];  
        }  
        return null;  
    }  
    public void ClearInfo()  
    {        //清空  
        dic.Clear();  
        //卸载资源  
        Resources.UnloadUnusedAssets();  
    }
}
```
![](static/Unity核心_images_27.png)

##### 练习题二

```C#
using System.Collections;  
using System.Collections.Generic;  
using UnityEngine;  
  
public class PlayerObject : MonoBehaviour  
{  
    public float moveSpeed = 5;  
    private float h;  
  
    private SpriteRenderer sr;  
    // Start is called before the first frame update  
    void Start()  
    {        sr = this.GetComponent<SpriteRenderer>();  
    }  
    // Update is called once per frame  
    void Update()  
    {        h = Input.GetAxis("Horizontal");  
        this.transform.Translate(5 * Time.deltaTime * Vector3.right * h);  
        if (h < 0)  
            sr.flipX = true;  
        else if (h > 0)  
            sr.flipX = false;  
    }}
```


#### 5.SpriteRenderer精灵创造者

#####  知识点一 Sprite Creator是什么？
- 顾名思义，Sprite Creator是精灵创造者 
- 我们可以利用Sprite Editor的多边形工具创造出各种多边形 
- Unity也为我们提供了现成的一些多边形 
  
- 它的主要作用是2D游戏的替代资源 
- 在等待美术出资源时我们可以用他们作为替代品 
- 有点类似Unity提供的自带几何体 
  
 - 替代资源是做demo和学习时的必备品

##### 知识点二 使用Sprite Creator 

- 在Project窗口右键创建各种形状的Sprite精灵图片
![](static/Unity核心_images_28.png)


#### 6. SpriteMask精灵遮罩

##### 知识点一 SpriteMask是什么？ 

- 顾名思义，SpriteMask是精灵遮罩的意思 
- 它的主要作用就是对精灵图片产生遮罩 
- 制作一些特殊的功能，比如只显示图片的一部分让玩家看到

##### 知识点二 参数相关
![](static/Unity核心_images_29.png)
![](static/Unity核心_images_30.png)
![](static/Unity核心_images_31.png)

#### 7. SortingGroup分组

##### 知识点一 SortingGroup是什么？ 

- 顾名思义，SortingGroup是排序分组的意思 
- 它的主要作用就是对多个精灵图片进行分组排序 
- Unity会将同一个排序组中的精灵图片一起排序，就好像他们是单个游戏对象一样 
- 主要作用是对于需要分层的2D游戏用于整体排序

##### 知识点二 SortingGroup的使用

![](static/Unity核心_images_32.png)

````ad-tip
每层管自己 父对象优先子对象
````
##### 知识点三 注意事项 

![](static/Unity核心_images_33.png)
![](static/Unity核心_images_34.png)
````ad-tip
SpriteRender层级中New Layer层级高于Default层
````
- 1.子排序组，先排子对象 再按父对象和别人一起排 （同层和同层比）
- 2.多个 挂载排序分组组件的预设体 之间 通过修改 排序索引号来决定前后顺序

#### 8. SpriteAtlas 精灵图集

##### 知识点一 为什么要打图集

- 打图集的目的就是减少DrawCall 提高性能

##### 知识点二 在Unity中打开自带的打图集功能 

- 在工程设置面板中打开功能 
- Edit——>Project Setting——>Editor 
- Sprite Packer(精灵包装器，可以通过Unity自带图集工具生成图集) 
- Disabled：默认设置，不会打包图集 
  
- Enabled For Builds（Legacy Sprite Packer）：Unity仅在构建时打包图集，在编辑模式下不会打包图集 
- Always Enabled（Legacy Sprite Packer）：Unity在构建时打包图集，在编辑模式下运行前会打包图集 
  
- Legacy Sprite Packer传统打包模式 相对下面两种模式来说 多了一个设置图片之间的间隔距离 
- Padding Power:选择打包算法在计算打包的精灵之间以及精灵与生成的图集边缘之间的间隔距离 
-               这里的数字 代表2的n次方 
  
- Enabled For Build：Unity进在构建时打包图集，在编辑器模式下不会打包 
- Always Enabled：Unity在构建时打包图集，在编辑模式下运行前会打包图集

##### 知识点三 打图集面板参数相关

![](static/Unity核心_images_35.png)


##### 知识点四 代码控制 

- *GameObject obj = new GameObject();* 
- *SpriteRenderer sr = obj.AddComponent\<SpriteRenderer>();* 
- 加载图集资源 
- *SpriteAtlas spriteAtlas = Resources.Load\<SpriteAtlas>("MyAtlas");* 
- //加载图集资源中的某一张小图 
- *sr.sprite = spriteAtlas.GetSprite("dead1");*

##### 知识点五 观察DrawCall数量

````ad-tip
不是图集内的图片挡在图集中的两个图片中间时(包括在同一图集不同的两个图片层级中间时) 会增加Draw Call
````


### ③. 2D物理系统

#### 1.刚体

##### 知识点一 2D物理系统中的刚体组件 

- 刚体是物理系统中用于帮助我们进行模拟物理碰撞中力的效果的 
  
- 2D物理系统中的刚体和3D中的刚体基本是一样的 
- 最大的区别是对象只会在XY平面中移动，并且只在垂直于该平面的轴上旋转

##### 知识点二 参数相关

![](static/Unity核心_images_36.png)
![](static/Unity核心_images_37.png)
##### 知识点四 如何选择不同类型的刚体 

- Dynamic动态刚体：受力的作用，要动要碰撞的对象 
- Kinematic运动学刚体：通过刚体API移动的对象，不受力的作用，但是想要进行碰撞检测  
- Static静态刚体：不动不受力作用的静态物体，但是想要进行碰撞检测

##### 知识点五 刚体API 

- 加力 
- *Rigidbody2D rigid = this.GetComponent\<Rigidbody2D>();* 
- *rigid.AddForce(new Vector2(0, 100));* 
- //速度 
- *rigid.velocity = new Vector2(1, 0);*

#### 2.碰撞器

##### 知识点一 碰撞器是用来干嘛的？ 

- 碰撞器是用于在物理系统中 表示物体体积的的（形状或范围） 
- 刚体通过得到碰撞器的范围信息进行计算 
- 判断两个物体的范围是否接触 
- 如果接触 刚体就会模拟力的效果产生速度和旋转

##### 知识点二 2D碰撞器 

- 1.圆形碰撞器 
- 2.盒状碰撞器 
 - 3.多边形碰撞器 
- 4.边界碰撞器 
- 5.胶囊碰撞器 
- 6.复合碰撞器
![](static/Unity核心_images_38.png)
![](static/Unity核心_images_39.png)

##### 知识点三 碰撞检测函数
![](static/Unity核心_images_40.png)
![](static/Unity核心_images_41.png)

#### 3. 物理材质

##### 知识点一 什么是物理材质 

- 物理材质是用于决定在物体产生碰撞时这些物体之间的摩擦和弹性表现的 
- 通过物理材质我们可以做出类似 斜坡不滑落，小球反弹等效果

##### 知识点二 参数讲解

![](static/Unity核心_images_42.png)

#### 4.恒定力

##### 知识点一 什么是恒定力？ 

- 恒定力是一个特殊的脚本 
- 它可以给一个2D刚体持续添加一个力 
- 在做一些随着时间推移而加速的对象时很适用 
- 比如类似火箭发射等效果 
  
- 恒定力脚本会线性的为对象添加力和扭矩力 让其移动和旋转

##### 知识点二 参数讲解

![](static/Unity核心_images_43.png)
#### 5.表面效应器

##### 知识点一 2D效应器是什么？ 

- 2D效应器是配合2D碰撞器一起使用 
- 可以让游戏对象在相互接触时产生一些特殊的物理作用力 
- 可以通过2D效应器 
- 快捷的实现一些 
- 传送带 互斥 吸引 漂浮 单向碰撞等等效果

##### 知识点二 不同种类2D效应器的使用  
- 1.区域效应器 
![](static/Unity核心_images_44.png)
- 2.浮力效应器 
![](static/Unity核心_images_45.png)
- 3.点效应器 
![](static/Unity核心_images_46.png)
- 4.平台效应器 
![](static/Unity核心_images_47.png)
- 5.表面效应器

![](static/Unity核心_images_48.png)


### ④. SpriteShape

#### 1. SpriteShapeProfile精灵形状概述文件

##### 知识点一 SpriteShape是用来做什么的？ 

- 顾名思义，SpriteShape是精灵形状的意思 
- 从名字上看不出到底是用来干什么的 
- 其它它主要是方便我们以节约美术资源为前提 
- 制作2D游戏场景地形或者背景的

##### 知识点二 导入SpriteShape工具 

- 1.在Package Manager中导入相关工具  
- 2.可以选择性导入事例和拓展资源

##### 知识点三 准备 精灵形状概括资源 

- 想要节约美术资源的创建地形或其它类似资源 
- 首先我们要准备精灵形状概括资源 
- 之后我们就会使用它来创建地形等资源 
  
- 1.开放不封闭的图形 
- 2.封闭的图形

##### 知识点四 使用精灵形状概括资源创建地形

![](static/Unity核心_images_49.png)





#### 2.SpriteShapeRenderer和Controller知识点

##### 知识点一 Sprite Shape Renderer参数相关

![](static/Unity核心_images_50.png)


![](static/Unity核心_images_51.png)



##### 知识点二 Sprite Shape Controller参数相关

![](static/Unity核心_images_52.png)


##### 知识点三 生成碰撞器

- 1.使用边界碰撞器 

![](static/Unity核心_images_53.png)

- 2.使用多边形 碰撞器 配合复合碰撞器
![](static/Unity核心_images_54.png)
````ad-tip

勾选 Used By Composite 来生成复合碰撞器 否则会生成多边形组成的碰撞器

另外多边形碰撞器有一个缺点：会强制生成一个刚体 可以将刚体的 Body Type 改为static避免墙体发生不必要的碰撞效果

````

### ⑤.Tilemap
#### 1.瓦片资源

##### 知识点一 什么是Tilemap？ 

- Tilemap一般称之为 瓦片地图或者平铺地图 
- 是Unity2017中新增的功能 
- 主要用于快速编辑2D游戏中的场景 
- 通过复用资源的形式提升地图多样性 
  
- 工作原理就是用一张张的小图排列组合为一张大地图 
  
- 它和SpriteShape的异同 
- 共同点 ：
- 他们都是用于制作2D游戏的场景或地图的 

- 不同点 ：
- 1.SpriteShape可以让地形有弧度,TileMap不行 
- 2.TileMap可以快捷制作有伪“Z”轴的地图，SpriteShape不行

##### 知识点二 从PackageManager中引入Tilemap包

![](static/Unity核心_images_55.png)

##### 知识点三 Tilemap的最小单位——"瓦片" 

- 首先导入学习用资源  
  
- 方法一： 
- Assets——>Create——>Tile 
  
- 方法二： 
- 在Tile Palette瓦片调色板窗口创建 
- 1.首先新建一个瓦片地图编辑文件 
- 2.将资源拖入到窗口中选择要保存的路径
![](static/Unity核心_images_56.png)
#### 2.瓦片调色板

##### 知识点一 创建瓦片调色器相关参数
![](static/Unity核心_images_57.png)

##### 知识点二 TilePalette瓦片调色板窗口基本操作技巧

![](static/Unity核心_images_58.png)

##### 知识点三 TilePalette瓦片调色板窗口面板基本功能

![](static/Unity核心_images_59.png)

##### 知识点四 编辑瓦片地图 

- 方法一：通过瓦片调色板文件创建 
- 方法二：直接在场景中进行创建 
  
- 矩形瓦片地图用于做横版游戏地图 
- 六边形瓦片地图用于做策略游戏地图 
- 等距瓦片地图用于做有"Z"轴的2D游戏 
  
- 注意： 
- 在编辑等距瓦片地图时 
- 1.需要修改工程的自定义轴排序 以Y轴决定渲染顺序 
- 2.如果地图存在前后关系需要修改TileRenderer的渲染模式 
- 3.可以通过Z轴偏移来控制绘制单个瓦片时的高度 
 - 4.精灵纹理的中心点会影响最终的显示效果

````ad-tip
需要在EDIT——Project Settings——Graphics中更改排序模式成自定义模式

并将X-Y-Z改成(0,1,-0.26)

再在tilemap对象的Tilemap Renderer 组件中将MODE改成individual

否则渲染顺序会有异常
````

#### 3.瓦片地图关键脚本和碰撞器

##### 知识点一 瓦片地图关键脚本参数

![](static/Unity核心_images_60.png)
##### 知识点三 瓦片地图碰撞器 

- 为挂载TilemapRenerer脚本的对象添加Tilemap Collider2D脚本 
- 会自动添加碰撞器 
- 注意：想要生成碰撞器的瓦片Collider Type类型要进行设置

#### 4.瓦片地图拓展包——导入知识点

##### 知识点一 下载官方拓展包 

- 下载地址： 
- https://github.com/Unity-Technologies/2d-extras

##### 知识点二 导入官方拓展包 

- 解压后直接拖入到Assets文件夹中即可


##### 知识点三 了解官方拓展包为Tilemap添加了什么

- 拓展包为Tilemap添加新的瓦片类型和笔刷类型 帮助我们更加方便的编辑2D场景

#### 5.瓦片地图拓展包——新增瓦片类型

##### 知识点一 规则瓦片 RuleTile

 - 定义不同方向是否存在连接图片的规则 
 - 让我们更加快捷的进行地图编辑 

  ![](static/Unity核心_images_61.png)
  ![](static/Unity核心_images_62.png)
  
#####  知识点二 动画瓦片 AnimatedTile
 
 - 可以指定序列帧 
 - 产生可以播放序列帧动画的瓦片 

  
##### 知识点三 管道瓦片 PipelineTile

 - 根据自己相邻瓦片的数量更换显示的图片 
![](static/Unity核心_images_63.png)
  
##### 知识点四 随机瓦片 RandomTile

 - 根据你设置的图片，随机从中选一个进行绘制 
![](static/Unity核心_images_64.png)
  
##### 知识点五 地形瓦片 TerrainTile

 - 有点类似规则瓦片，只不过地形瓦片是帮助你定好的规则 

  ![](static/Unity核心_images_65.png)
##### 知识点六 权重随机瓦片 WeightedRandomTile

 - 可以不平均随机选择图片的瓦片 

  ![](static/Unity核心_images_66.png)
##### 知识点七 (高级)规则覆盖瓦片 (Advanced)Rule Override TileBase

 - 在规则瓦片的基础上 改变图片或者指定启用的规则 
![](static/Unity核心_images_67.png)

![](static/Unity核心_images_68.png)
#### 6.瓦片地图拓展包——新增笔刷类型

##### 知识点一 获取Tilemap和TileBase和Grid 

- Tilemap组件：用于管理瓦片地图 
- TileBase组件：瓦片资源对象基类 
- Grid组件：用于坐标转换 
  
- 使用他们需要引用命名空间

##### 知识点二 重要API

- 1.清空瓦片地图 
- *map.ClearAllTiles();*

- 2.获取指定坐标格子 
- *TileBase tmp = map.GetTile(Vector3Int.zero);* 
- *print(tmp);*

- 3.设置删除瓦片 
- *map.SetTile(new Vector3Int(0, 2, 0), tileBase);* 
  
- *map.SetTile(new Vector3Int(1, 0, 0), null);* 
  
- *map.SetTiles()*

- 4.替换瓦片 
- *map.SwapTile(tmp, tileBase);*

- 5.世界坐标转格子坐标 
- 屏幕坐标转世界坐标 
- 世界坐标转格子坐标 
- 传入的参数是世界坐标 
- *grid.WorldToCell()*

![](static/Unity核心_images_69.png)



#### 7.瓦片地图——代码控制

##### 知识点一 获取Tilemap和TileBase和Grid
- Tilemap组件： 用于管理瓦片地图
- TileBase组件： 瓦片资源对象基类
- Grid组件： 用于坐标转换

##### 知识点二 重要API
- 1. 清空瓦片地图
- *map.ClearAllTiles();*

- 2.获取指定坐标格子
- *TileBase tmp = map.GetTile(new Vector3Int(0,0,0));*

- 3.设置删除瓦片
- *map.SetTile(new Vector3Int(0,0,0),tileBase)*  //设置
- *map.SetTile(new Vector3Int(0,0,0),null)*  //删除

- 4.替换瓦片
- *map.SwapTile(tmp,tileBase);*  //批量替换

- 5.世界坐标转格子坐标
- 屏幕坐标转世界坐标
- *Vector3 ScreenPosition = Input.mousePositon;*
- *Camera.ScreenToWorldPoint(new Vector3(screenPosition.x,screenPoint.y,1))*
- 世界坐标转格子坐标
- *grid.WorldToCell()*

## 四、动画基础

### ①. Animation动画窗口

#### 1. 认识Animation动画窗口

##### 知识点一 打开Animation窗口
- Window —> Animation ——>Animation

##### 知识点二 Animation窗口是用来干啥的
- Animation窗口 直译就是动画窗口
- 它主要用于在Unity内部创建和修改动画
- 所有在场景中的对象都可以通过Animation窗口为其制作动画

- ## 原理：
- 制作动画时： 记录在固定时间点对象挂载的脚本的变量变化
- 播放动画时： 将制作动画记录的数据在固定时间点改变，产生动画效果

##### 知识点三 关键词说明
- *动画时间轴：* 
- 每一个动画文件都有自己的一个生命周期，从动画开始到结束 
- 我们可以在动画时间轴上编辑每一个动画生命周期中变化 

- *动画中的帧：* 
- 假设某个动画的帧率为60帧每秒，意味着该动画1秒钟最多会有60次改变机会 
- 每一帧的间隔时间是 1s/60 ≈ 16.67毫秒 
- 也就是说 我们最快可以每16.67毫秒改变一次对象状态 

- *关键帧：* 
- 动画在时间轴上的某一个时间节点上处于的状


- **知识点四 认识Animaiton窗口功能**
- ![](static/Unity核心_images_70.png)![](static/Unity核心_images_71.png)

#### 2. 创建编辑Animation动画

##### 知识点一 创建动画
- 1.在场景中选中想要创建动画的对象 
- 2.在Animation窗口中点击创建 
- 3.选择动画文件将要保存到的位置

##### 知识点二 窗口上的变化
- ![](static/Unity核心_images_72.png)

````ad-tip

可以通过 在录制模式开启的状态下 选择合适的帧位置 直接更改Inspector面板上的数据来直接插入关键帧

````


##### 知识点三 关键帧模式下编辑动画
![](static/Unity核心_images_73.png)

##### 知识点四 曲线模式下编辑动画
![](static/Unity核心_images_74.png)

![](static/Unity核心_images_75.png)
##### 知识点五 动画文件界面参数
- ![](static/Unity核心_images_76.png)
- ![](static/Unity核心_images_77.png)

#### 3.代码控制动画（老动画系统）

##### 知识点一 什么是老动画系统
- Unity中有两套动画系统 
- 新：Mecanim动画系统——主要用Animator组件控制动画 
- 老：Animation动画系统——主要用Animation组件控制动画（Unity4之前的版本可能会用到） 
  
- 目前我们为对象在Animation窗口创建的动画都会被新动画系统支配 
- 有特殊需求或者针对一些简易动画，才会使用老动画系统
##### 知识点二 老动画系统控制动画播放
- 注意： 
- 在创建动画之前为对象添加Animation组件之后再制作动画 
- 这时制作出的动画和之前的动画格式是有区别的 
  
- Animation参数
![](static/Unity核心_images_78.png)

##### 知识点三 代码控制播放

- 1.播放动画 
- *if(Input.GetKeyDown(KeyCode.Alpha1))* 
- *{* 
-    *animation.Play("1");* 
- *}* 

- *if (Input.GetKeyDown(KeyCode.Alpha2))* 
- *{* 
-    *animation.Play("2");* 
- *}* 
- 2.淡入播放,自动产生过渡效果 
- *if(Input.GetKeyDown(KeyCode.Alpha3))* 
- *{* 
- *当你要播放的动画的开始状态 和当前的状态 不一样时* 
- *就会产生过渡效果* 
-    *animation.CrossFade("3");* 
-    *//animation.Play("3");* 
- *}* 
  
- 3.前一个播完再播放下一个 
- *if( Input.GetKeyDown(KeyCode.Alpha4) )* 
- *{* 
-    *//animation.PlayQueued("2");* 
-    *animation.CrossFadeQueued("2");* 
- *}* 
  
- 4.停止播放所有动画 
- *animation.Stop();* 
  
- 5.是否在播放某个动画 
- *if( animation.IsPlaying("1") )* 
- *{* 
- *}* 
  
- 6.播放模式设置  
- *animation.wrapMode = WrapMode.Loop;*
  
- 7.其它（了解即可，新动画系统中会详细讲解） 
- 层级和权重以及混合（老动画系统需要通过代码来达到动画的遮罩、融合等效果） 
- 设置层级 
- *animation["1"].layer = 1;* 
- 设置权重 
- *animation["1"].weight = 1;* 
- 混合模式 叠加还是混合 
- *animation["1"].blendMode = AnimationBlendMode.Additive;* 
- 设置混组相关骨骼信息 
- *animation[""].AddMixingTransform();*

##### 知识点四 动画事件
- 动画事件主要用于处理 当动画播放到某一时刻想要触发某些逻辑  
- 比如进行伤害检测、发射子弹、特效播放等等
![](static/Unity核心_images_79.png)![](static/Unity核心_images_79.png)g)![](static/Unity核心_images_80.png)
- *public void AnimationEvent()* 
- *{* 
-   *print("动画事件触发");* 
- *}*

````ad-tip

老动画系统中 创建的关键帧 需要确保 模型上每个组件都有初始关键帧 否则模型不会回正

需要在每个需要设置关键帧的模型组件上 都设置一下位置（若要保持原样 可以将旋转角度轻微变动 再改回原先值 以添加关键帧属性）

````


### ②. Animator动画状态机

#### 1.有限状态机概念

##### 知识点一 什么是有限状态机
- 有限状态机（Finite // state machine, FSM） 
- 又称有限状态自动机，简称状态机 
- 是表示有限个状态以及在这些状态之间的转移和动作等行为的数学模型 
  
- 有限：表示是有限度的不是无限的 
- 状态：指所拥有的所有状态 
  
- 举例说明： 
- 假设我们人会做很多个动作，也就是有很多种状态 
- 这些状态包括 站立、走路、跑步、攻击、防守、睡觉等等 
- 我们每天都会在这些状态中切换，而且这些状态虽然多但是是有限的 
- 当达到某种条件时，我们就会在这些状态中进行切换 
- 而且这种切换时随时可能发生的

##### 知识点二 有限状态机对于我们的意义
- 游戏开发中有很多功能系统都是有限状态机 
- 最典型的状态机系统 
- 动作系统 —— 当满足某个条件切换一个动作，且动作是有限的 
- AI（人工智能）系统 —— 当满足某个条件切换一个状态，且状态时有限的 
  
- 所以状态机是游戏开发中一个必不可少的概念

##### 知识点三 最简单的状态机实现
- 假设我们只有一个值来控制当前玩家的状态 
- *string animName = "idle";* 
- *switch (animName)* 
- *{* 
-   *case "idle":* 
-     *//待机动作逻辑* 
-     *break;* 
- *case "move":* 
 -    *//移动动作逻辑* 
-    *break;* 
- *case "run":* 
-   *//跑步动作逻辑* 
-   *break;* 
- *case "atk":* 
-   *//攻击动作逻辑* 
-   *break;* 
- *}*

#### 2.Animator Controller动画控制器（状态机）

##### 知识点一 创建动画状态机
- 1.通过为场景中物体创建动画时自动创建 
- 2.手动创建动画状态机文件
- ![](static/Unity核心_images_81.png)
##### 知识点二 基础使用——初识动画状态机窗口
 ![](static/Unity核心_images_82.png)![](static/Unity核心_images_83.png))


##### 知识点三 基础使用——添加动画
- 自动添加——为对象创建动画后会自动将动画添加到状态机中 
- 手动添加1——将动画文件拖入到状态机中（注意：老动画拖入会有警告） 
- 手动添加2——右键创建状态，再关联动画
-![](static/Unity核心_images_84.png)

##### 知识点四 基础使用——添加切换连线
![](static/Unity核心_images_85.png)
##### 知识点五 基础使用——添加切换条件
- 在左侧面板点击参数页签 
- 可以在这里添加4中类型的切换条件
 ![](static/Unity核心_images_86.png)
##### 知识点六 基础使用——设置动画间切换条件

![](static/Unity核心_images_86.png)![](static/Unity核心_images_87.png)![](static/Unity核心_images_88.png)
````ad-tip

trigger在切换成功之后会自动变成不激活状态

所以一般用在有返回连线的情况下

````

#### 3.代码控制动画状态机切换

##### 知识点一 关键组件Animator

![](static/Unity核心_images_89.png)
##### 知识点二 Animator中的API
- 我们用代码控制状态机切换主要使用的就是Animator提供给我们的API 
- 我们知道一共有四种切换条件 int float bool trigger//所以对应的API也是和这四种类型有关系的 
- *private Animator animator;*
- *animator = this.GetComponent\<Animator>();*
-  1.通过状态机条件切换动画 
- *animator.SetFloat("条件名", 1.2f);* 
- *animator.SetInteger("条件名", 5);* 
- *animator.SetBool("条件名", true);* 
- *animator.SetTrigger("条件名");* 
  
- *animator.GetFloat("条件名");* 
- *animator.GetInteger("条件名");* 
- *animator.GetBool("条件名");* 
  ![](static/Unity核心_images_90.png)



![](static/Unity核心_images_91.png)
````ad-tip
如果不取消勾选 会延迟到动画结束才切换状态
````
- 2.直接切换动画 除非特殊情况 不然一般不使用 
- *animator.Play("状态名");*


## 五、2D动画

### ①.序列帧动画

#### 2D序列帧动画

##### 知识点一 什么是序列帧动画
- 我们最常见的序列帧动画就是我们看的 日本动画片 
- 以固定时间间隔 按序列切换图片 就是 序列帧动画的本质 
- 当固定时间间隔足够短时 我们肉眼就会认为图片是连续动态的 进而形成动画（会动的画面） 
  
- 它的本质和游戏的帧率概念有点类似 
  
- 原理就是在一个循环中按一定时间间隔不停的切换显示的图片

##### 知识点二 代码制作序列帧动画
```C# 
public Sprite[] sprs;  
  
private SpriteRenderer sr;  
private float time = 0;  
private int nowIndex = 0;


sr = this.GetComponent<SpriteRenderer>();  
sr.sprite = sprs[nowIndex];

//每一次增加帧间隔时间  
time += Time.deltaTime;  
//当帧间隔时间达到某一个条件时 就切换图片  
if( time >= 0.03f )  
{  
    //索引增加 切换图片  
    nowIndex++;  
    //如果显示到最后一张了 从头显示  
    if (nowIndex >= sprs.Length)  
        nowIndex = 0;  
    sr.sprite = sprs[nowIndex];  
    time = 0;  
}  
  

```

##### 知识点三 Animation窗口制作序列帧动画
- 方法一： 
- 1.创建一个空物体 
- 2.创建一个动画 
- 3.直接将某一个动作的序列帧拖入窗口中 

![](static/Unity核心_images_91.png)
- 方法二： 
- 直接将图片拖入Hierarchy层级窗口中 
- 注意：需要修改动画帧率 来控制动画的播放速度

![](static/Unity核心_images_92.png)
![](static/Unity核心_images_93.png)
![](static/Unity核心_images_76![](static/Unity核心_images_77.png)6.png)
##### 知识点四 利用Animator进行动画控制
```C#
  
if (Input.GetKeyDown(KeyCode.Space))  
    animator.SetBool("isDown", true);  
else if (Input.GetKeyUp(KeyCode.Space))  
    animator.SetBool("isDown", false);
    
```
![](static/Unity核心_images_94.png)

### ②. 骨骼动画——2D Animation
#### 1..单张图片骨骼编辑

##### 知识点一 什么是2D骨骼动画

- 首先回顾一下序列帧动画 
- 传统的序列帧动画为了达到好的动画效果 
- 理论上来说，图片越多，动作越流畅 
- 往往需要较多的美术资源，虽然效果好但是资源占用较多 
- 而2D骨骼动画是利用3D骨骼动画的制作原理进行制作的 
- 将一张2D图片分割成n个部位，为每个部位绑上骨骼，控制骨骼旋转移动 
- 达到用最少的2D美术资源做出流畅的2D动画效果


##### 知识点二 Unity中如何制作2D骨骼动画
- 主要方式有两种 
- 1.使用Unity2018新加功能 2D Animation 工具制作 
- 2.使用跨平台骨骼动画制作工具 Spine 制作


##### 知识点三 导入2D Animation工具
- 在Package Manager窗口 搜索 2D Animation并![](static/Unity核心_images_95.png)ng)

##### 知识点四 面板讲解
- 导入工具后 在Sprite Editor窗口会多一个选项 Skinning Editor
- ![](static/Unity核心_images_96.png)
![](static/tmp1762328995912_Unity核心_images_43.png![](static/tmp1762328996046_Unity核心_images_44.png)g)
![](static/Unity核心_images_97.png)

![](static/Unity核心_images_97.png)







##### 知识点五 骨骼动画使用

````ad-tip

1.添加SpriteSkin脚本

2.点击Create Bones按钮 来添加图片上的骨骼信息

3.添加Animation动画，在合适的关键帧位置更改骨骼位置来制作动画

 
````

#### 2.图集图片骨骼编辑

##### 知识点一 注意事项
- 1.设置Sprite为图集模式 
- 2.对图集图片进行切片

##### 知识点二 图集骨骼编辑
````ad-tip

进入sprite editor 模式

选择skinning editor

对图集中不同图片进行骨骼绑定 蒙皮 和权重设置

全部完成后 点开图集 可以看到图集中存在的不同部分的图片

在Hierachy窗口新建空物体用来充当父对象

为不同图片设定不同层级 来确保图像位置层级正确拼凑 

本方法中 因为是图集的原因 各个图片是独立的 骨骼的父子关系没有一开始就确定

如果要明确骨骼的层级关系 需要在Hierachy窗口中 为每张独立图片点击create bones 创建之前制作的骨骼并将需要成为子层级的图片放在父层级的子层级的骨骼下作为子层级

如果将子层级的图片直接放在父层级下 无法达成需要的效果

````

##### 知识点三 图集骨骼动画使用

````ad-tip

同单张图片骨骼编辑 需要在animation窗口中制作动画

````

#### 3. psb图片骨骼编辑

##### 知识点一 认识PSB文件

- 认识PSB之前先认识PS 
- PS（photoshop）是一款强大的图像处理软件 
- 在各领域都被广泛使用 
- 在游戏行业中也是美术同学使用最多的图像处理软件之一 
  
- PSD和PSB两种格式，都是PS这款软件用于保存图像处理数据的文件格式 
  
- PSD和PSB两种格式并没有太大的区别 
- 最大的区别是PSD格式兼容除PS以外的其它一些软件 
- 而PSB只能用PS打开 
  
- 在Unity中官方建议使用psb格式

##### 知识点二 在Unity中使用PSB文件

- 需要在Packages Manager窗口中引入 2D PSD Importer工具包

##### 知识点三 设置PSB文件关键参数

![](static/tmp1762344430262_Unity核心_images_73.png)
![](static/tmp1762341158893_Unity核心_images_68.png)
##### 知识点四 为PSB文件编辑骨骼信息
![](static/tmp1762341158893_Unity核心_images_68.png)
![](static/Unity核心_images_98.png)
 ````ad-tip
 
多出来的 sprite sheet用来切换 图集 和拼好的图

自动生成的蒙皮同时生成权重情况下 会生成不必要的骨骼关系 

可以通过权重里的Bone influence来删除不必要的骨骼之间的关系

````
##### 知识点五 为PSB文件制作骨骼动画
````ad-tip

与图集不同 在新建的空对象下 拖入制作完成的PSD图像 会自动的生成对应的骨骼

不需要额外的手动生成

本事例中存在额外的物体权杖  在空物体下拖入制作完成的PSD图像是作为一个预制体 不能直接性的改变权杖位置

此时可以右键所有图像的父对象的空物体 选择Unpack Prefab 来破坏预设体 之后再改动图像

````

#### 4.反向动力学IK

##### 知识点一 什么是IK？

- 在骨骼动画中，构建骨骼的方法被称为正向动力学 
- 它的表现形式是，子骨骼（关节）的位置根据父骨骼（关节）的旋转而改变 
- 用我们人体举例子 
- 当我们抬起手臂时，是肩部关节带动的整个手臂的运动，用父子骨骼理解的话就是父带动了子 
  
- 而IK全称是Inverse Kinematics，翻译过来的意思就是反向动力学的意思 
- 它和正向动力学恰恰相反 
- 它的表现形式是，子骨骼（关节）末端的位置改变会带动自己以及自己的父骨骼（关节）旋转 
- 用我们人体举例子 
- 当我们拿起一个杯子的时候是用手掌去拿，以杯子为参照物，我们移动杯子的位置，手臂会随着杯子一起移动 
- 用父子骨骼理解的话就是子带动了父

##### 知识点二 2D IK包引入

- 在Package Manager窗口中引入2D IK工具包 
- 需要在Advanced高级选项中选中Show preview packages（显示预览包） 
- 这样才能看到2D IK相关内容 
  
- 注意：如果在引入包时报错，需要在Windows防火墙中添加入站规则

##### 知识点三 2D IK的使用

![](static/Unity核心_images_99.png)

````ad-tip

操作流程：

1.在父对象上添加IK Manager 2D组件

2.在模型的各个组成部分的骨骼末端上创建空对象（移动空对象到骨骼末端） 

3.在父对象的IK Manager 2D 组件上添加IK解算器

4.关联刚刚创建的空对象到解算器上并进行相应设置

三种不同的结算 第一种不能反向  第二种能反向 能360°转 第三种只能影响三个关节点

````
![](static/tmp1762340013990_Unity核心_images_70.png)
![](static/tmp1762346778203_Unity核心_images_93.png)
![](static/Unity核心_images_100.png)
![](static/tmp1762346103617_Unity核心_images_87.png)
![](static/Unity核心_images_101.png)



##### 知识点四 IK对于我们的意义 

- 1.瞄准功能 
- 2.头部朝向功能 
- 3.拾取物品功能 
- 等等有指向性的功能时 我们都可以通过IK来达到目的 
  
- 最大的作用，可以方便我们进行动画制作

#### 5.换装——在同一文件中的换装资源

##### 知识点一 如何在同一个psb文件中制作换装资源

- 1.在ps中制作美术资源时，将一个游戏对象的所有换装资源都摆放好位置 
- 2.当我们导入该资源时，要注意是否导入隐藏的图层

##### 知识点二 编辑换装资源的骨骼信息以及分组类别

- 注意事项： 
- 每个部位 关联的骨骼要明确设置 
- 为同一个部位的不同装备分组

##### 知识点三 如何换装

- 两个关键组件 
- SpriteLibrary——精灵资料库，确定类别分组信息 
- SpriteResolver——精灵解算器，用于确定部位类别和使用的图片 
- 一个数据文件 
- SpriteLibraryAsset——精灵资料库资源，具体记录类别分组信息的文件

##### 知识点四 代码换装

- 1.获取各部位的SpriteResolver（需要引用命名空间）  
- 2.使用SpriteResolver的API进行装备切换  
- GetCategory() 获取当前部位默认的类别名  
- SetCategoryAndLabel 设置当前部位想要切换的图片信息  
- *sr.SetCategoryAndLabel(sr.GetCategory(), "CASK 1");*
-![](static/Unity核心_images_101.png)

#### 6.换装——在不同文件中的换装

##### 知识点一 如何在不同psb文件中制作换装资源

- 1.保证个部位在PS文件中的统一 
- 2.基础部位可选择性隐藏

##### 知识点二 编辑换装资源的骨骼信息

````ad-warning

注意事项：  

不同文件的骨骼信息必须统一,所以我们直接使用复制的方式

````

##### 知识点三 手动添加关键组件和数据文件

- 1.首先创建SpriteLibraryAsset数据文件 
- 2.为跟对象添加SpriteLibrary并关联数据文件 
- 3.为换装部位关联SpriteResolver

````ad-tip
新版unity中的SpriteLibraryAsset需要自己配置图片类型和标签
````
![](static/Unity核心_images_101.png)
![](static/Unity核心_images_101.png)
![](static/Unity核心_images_101.png)
![](static/Unity核心_images_101.png)


##### 总结: 如何选择 同一文件和 不同文件 制作换装资源两种方案 

- 换装较少的游戏 比如只有面部表情更换 可以使用同一psb文件方案  
- 换装较多的游戏 比如各部位有n种装备 可以使用不同psb文件方案  
- 不同psb文件 拓展性更强


### ③.骨骼动画——Spine

#### 1.Spine——运行库导入

##### 知识点一 Spine是什么？

- Spine是一个收费的跨平台的2D骨骼动画制作工具 
- 它支持Unity，UE，Cocos2D，Cocos2D-x等等游戏引擎 
- 相对Unity2018才推出的 2D Animation 
- Spine是目前商业游戏中较为常用的骨骼动画制作方案 稳定且高效 
- 官方地址：http://zh.esotericsoftware.com/

##### 知识点二 如何学习Spine

- 制作骨骼动画时美术人员的工作 
- 除非你是要做独立游戏，美术程序一人包 
- 那么我们没有必要去学习如何通过Spine制作骨骼动画 
- 我们只需要学习如何在Unity中通过程序使用Spine制作的资源 
- 如果想要学习如何制作Spine骨骼动画，可以根据官网提供的教学内容进行学习

##### 知识点三 导入Unity使用的Spine运行库

- 有了Spine提供的支持Unity开发的运行库  
- 我们才能在Unity中使用Spine制作的骨骼动画  
- 你可以简单理解其实就是官方写好的识别文件处理文件呈现效果的代码  
- 我们只需要学习如何使用它提供的API即可
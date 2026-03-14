![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260306192318868.png)



## 添加新世界须知
````ad-danger
###### 务必在WorldManager的枚举中添加新字段 
###### 并且GetBehaviourExecution方法里必须添加新if分支来保证CurWorldEnum正确改变 
###### 如果对脚本创建优先级有特殊需求 返回值可以为Null
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260304220049636.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260304220458958.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260304220720776.png)


# 打包策略

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310134121451.png)

## 核心组件

````ad-tip
资源加载管理类
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260312100759016.png)

````ad-tip
ZMAsset 走AB包加载资源的API
````
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260312101135257.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260312100911259.png)

````ad-tip
原始数据 （如果想要UI对象在放进对象池后 在被再次调用后 能返回原始预制体状态（即使子节点被改变了））的情况下使用
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260312162704295.png)




## 一、创建无限滚动窗口

- 得生成item脚本 然后手动继承IZMUIViewlistItem接口
- windowdatacomponent脚本也得生成 用来关联自定义类ZMUIListView
- window脚本里的生命周期也得声明刷新逻辑和关联脚本对象
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260301145220718.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260301144959802.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260301145129205.png)


![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260301145333169.png)

## 二、刘海屏
- 上面一个脚本是刘海屏脚本  底下一个是IOS特有的触摸条
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260301194835969.png)

## 三、3D粒子特效遮挡/粒子遮罩

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302094145773.png)
````ad-tip
在特效粒子上方层级的根物体添加UI Particle脚本 就可以让特效正确参与UI渲染层级 可被后渲染的UI元素遮挡
````


````ad-tip
想要粒子跟随界面分辨率和缩放自适应变化大小，需要在特效根节点挂上ParticleScaler
````
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302102239815.png)



````ad-tip
想要3D粒子被正确裁剪 需要自定义特效渲染材质 将其shader改成自定义shader

shader裁剪的主要参数在于_MinX _MaxX _MinY _MaxY四个参数

i.vps.x/y必须在四个参数构成的矩形内 不然超出部分 最下面的表达式里条件判断就会变成false，导致不渲染 
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302100628696.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302100335645.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302100148434.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302100110220.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260302095339439.png)

## 四、AppDomain

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260303141736272.png)

## Set设置为私有
````ad-warning
这里把set设置为私有 并通过内部方法更改值 是为了之后查BUG只需要查方法的调用 就能定位错误 

不然万一调用多起来 出现报错 得一个个查数据的调用 还要查数据是否更改 效率极低 
````
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260305225302656.png)

## 逻辑如果耦合 可能产生的问题
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260306114718898.png)

## 如果确定使用AB包加载 

````ad-danger
就不能再用resource来读取 或者直接 destory（obj）了

后者会打乱框架内的引用计数 导致对象资源无法释放 因为此处释放资源需要销毁 所以额外传第二个参数true（默认为false）
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260306164246778.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260306165147563.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260306172512035.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260306172308086.png)


## 非热更模式下 

````ad-danger
非热更模式下 程序入口的awake里不能直接初始化资源管理框架

# 因为初始化资源管理框架的方法里 存在通过AB包读取数据的方法  需要在确定资源读取完毕后 才能调用初始化 以及构建大厅世界
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260307100354383.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260307100810279.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260307100448119.png)

## 游戏启动热更流程实现

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310115313194.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310115443860.png)

````ad-tip
由于UI框架的初始化 包含了调用AssetBundle，所以不能够在一开始就调用。需要等到资源热更结束（也可能不需要热更）并加载完资源 才能调用
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310115615812.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310115907591.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310121544194.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310141528797.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260310142709701.png)



























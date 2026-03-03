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





































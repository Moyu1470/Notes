![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314195451045.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314195511196.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314195518167.png)



## 刷新列表的API最好最后刷新下榜单数据 不然可能会出BUG

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314160007416.png)

## API相关
![](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314192254096.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314191925100.png)

### 1.InitParam
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314192254096.png)


![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314160321598.png)
### 2.SetListItemCount(list.Count,isReSetPos) 第一个参数为 榜单数据 第二个为是否重置到榜单顶部
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314192230715.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314183108122.png)


### 3.RefreshAllShowItem

````ad-tip
这个接口要是在RefreshListView末尾不调用 如果在拉取列表的情况下 数据有发生改动 OnGetItemIndex这个回调的调用会不正常（已显示的不更新） 导致数据错误

下图例子里 本身为100条数据 按Q 加50条 
````
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314192216393.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314170206946.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314165921738.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314165707125.png)

### 4.MovePanelToItemIndex 元素跳转接口
````ad-tip
第一个参数是 瞬移到的索引位置 

第二个参数是 瞬移到索引位置后的偏移量（即最终位置 = 瞬移索引的位置 + 偏移量）
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314171713436.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314183221770.png)


### 5.元素滚动接口SetSnapTargetItemIndex

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314192139592.png)

````ad-tip
这个接口 用于设置缓动跳转到位置 （不会像上个事例里直接跳转到接Index位置，更有动画感）

这里的XXX.Index = 50的50就是要跳转到的索引

loopListView.itemList[0].ItemIndex则是当前视口展示的第一个索引，这里的写法的意思即从当前视口位置缓动到索引为50处。

XXXX.CachedRectTransform.rect.height为预制体高度 

这个接口的第二个参数类型为float，用来控制缓动的速度 
````

````ad-danger
用这个方法的时候，RefreshListView 的参数一定要设置成 false 

否则每次添加新数据 都会将视口调整到榜首

导致缓动变成 无论在哪边添加数据 都会从榜首缓动到目标位置 
````
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314182808952.png)

### 6.回弹遮挡处理

````ad-tip
可以看到 榜首数据的ui被遮挡了一部分 这里的问题 可以通过 修改ScrollView上的脚本的ItemPadding参数为0-10来解决

也可以通过拉升克隆对象的（即第一条数据的）UI填充方式 并拉升 Y轴高度 来更改预制体UI填充背景的高 导致其不适配完整高度 留下空白 来模拟间隔
````
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314190640732.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314190751414.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314191016509.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314191035188.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314191040291.png)

### 7.动态修改Item高度

````ad-tip
这里得写else分支 控制数据更新时 非需要更改数据的情况 

否则可能会导致 某些复制的预制体 高度不正确（因为原理是修改了复制体的宽高 复制体进对象池 再调用时还保持改变的状态）

如果补充了其余的逻辑 就会在刷新的时候修改所有的预制体到正确的大小 

可以用这个方法 来设置特殊节点的宽高 以显示节点被隐藏的UI 较常用于显示特殊节点的奖励等
````

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314192402172.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314195126479.png)

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314200208817.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260314200224110.png)






















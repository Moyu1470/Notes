# 核心组件

## 1.反馈器（MMF_Feedback）
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326131018825.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326131032934.png)

### 主要涉及位移 旋转 放大等 

## 2.播放器（MMF_Player）
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326130943785.png)


### 该组件可以显示当前所有Feedbacksd的状态
## 3. 振动器（Shackers）

### 既可以控制游戏实体的表现 也能控制游戏内的 摄像头和视频监听器（Audio Listener）
#### 出于解耦考虑，Feel在镜头、音乐监听器上添加shaker来监听feedback抛出的广播 （Shaker就是特定Feedback的Listener）

## 4.信道（Channel）
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326130928241.png)


### 每个Shaker和除法Shaker的Feedback都有一个信道参数，用来控制Feedback触发哪个匹配的Shaker

## 5.暂停器（Pauses）

### 默认情况下的pause会和其他FeedBack一起被激活 而之后的Feedback在Pause执行后再执行
#### 相当于为Pause之后的FeedBack统一增加一个延迟时间
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326131602980.png)

### 另一种HoldingPause则是等前面的所有操作完成之后才会执行
#### 相当于等待之前所有Feedback完成，再等待Holding Pause 的Pause Duration之后才继续执行

![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326131609902.png)

## 6.循环（Loops）

### 如果想要循环一系列的Feedback操作，就要使用Looper操作


![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326132006262.png)


![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205125833.png)


![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205127794.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205144538.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205153684.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205215516.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205230773.png)
![image.png](https://cdn.jsdelivr.net/gh/Moyu1470/Notes/img/20260326205255844.png)

































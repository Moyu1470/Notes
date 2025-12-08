## 一、视频格式和解码器

![](static/Unity进阶之视频播放_images_1.png)
![](static/Unity进阶之视频播放_images_2.png)
![](static/Unity进阶之视频播放_images_3.png)
![](static/Unity进阶之视频播放_images_4.png)
![](static/Unity进阶之视频播放_images_5.png)
![](static/Unity进阶之视频播放_images_6.png)
![](static/Unity进阶之视频播放_images_7.png)
![](static/Unity进阶之视频播放_images_8.png)
![](static/Unity进阶之视频播放_images_9.png)
![](static/Unity进阶之视频播放_images_10.png)
![](static/Unity进阶之视频播放_images_11.png)

## 二、Unity中的视频兼容性

#### Unity中的视频兼容性

![](static/Unity进阶之视频播放_images_12.png)
![](static/Unity进阶之视频播放_images_13.png)
![](static/Unity进阶之视频播放_images_14.png)
![](static/Unity进阶之视频播放_images_15.png)
![](static/Unity进阶之视频播放_images_16.png)
![](static/Unity进阶之视频播放_images_17.png)
![](static/Unity进阶之视频播放_images_18.png)
![](static/Unity进阶之视频播放_images_19.png)
![](static/Unity进阶之视频播放_images_20.png)
![](static/Unity进阶之视频播放_images_21.png)
![](static/Unity进阶之视频播放_images_22.png)
![](static/Unity进阶之视频播放_images_23.png)
![](static/Unity进阶之视频播放_images_24.png)
![](static/Unity进阶之视频播放_images_25.png)
![](static/Unity进阶之视频播放_images_26.png)

## 三、视频剪辑设置相关

#### 视频剪辑设置相关

##### 知识点一 为什么要对视频剪辑进行设置？
- 当我们将准备好的视频导入Unity后 
- 我们可以选中该视频剪辑，并在Inspector窗口中进行设置 
- 设置视频剪辑的主要原因 
- 1.预览视频效果 
- 2.查看视频文件的基本信息 
- 3.设置视频剪辑是否开启转码设置（重要） 
  
- 通过对视频剪辑进行转码相关设置 
- 我们可以保证在各平台都能正常播放

##### 知识点二 视频剪辑设置参数相关

![](static/Unity进阶之视频播放_images_27.png)
![](static/Unity进阶之视频播放_images_28.png)

##### 总结 

- 视频剪辑相关设置的主要目的 
- 是为了设置视频转码相关方案 
- 通过视频转码，可以让视频尽量支持各平台 
  
- 关于各平台的转码规则 我们在上节课中就已经讲过 
- 1.可用于硬件加速并且本机支持的最优视频编解码器是 H.264 
- 2.当优先考虑跨平台支持时，VP8 是一个不错的选择。 
-   VP8 得到广泛支持并具有全面的功能集，但与硬件加速的编解码器（例如 H.264）相比，需要消耗更多的资源。 
- 3.在支持 H.265 的设备上可以使用 H.265。 
- 4.Android 使用原生库支持 VP8，因此 VP8 在某些 Android 设备上也可能获得硬件辅助。 
  
- 一劳永逸 mp4格式 + H.264编解码器 
- 根据设备情况考虑使用 VP8 和 H.265 编解码器

## 四、Video Player 视屏播放器

#### Video Player 视屏播放器

##### 知识点一 Video Player是什么 

- Video Player顾名思义是视频播放器的意思 
- 它是Unity提供给我们用于播放视频的组件 
- 该视频播放器组件 
- 可以在游戏中播放导入的视频剪辑文件

##### 知识点二 添加Video Player组件 

- 方法一：在Hierarchy窗口点击加号，选择Video > Video Player 
- 方法二：选择场景上任何一个对象，为其添加Video Player组件 
- 方法三：直接将视频文件拖入到Hierarchy窗口中

##### 知识点三 Video Player参数相关

![](static/Unity进阶之视频播放_images_29.png)
![](static/Unity进阶之视频播放_images_30.png)

##### 知识点四 Video Player代码相关

- 注意：使用VideoPlayer组件需要引用命名空间UnityEngine.Video 
  
- 1.将一个 VideoPlayer 附加到主摄像机。 
-   将 VideoPlayer 添加到摄像机对象时， 
-   它会自动瞄准摄像机背板，无需更改 videoPlayer.targetCamera。 
- GameObject camera = GameObject.Find("Main Camera"); 
- videoPlayer = camera.AddComponent\<VideoPlayer>(); 
  
- 2.参数相关设置 
-   是否自动播放 
- videoPlayer.playOnAwake = false; 
-   渲染模式 
- videoPlayer.renderMode = VideoRenderMode.CameraFarPlane; 
- 设置目标 渲染贴图 
- videoPlayer.targetTexture = texture; 
- 设置目标摄像机 
- videoPlayer.targetCamera 
  
-   透明度 
- videoPlayer.targetCameraAlpha = 0.5f; 
- videoPlayer.targetCamera3DLayout = Video3DLayout.OverUnder3D; 
  
-   视频源 
- videoPlayer.source = VideoSource.VideoClip; 
- videoPlayer.clip = clip; 
  
- videoPlayer.source = VideoSource.Url; 
- videoPlayer.url = Application.streamingAssetsPath + "/Video.mp4"; 
  
-   是否循环 
- videoPlayer.isLooping = false; 
  
-   视频总时长 
- print(videoPlayer.length);- 单位为s 
-   当前时长,播放了多久 
- print(videoPlayer.time);- 单位为s 
  
-   总帧数  
- print(videoPlayer.frameCount); 
-   当前帧  
- print(videoPlayer.frame); 
  
  
- 3.方法相关 
-   播放、停止、暂停 
  
-   准备函数 
- videoPlayer.Prepare(); 
  
- 4.事件相关 
-   准备完成事件 
videoPlayer.prepareCompleted += (v) => 
- { 
-     print("准备完成"); 
-     isOver = true; 
- }; 
  
-   开始事件 
videoPlayer.started += (v) => 
- { 
-     print("当执行player播放方法后 会调用的事件");  
- }; 
  
-   结尾时调用事件 
videoPlayer.loopPointReached += (v) => 
- { 
-     print("视频播放到结尾处时会调用的事件"); 
- };
![](static/Unity进阶之视频播放_images_31.png)
##### 总结 

- VideoPlayer是用于视频播放的组件 
- 我们可以通过它来控制视频播放相关设置 
  
- 其中比较重要的参数有 
- 1.渲染模式 
- 2.播放暂停相关API 
  
- 视频播放时，需要有短暂的准备时间才会开始播放 
- 我们可以通过Prepare函数来启动准备，准备完毕后再正式开始播放

##### 练习题

![](static/Unity进阶之视频播放_images_32.png)

## 五、全景视频

#### 全景视频

##### 知识点一 Unity支持的全景视频 

- 1.等距圆柱投影布局(也称为球面投影、简化圆柱投影、矩形投影或普通圆柱投影) 
-   的全景视频(视频宽高比为 2:1的360度内容 或 1:1的180度内容) 
  
- 2.立方体贴图布局(六个正方形纹理的集合) 
-   的的全景视频(视频宽高比为1:6、3:4、4:3、6:1) 
  
- 我们可以通过视频分辨率的比值判断该全景视频 为哪一种

##### 知识点二 在Unity中使用全景视频 

- 1.导入等距圆柱投影布局的视频文件 
- 2.用Video Player以Render Texture渲染纹理播放视频 
- 3.设置接受渲染纹理的天空盒材质,天空盒材质的着色器使用 Skybox>Panoramic 
- 4.设置场景以使用天空盒材质 
  
- 注意：尽量使用较高分辨率率的全景视频（4K或8K）,这样效果更好 
- 但是对于一些老设备或者移动设备可能最多只能使用2K分辨率，具体根据实际情况而定

##### 知识点三 使用全景视频时的注意事项 

- 1.Render Texture渲染纹理的Size和视频尺寸一样，可以在视频预览窗口选择Source Info查看分辨率 
- 2.将渲染纹理的Depth Buffer设置为No depth buffer 
- 3.天空盒材质中 
-   3-1等距圆柱投影布局，将Mapping设置为Latitude Longitude Layout 
-      根据视频时180视图还是360视图选择 360 degree或者180 degree 
-   3-2立方体贴图，将Mapping设置为6 Frames Layout 
- 4.如果视频时VR视频 
-   分为了左右双眼，我们需要将天空盒材质的3D Layout设置为Side by Side 
-   如果左右侧内容在视频中上下分部，3D Layout设置为Over Under

##### 总结 

- 全景视频一般在VR项目中才会使用 
- 我们也可以使用全景视频再游戏中来制作一些动态天空盒效果








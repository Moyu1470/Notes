# GUI

## 文本和控件按钮
### 一、GUI控件绘制的共同点
1. 都是GUI公共类中提供的**静态函数**，**直接调用**即可
2. 他们的**参数**都大同小异
    **位置**参数： Rect参数 x y位置 w h 尺寸
    显示**文本**： String参数
    **图片**信息： Texture参数
    **综合**信息： GUIContent
    **自定义**样式： GUIStyle

### 二、 文本控件
//基本使用
```c#
//基本使用
GUI.Label(new Rect (0,0,100,20),"xxxxxx");   //位置+文本信息
GUI.Label(rect,tex);                         //位置+图片    需public申明
//综合使用
GUI.Label(rect1,content);                    //位置+综合信息（文本、图片、）
//可以获取当前鼠标或者键盘选中的GUI控件 对应的tooltip
Debug.Log(GUI.tooptip);
//自定义样式
```

### 三、按钮控件
//基本使用
//综合使用
//自定义样式
```C#
if(GUI.Button(btnRect.btnContent,btnStyle))
{
//处理点击按钮的逻辑   必须在按钮范围内 按下并抬起  才算一次点击
Debug.Log(按钮被点击);
}

//只要在长按按钮范围内 按下鼠标 就会一直返回true
if（GUI.RepeatButton(GUI.Button(btnRect.btnContent)）
{
Debug.Log("长按按钮被点击);
}
```
## 多选框和单选框
### 一、多选框

```c#
private bool isSel;    //私有申明一个siSel标志符 而不是直接写死bool值
private bool isSel2;   //若不申明 GUI状态每帧更新 点击后bool值会变但 下一帧会立马变回申明状态

//普通样式
isSel =  GUI.Toggle(new Rect(0,0,100,30),isSel,"效果开关")

//自定义样式
//修改固定宽高 fixedWidth和fixedHeight (如果直接改width 和 height 响应区域也会跟着改变)
//修改从GUIStyle边缘到内容起始处的空间 padding 
isSel2 = GUI.Toggle(new Rect(0,0,100,30),isSel,"音效开关"，style)
```

### 二、单选框
```C# 
private int nowSelIndex = 1;


//单选框的实现  基于多选框
//关键： 通过一个Int标识用来决定是否选中
if(GUI.Toggle(new Rect(0,100,100,30),true,"选项一"))
{
nowSelIndex = 1;
}

if(GUI.Toggle(new Rect(0,140,100,30),true,"选项二"))
{
nowSelIndex = 2;
}

if(GUI.Toggle(new Rect(0,180,100,30),true,"选项三"))
{
nowSelIndex = 3;
}
```

## 输入框和拖动条

### 一、 输入框 
```C#
private string inputStr="";
private string inputPW ="";

//普通输入    //此处若不写inputStr=  则会每帧更新 临时输入的内容会变成初内容 
            //此处实际效果为  每帧将当前输入的内容返回给输入框用于对其赋值
inputStr = GUI.TextField(new Rect(0,0,100,30),inputStr)

//密码输入
inputPW = GUI.PasswordField(new Rect(0,50,100,30),inputPW,'*')
```

### 二、拖动条

#### 水平拖动条
``` C#
private float nowValue = 0.5f;

//当前值
//最小值 left
//最大值 right
nowValue = GUI.HorizontalSlider(new Rect)(0,100,100,50),nowValue，0,1)
```

#### 竖直拖动条
```C#

nowValue = GUI.verticalSlider(new Rect)(0,150,50,100),nowValue，0,1)

```

## 图片绘制和框

### 一、 图片绘制
```C#
public Rect     texPos;
public Texture  tex;


//ScaleMode
//ScaleAndCrop:通过宽高比来计算图片 但是会进行裁剪
//ScaleToFit:自动根据宽高比进行计算 不会拉变形 会一直保持图片完全显示的状态
//StretchToFill:始终填充满你传入的Rect范围

//alpha 是用来 控制 图片是否开启透明通道的

//imageAspect 自定义宽高比 如果不填 默认为0 就会使用 图片原始宽高

GUI.DrawTexture(texPcs,tex,mode,alpha,wh)

```

### 二、框绘制

```C#
public Rect texPos;

public Texture BoxTexure

GUI.Box(texPos," ") //简单文本显示框

GUI.Box(texPos,BoxTexure)//显示带纹理的框

GUI.Box(texPos,"自定义样式",style)//自定义框的外观
```

## 工具栏和选择网格

### 一、工具栏 

```C#
private int toolbarIndex = 0;
private string[] toolbarInfos = new string[]{"选项一"，"选项二"，"选项三"};

toolbarIndex = GUI.Toolbar(new Rect(0,0,300,30), toolbarIndex,toolbarInfos)
//工具栏可以帮助我们根据不同的返回索引 来处理不同的逻辑

switch(toolbarIndex)
{
case 0 :
    break;
case 1 :
    break;
case 2 :
    break;
}
```

### 二、选择网格

```C#
private int selGridIndex = 0;
private string[] toolbarInfos = new string[]{"选项一"，"选项二"，"选项三"};

//相对toolbar多了一个参数 xCount 代表 水平方向最多显示的按钮数量
GUI.SelectionGrid(new Rect(0,50,200,30),selGridIndex,toolbarInfos，3)
```

## 滚动列表和分组

### 一、分组

```C#
//用于批量控制组件位置
//可以理解为 包裹着的控件加了一个父对象
//可以通过控制分组来控制包裹控件的位置
public Rect groupPos;


GUI.BeginGroup(groups);
GUI.Button(new Rect(0,0,100,50),"测试按钮")
GUI.EndGroup();



```

### 滚动列表

``` C#
public  Rect  scPos;
public  Rect  showPos;
private Vector2  nowPos;

public static Vector2 BeginScrollView(Rect position, Vector2 scrollPosition, Rect viewRect, bool alwaysShowHorizontal, bool alwaysShowVertical, GUIStyle horizontalScrollbar, GUIStyle verticalScrollbar);

//position : 屏幕上用于滚动视图的矩形区域。
 
//scrollPosition: 视图在 X 和 Y 方向上滚动的像素距离。   
//viewRect: 在滚动视图内使用的矩形区域。  
//horizontalScrollbar 和 verticalScrollbar: （可选）用于水平和垂直滚动条的 GUIStyle。如果省略，则使用当前 GUISkin 的样式。 
//alwaysShowHorizontal 和 alwaysShowVertical: （可选）指示是否始终显示水平和垂直滚动条。


nowPos = GUI.BeginScrollView(scPsos,nowPos,showPos)


GUI.EndScrollView();
```
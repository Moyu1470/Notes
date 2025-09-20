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

GUI.DrawTexture(texPcs,tex)

```



# 滑动条 (Slider)

> 参考 [滑动条 (Slider)](https://docs.unity3d.com/cn/2023.2/Manual/script-Slider.html) 官方文档。
>
> 前置知识： [可选基类 ／交互基类 (Selectable Base Class)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html) 内容。

​`滑动条` 控件允许用户通过拖动鼠标从预定范围中选择数值。常见的应用场景包括游戏中的难度设置、音量调节和图像编辑器中的亮度设置等。

### 图示

![滑动条示例](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_SliderExample.png)  
​![滑动条检视面板](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_SliderInspector.png)

‍

### 核心参数

[可选基类 ／交互基类 (Selectable Base Class)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html)

- 包含 `Interactable`​, `Transition`​, `Navigation` 等交互属性，详情请参考前置知识。

#### **Fill Rect**

​`填充区域` - 用于显示滑动条当前值填充区域的图形对象。

#### **Handle Rect**

​`控制柄` - 用于用户拖动以改变滑动条值的图形对象。

#### **Direction**

​`方向` - 定义拖动控制柄时，滑动条的值增加的方向。

- ​`Left To Right`: 从左到右，值递增。
- ​`Right To Left`: 从右到左，值递增。
- ​`Bottom To Top`: 从下到上，值递增。
- ​`Top To Bottom`: 从上到下，值递增。

#### **Min Value**

​`最小值` - 当控制柄处于起始位置时，滑动条所代表的最小值。

#### **Max Value**

​`最大值` - 当控制柄处于终点位置时，滑动条所代表的最大值。

#### **Value**

​`当前值` - 滑动条当前所代表的数值。此值会在运行时根据用户操作而改变，也可以在代码中设置。

‍

### 可配参数

#### **Whole Numbers**

​`整数值`​ - 勾选后，滑动条的值将被约束为整数。即使启用此选项，`On Value Changed`​ 事件传递的参数仍然是 `float` 类型。

‍

---

### 事件

#### **On Value Changed**

​`值变化事件`​ - 这是一个 [UnityEvent](https://docs.unity3d.com/cn/2023.2/Manual/UnityEvents.html)，当滑动条的 `Value` 发生改变时被调用。

- 该事件可以动态传递一个 `float` 类型的参数，即滑动条的当前值。这使得我们可以方便地将滑动条的值与游戏逻辑或其它UI元素的状态进行绑定。

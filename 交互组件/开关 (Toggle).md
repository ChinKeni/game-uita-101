# 开关 (Toggle)

> 参考 [开关 (Toggle)](https://docs.unity3d.com/cn/2023.2/Manual/script-Toggle.html) 、[开关组 (Toggle Group)](https://docs.unity3d.com/cn/2023.2/Manual/script-ToggleGroup.html) 官方文档。
>
> 前置知识： [可选基类 ／交互基类 (Selectable Base Class)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html) 内容。

​`开关 (Toggle)`​ 控件是一个允许用户打开或关闭某个选项的复选框。当多个 `Toggle`​ 被放入一个 `开关组 (Toggle Group)` 时，可以实现单选（Radio Button）效果。

### 图示

![开关组件示例](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_ToggleExample.png)  
​![开关检视面板](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_ToggleInspector.png)

‍

### 核心参数

[可选基类 ／交互基类 (Selectable Base Class)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html)

- ​**​`Interactable`​** - 组件是否接收交互。
- ​**​`Transition`​** - 控件响应用户操作的过渡效果（如颜色变化、精灵图切换等）。
- ​**​`Navigation`​** - 用于定义UI元素之间的导航顺序。

‍

#### **Is On**

​`初始状态` - 决定开关在程序开始时是否处于“开”状态。勾选此项，则默认为“开”。

#### **Graphic**

​`图形`​ - 用于表示“开”状态的 `Image`​ 组件，通常是一个对勾 ✔ 图标。当 `Is On`​ 为 `true`​ 时，此图形会根据 `Toggle Transition` 的设置显示出来。

#### **Group**

​`开关组`​ - 关联一个 `Toggle Group`​ 组件。将多个 `Toggle`​ 关联到同一个 `Group`​ 后，它们将表现为一组单选按钮，即同一时间内只有一个 `Toggle`​ 能被选中。如果此项为 `None`，则该开关为独立的复选框。

‍

### 可配参数

#### **Toggle Transition**

​`切换过渡效果`​ - 定义当开关状态改变时，其 `Graphic`（对勾图标）的显示方式。

- ​`None`​: 无过渡效果。`Graphic` 会在状态切换时立即出现或消失。
- ​`Fade`​: 淡入淡出。`Graphic` 会在状态切换时平滑地淡入或淡出，提供更柔和的视觉反馈。

‍

### 事件

#### **On Value Changed (Boolean)**

​`值变更事件`​ - 这是 `Toggle` 最核心的事件。当用户点击开关，使其状态发生改变时，此事件会被触发。

- 它会传递一个 `bool` 类型的动态参数给监听函数。
- 当开关变为“开”状态时，参数值为 `true`。
- 当开关变为“关”状态时，参数值为 `false`。

# 按钮 (Button)

> 参考 [按钮 (Button)](https://docs.unity3d.com/cn/2023.2/Manual/script-Button.html) 官方文档。
>
> 前置知识： [可交互基类 (Selectable)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html) 、 [过渡选项 (Transition Options)](https://docs.unity3d.com/cn/2023.2/Manual/script-SelectableTransition.html) 、 [导航选项 (Navigation Options)](https://docs.unity3d.com/cn/2023.2/Manual/script-SelectableNavigation.html) 、 [UnityEvent](https://docs.unity3d.com/cn/2023.2/Manual/UnityEvents.html)

​`按钮 (Button)` 控件可响应用户的点击，用于启动或确认操作。

### 图示

![按钮示例](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_ButtonExample.png)  
​![按钮检视面板](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_ButtonInspector.png)

‍

### 核心参数

#### **Interactable**

​`可交互` - 布尔值，用于控制按钮是否能接受用户的输入。

- 勾选时，按钮可以被正常点击。
- 取消勾选时，按钮会进入“禁用”状态，无法响应点击，并通常会通过 `Transition` 属性改变外观以示区别。

‍

#### **Transition**

​`过渡效果`​ - 定义按钮在不同交互状态（如高亮、按下、选中、禁用）下的视觉反馈方式。这是影响按钮外观和手感的重要参数。具体配置请参考 [过渡选项 (Transition Options)](https://docs.unity3d.com/cn/2023.2/Manual/script-SelectableTransition.html) 文档。

‍

#### **Navigation**

​`导航`​ - 用于设置在使用键盘或手柄时，UI 元素之间的导航顺序。对于需要支持非鼠标操作的游戏或应用非常重要。具体配置请参考 [导航选项 (Navigation Options)](https://docs.unity3d.com/cn/2023.2/Manual/script-SelectableNavigation.html) 文档。

‍

---

### 核心事件

#### **On Click ()**

​`点击事件`​ - 这是按钮组件最重要的部分。它是一个 [UnityEvent](https://docs.unity3d.com/cn/2023.2/Manual/UnityEvents.html)，允许你指定当用户点击并释放按钮时要执行的方法。

- 你可以在检视面板中拖拽游戏对象，并从其挂载的脚本中选择一个公共方法来响应点击事件。
- 典型的用例包括：

  - 确认决定（例如开始游戏、保存进度）。
  - 打开新的菜单或面板。
  - 取消一个操作（例如关闭窗口）。

‍

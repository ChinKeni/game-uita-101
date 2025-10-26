# 动画集成 (Animation Integration)

> 参考 [UI Animation Integration](https://docs.unity3d.com/cn/2023.2/Manual/UIAnimationIntegration.html) 官方文档。
>
> 前置知识：[可选基类 ／交互基类 (Selectable Base Class)](可选基类%20／交互基类%20(Selectable%20Base%20Class).md)

---

## 简介

​`动画集成`​ 是交互组件中最强大的过渡模式。通过该模式，可以利用 Unity 强大的动画系统 (`Animator`) 来完全控制控件在不同状态（如普通、高亮、按下等）之间的过渡效果。由于几乎所有属性都可以被动画化，因此可以实现非常复杂和高度自定义的视觉反馈。

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/GUI_ButtonInspectorAnimation.png)

‍

## 设置步骤

要使用 `动画 (Animation)`​ 过渡模式，UI 控件所在的游戏对象上必须附加一个 `Animator` 组件。

1. 在 `Selectable`​ 组件（如 `Button`​、`Toggle`​ 等）的 `Transition`​ 属性中选择 `Animation`。
2. 点击 `Auto Generate Animation` 按钮。
3. Unity 会自动为该对象添加一个 `Animator`​ 组件，并创建一个 `Animator Controller` 资源。你需要为这个新生成的控制器指定一个保存位置和文件名。

保存后，`Animator Controller`​ 会被自动设置好，包含 `Normal`​、`Highlighted`​、`Pressed`​、`Selected`​ 和 `Disabled` 等状态，可以直接使用。

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/GUI_ButtonAnimator.png)

通过共享同一个 `Animator Controller`，可以使多个UI控件拥有相同的动画行为。

‍

## 编辑动画

生成控制器后，就可以为每个状态编辑具体的动画效果。

1. 选中附加了 `Animator` 的UI控件游戏对象。
2. 打开动画窗口（菜单栏：`Window`​ > `Animation`​ > `Animation`）。
3. 在动画窗口中，可以看到一个动画剪辑的下拉菜单，其中包含了所有可编辑的状态。

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/GUI_ButtonAnimationWindow.png)

#### 可编辑的状态剪辑

- ​`Normal`：普通状态。该状态的属性值由控件本身在 Inspector 中的设置决定，此剪辑通常可以留空。
- ​`Highlighted`：高亮状态（例如鼠标悬停）。
- ​`Pressed`：按下状态。
- ​`Selected`：选中状态（在使用键盘或手柄导航时）。
- ​`Disabled`：禁用状态。

#### 编辑方法

通常，我们只需要在每个状态剪辑的第0帧（开头）设置一个关键帧，来定义该状态下的最终表现。状态之间的过渡动画将由 `Animator` 自动处理。

例如，要修改 `Highlighted` 状态下按钮的宽度：

1. 在动画窗口的下拉菜单中选择 `Highlighted` 剪辑。
2. 将时间轴播放头移动到 `0:00` 位置。
3. 点击红色的 `录制` 按钮进入录制模式。
4. 在 Inspector 中，修改 `Rect Transform`​ 的 `Width` 属性。
5. 再次点击 `录制` 按钮退出录制模式。

完成以上步骤后，进入播放模式，当鼠标悬停在按钮上时，其宽度就会平滑地过渡到你所设置的新值。通过这种方式，可以在一个关键帧中设置任意数量的属性。

‍

## 注意事项

- UI 的 `动画 (Animation)`​ 过渡模式与 Unity 的旧版 `Animation` 系统不兼容。
- 请务必使用 `Animator`​ 组件，而不是旧版的 `Animation` 组件。

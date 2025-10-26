# 动画(Animation)

> **注意：**  这是 **旧版** 动画 (`Animation`) 组件。在引入 Unity 的现代动画系统（Mecanim）之前，此组件被用于游戏对象的动画播放。
>
> 此组件仅为确保向后兼容而保留在 Unity 中。对于新项目，强烈建议使用功能更强大的 [Animator组件](https://docs.unity3d.com/cn/2023.2/Manual/class-Animator.html)。

> 参考：[Animation 窗口指南](https://docs.unity3d.com/cn/2023.2/Manual/AnimationEditorGuide.html) 、 [模型导入工作流程](https://docs.unity3d.com/cn/2023.2/Manual/ImportingModelFiles.html)。

## 图示

![动画检视面板 (Animation Inspector)](https://docs.unity3d.com/cn/2023.2/uploads/Main/AnimationInspector35.png)

## 核心参数

#### **Animation**

​`默认动画`​ - 指定一个默认的动画剪辑 (Animation Clip)。如果 `Play Automatically` 被勾选，游戏开始时将播放此动画。

#### **Animations**

​`动画列表`​ - 一个动画剪辑列表，包含了所有可以通过脚本控制和播放的动画。需要在这里添加动画剪辑后，才能在代码中通过名称来调用 `Play()` 等方法。

#### **Play Automatically**

​`自动播放`​ - 如果勾选此项，附加到游戏对象上的 `Animation`​ 组件将在游戏启动时自动播放 `Animation` 字段中设置的默认动画。

#### **Animate Physics**

​`物理动画`​ - 如果勾选此项，动画的更新将与物理引擎的更新循环（`FixedUpdate`）同步。这适用于需要与物理系统进行精确交互的动画，例如控制一个使用 Rigidbody 的角色。

#### **Culling Type**

​`剔除类型` - 用于确定当游戏对象在摄像机视野外时，动画应如何处理以优化性能。

- ​`Always Animate`：始终播放动画。无论对象是否可见，动画都会持续更新。这是默认选项，但性能开销最大。
- ​`Based on Renderers`：基于渲染器剔除。当附加到此游戏对象或其子对象上的所有渲染器（Renderer）都位于摄像机视野之外时，动画将停止播放，直到对象再次可见。这是推荐的性能优化选项。

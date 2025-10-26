# 状态机(Animator)

> 参考 [Animator Controller](https://docs.unity3d.com/cn/2023.2/Manual/class-AnimatorController.html)、[Avatar](https://docs.unity3d.com/cn/2023.2/Manual/class-Avatar.html)、[状态机 (State Machine)](https://docs.unity3d.com/cn/2023.2/Manual/AnimationStateMachines.html)、[混合树 (Blend Tree)](https://docs.unity3d.com/cn/2023.2/Manual/class-BlendTree.html) 官方文档。
>
> 前置知识：[动画(Animation)](动画(Animation).md)

​`Animator`​ 组件用于将动画分配给场景中的游戏对象。它需要引用一个 `Animator Controller` 资源，该资源定义了要使用的动画剪辑，并控制剪辑之间的混合与过渡。

---

### 图示

![已分配控制器和 Avatar 的 Animator 组件](https://docs.unity3d.com/cn/2023.2/uploads/Main/MecanimAnimatorComponent.png)

下图展示了动画剪辑、Animator Controller 和 Avatar 等资源如何在游戏对象的 `Animator` 组件中协同工作：

![动画系统各部分连接示意图](https://docs.unity3d.com/cn/2023.2/uploads/Main/MecanimHowItFitsTogether.jpg)

‍

### 核心参数

#### **Controller**

​`控制器`​ - 附加到此游戏对象的 `Animator Controller` 资源。它是一个状态机，负责管理和切换不同的动画状态。

#### **Avatar**

​`虚拟形象`​ - 关联到此游戏对象的 `Avatar` 资源。此参数主要用于人形（Humanoid）角色的动画，它定义了骨骼映射关系。

‍

### 可配参数

#### **Apply Root Motion**

​`应用根运动` - 勾选后，游戏对象的位置和旋转将由动画剪辑本身的数据驱动，而不是由脚本控制。这对于实现精确的角色移动非常有用。

#### **Update Mode**

​`更新模式`​ - 选择 `Animator` 的更新时机和所使用的时间标度。

- ​`Normal`​：与 `Update`​ 函数同步更新。`Animator`​ 的播放速度会受到 `Time.timeScale` 的影响。如果时间变慢，动画也会随之减速。
- ​`Animate Physics`​：与 `FixedUpdate` 函数同步更新，即与物理系统步调一致。当动画需要与物理交互时（例如，角色推动刚体），应使用此模式。
- ​`Unscaled Time`​：与 `Update`​ 函数同步更新，但会忽略 `Time.timeScale`​。即使游戏暂停（`Time.timeScale = 0`），动画依然会以正常速度播放。适用于不受游戏暂停影响的UI动画等场景。

#### **Culling Mode**

​`剔除模式` - 用于优化动画性能，决定当角色在摄像机视野外时的行为。

- ​`Always Animate`：始终播放动画，即使游戏对象在屏幕外也不进行剔除。性能开销最大。
- ​`Cull Update Transforms`：当渲染器不可见时，禁用变换组件的重定向、IK（反向动力学）和写入操作，但动画状态机仍在运行。
- ​`Cull Completely`：当渲染器不可见时，完全禁用动画，包括状态机更新。这是性能最优的选项。

‍

### 动画曲线信息

​`Animator`​ 组件底部的信息框提供了当前 `Animator Controller` 中所有动画剪辑的数据摘要。动画剪辑包含“曲线”数据，用于描述属性值随时间的变化。

- **Clip Count**  
  ​`剪辑数量`​ - 当前 `Animator Controller` 使用的动画剪辑总数。
- **Curves (Pos, Rot &amp; Scale)**   
  ​`变换曲线` - 用于控制游戏对象位置、旋转或缩放的曲线总数。对于人形动画，这部分也包含了非标准肌肉骨骼（如尾巴、飘带）的动画曲线。
- **Muscles**  
  ​`肌肉`​ - 用于人形动画的肌肉动画曲线数量。这些曲线驱动标准人形 `Avatar` 的肌肉运动。
- **Generic**  
  ​`泛型` - 用于驱动其他数值属性（如材质颜色）的浮点型曲线数量。
- **PPtr**  
  ​`对象引用` - 精灵动画曲线的总数，主要由 Unity 的 2D 系统使用。
- **Curves Count**  
  ​`曲线总数` - 所有动画曲线的合计总数。
- **Constant**  
  ​`常量曲线` - 被优化为恒定（不变）值的动画曲线数量。如果动画文件中包含值不变的曲线，Unity 会自动进行此项优化。
- **Dense**  
  ​`密集曲线` - 使用“密集”方法存储数据的动画曲线数量。该方法存储离散值并在线性插值，比“流”方法占用更少的内存。
- **Stream**  
  ​`流曲线` - 使用“流”方法存储数据的动画曲线数量。该方法包含时间和切线数据用于曲线插值，占用的内存远多于“密集”方法。

> **注意**：如果在导入动画剪辑时，将 `Anim Compression`​ 设置为 `Optimal`​，Unity 会自动判断使用 `Dense`​ 还是 `Stream` 方法来存储每条曲线，以达到最佳优化效果。

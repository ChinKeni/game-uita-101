# 矩形变换 (Rect Transform)

> 参考 [矩形变换 (Rect Transform)](https://docs.unity3d.com/cn/2023.2/Manual/class-RectTransform.html)、[变换 (Transform)](https://docs.unity3d.com/cn/2023.2/Manual/class-Transform.html) 官方文档。
>
> 深入理解：推荐阅读 [UI 基本布局](https://docs.unity3d.com/cn/2023.2/Manual/UIBasicLayout.html) 页面，以全面了解矩形变换的用法。

​`矩形变换 (Rect Transform)`​ 组件是 `变换 (Transform)`​ 组件在 UI 系统中的对应组件。与 `Transform`​ 组件表示单个点不同，`Rect Transform`​ 表示一个矩形区域，用于定位和缩放 UI 元素。当一个 `Rect Transform`​ 的父对象也是 `Rect Transform` 时，它可以根据父矩形进行灵活的定位和尺寸调整，这是实现响应式 UI 的基础。

## 图示

![Rect Transform Component](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_RectTransform.png)

‍

## 核心属性

### 位置与尺寸

- **Pos (X, Y, Z)**   
  ​`位置`​ - 矩形 `轴心点 (Pivot)`​ 相对于 `锚点 (Anchors)` 的位置。  
  ‍
- **Width / Height**  
  ​`宽度 / 高度` - 矩形本身的宽度和高度。  
  ‍
- **Left, Top, Right, Bottom**  
  ​`边距`​ - 当锚点分离时（即 `Anchors`​ 的 `Min`​ 和 `Max`​ 值不相同时），这些值会取代 `Pos`​ 和 `Width/Height`。它们表示矩形的四个边缘相对于锚点所定义区域的距离，可以理解为内边距。

‍

### 锚点 (Anchors) 与 轴心点 (Pivot)

这是 `Rect Transform` 最核心和最关键的概念，用于实现灵活的 UI 布局。

- **Anchors**  
  ​`锚点`​ - 决定 UI 元素如何随父矩形尺寸变化而变化的关键属性。它由两个点（`Min`​ 和 `Max`）定义一个锚定区域。

  - **Min**: 锚点区域左下角的位置，以父矩形尺寸的比例表示（`0,0` 代表父级左下角）。
  - **Max**: 锚点区域右上角的位置，以父矩形尺寸的比例表示（`1,1` 代表父级右上角）。  
    ‍
- **Pivot**  
  ​`轴心点`​ - 矩形自身进行旋转、缩放和定位的中心点。该值以矩形自身尺寸的比例表示，`0,0`​ 是左下角，`0.5,0.5`​ 是中心，`1,1` 是右上角。

‍

### 变换

- **Rotation**  
  ​`旋转`​ - 对象围绕其 `轴心点 (Pivot)` 沿 X、Y、Z 轴的旋转角度（单位：度）。  
  ‍
- **Scale**  
  ​`缩放` - 对象在 X、Y、Z 轴上的缩放因子。

---

## 编辑器模式

这些是仅在编辑器中使用的辅助工具，用于简化 UI 布局的调整过程。

- **Blueprint Mode**  
  ​`蓝图模式`​ - 勾选后，可以在 Scene 视图中忽略旋转和缩放效果来编辑 `RectTransform`，使其像未旋转和缩放一样进行对齐和调整。此模式下会启用贴靠功能，非常适合在复杂旋转和缩放下进行精准布局。  
  ‍
- **Raw Edit Mode**  
  ​`原始编辑模式`​ - 勾选后，当编辑 `轴心点 (Pivot)`​ 和 `锚点 (Anchors)` 的值时，Unity 不会自动调整矩形的位置和大小来维持其在屏幕上的视觉位置。这允许你直接修改锚点和轴心点数据，而不产生副作用，适用于需要精确控制这些底层值的特殊情况。

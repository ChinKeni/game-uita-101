# 垂直布局组 (Vertical Layout Group)

> 参考 [垂直布局组 (Vertical Layout Group)](https://docs.unity3d.com/cn/2023.2/Manual/script-VerticalLayoutGroup.html)、[自动布局 (Auto Layout)](https://docs.unity3d.com/cn/2023.2/Manual/UIAutoLayout.html) 官方文档。
>
> 前置知识：[Rect Transform](https://docs.unity3d.com/cn/2023.2/Manual/class-RectTransform.html)

​`垂直布局组` 组件会将其所有子布局元素（UI对象）按照从上到下的顺序纵向排列。它会自动计算和控制子元素的位置，并能根据子元素的尺寸（最小、偏好、灵活）来调整自身的整体高度。

### 图示

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_VerticalLayoutGroupInspector.png)

‍

### 核心参数

这些参数主要用于调整布局组的基本边距、间距和对齐方式。

#### **Padding**

​`内边距` - 在布局组的四个边缘与内部子元素之间设置的空白区域。

#### **Spacing**

​`间距` - 在布局组内的各个子元素之间设置的垂直间距。

#### **Child Alignment**

​`子元素对齐` - 当子元素没有填满布局组的可用空间时，用于设定它们在布局组内的整体对齐方式（例如，顶部对齐、中部对齐、底部对齐）。

‍

### 尺寸控制参数

这些参数用于更精细地控制布局组如何管理其子元素的尺寸。

#### **Control Child Size**

​`控制子元素尺寸` - 勾选后，布局组将接管并控制其子元素的宽度和/或高度。

- ​`Width`: 强制所有子元素的宽度与布局组的宽度一致（扣除Padding）。
- ​`Height`: 根据布局规则（最小、偏好、灵活高度）分配和设置每个子元素的高度。

#### **Use Child Scale**

​`使用子元素缩放`​ - 在计算和应用布局时，是否将子元素 `Rect Transform`​ 组件中的 `Scale` 值考虑在内。

- 一般不配置，特殊情况（如子元素有动画缩放）下可能需要启用。

#### **Child Force Expand**

​`强制子元素扩展` - 是否强制子元素扩展以填满布局组中的额外可用空间。

- ​`Width`: 强制子元素在水平方向上填满布局组的宽度。
- ​`Height`: 强制子元素在垂直方向上填满布局组的高度。

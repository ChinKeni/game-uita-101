# 水平布局组 (Horizontal Layout Group)

> 参考 [自动布局 (Auto Layout)](https://docs.unity3d.com/cn/2023.2/Manual/UIAutoLayout.html) 官方文档。
>
> 前置知识：[Rect Transform](https://docs.unity3d.com/cn/2023.2/Manual/class-RectTransform.html) 的基本概念。

​`水平布局组 (Horizontal Layout Group)` 组件会将其所有子布局元素（UI对象）从左到右并排地放置在一起。它是一个强大的自动化布局工具，常用于创建列表、工具栏、标签页等水平排列的UI。

该组件会根据子元素的最小宽度、偏好宽度和灵活宽度来智能地计算和分配空间。

---

## 水平布局组 (Horizontal Layout Group)

### 图示

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_HorizontalLayoutGroupInspector.png)

‍

### 核心参数

#### **Padding**

​`内边距` - 布局组容器的边缘与其内部所有子元素之间的空间。

- ​`Left`​, `Right`​, `Top`​, `Bottom` 分别控制四个方向的边距。

#### **Spacing**

​`间距` - 布局组内相邻子元素之间的水平距离。

#### **Child Alignment**

​`子元素对齐` - 当子元素的总宽度小于布局组容器的宽度时，此参数决定了所有子元素作为一个整体在容器内的对齐方式。

- 例如，`UpperLeft`​ 会将所有子元素作为一个整体，靠到容器的左上角。`MiddleCenter` 则会将它们居中放置。
- 此设置在 `Child Force Expand` 启用时无效。

‍

### 可配参数

#### **Control Child Size**

​`控制子项尺寸` - 决定布局组是否要强制控制其子布局元素的宽度和高度。

- ​`Width`​：勾选后，布局组会根据布局规则（如`Child Force Expand`）来设定子元素的宽度。
- ​`Height`：勾选后，布局组会强制所有子元素的高度与布局组自身的高度（减去上下内边距）保持一致。

#### **Use Child Scale**

​`使用子项缩放`​ - 在计算布局时，是否考虑子元素的 `Scale` 值。

- 一般不配置。在特殊情况下，如果子元素有缩放（Scale不为1），勾选此项可以确保布局计算的准确性。

#### **Child Force Expand**

​`强制子项扩展` - 决定是否强制子元素拉伸以填满布局组中的可用空间。

- ​`Width`​：勾选后，如果布局组存在额外的未分配宽度，子元素会根据其灵活宽度（Layout Element组件中的`Flexible Width`）按比例拉伸，以填满整个容器宽度。
- ​`Height`：勾选后，子元素的高度将被强制拉伸以填满布局组的整个高度（减去上下内边距）。

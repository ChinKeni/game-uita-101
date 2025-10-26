# 布局元素 (Layout Element)

> 参考 [自动布局 (Auto Layout)](https://docs.unity3d.com/cn/2023.2/Manual/UIAutoLayout.html) 、 [布局元素 (Layout Element)](https://docs.unity3d.com/cn/2023.2/Manual/script-LayoutElement.html) 官方文档。
>
> 前置知识： [内容大小适配器 (Content Size Fitter)](https://docs.unity3d.com/cn/2023.2/Manual/script-ContentSizeFitter.html)

​`Layout Element`​ 组件用于覆写（Override）UI 元素在自动布局系统中的最小尺寸、偏好尺寸或灵活尺寸。当一个游戏对象上挂载了 `Layout Element`​ 组件后，布局控制器（如 `Horizontal Layout Group`​）会优先使用此组件中定义的数值，而不是从 `Image`​ 或 `Text` 等组件中获取默认的布局属性。

布局控制器会按照以下优先级顺序为布局元素分配宽度或高度：

1. **最小尺寸 (Min Size)** ：首先，确保元素的尺寸不小于指定的最小宽度和高度。
2. **偏好尺寸 (Preferred Size)** ：在满足最小尺寸后，如果有足够的可用空间，控制器会尝试将元素扩展到偏好宽度和高度。
3. **灵活尺寸 (Flexible Size)** ：在满足所有元素的偏好尺寸后，如果仍有额外的可用空间，控制器会根据灵活宽度和高度的权重，将剩余空间分配给设置了灵活尺寸的元素。

---

## 图示

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_LayoutElementInspector.png)

‍

## 核心参数

启用任一尺寸属性（如 `Min Width`）的复选框后，旁边会显示一个输入字段，用于指定具体的数值。

#### **Ignore Layout**

​`忽略布局` - 勾选后，整个自动布局系统将完全忽略此游戏对象及其子对象。它将不会参与任何布局计算。

‍

#### **Min Width / Min Height**

​`最小宽度 / 最小高度` - 定义此布局元素必须满足的最小尺寸。即使空间不足，布局系统也会尽力保证其尺寸不小于此值。单位为常规像素单位。

‍

#### **Preferred Width / Preferred Height**

​`偏好宽度 / 偏好高度` - 定义此布局元素期望达到的理想尺寸。在所有元素的最小尺寸都满足后，布局系统会尝试将元素扩展至此尺寸。单位为常规像素单位。

‍

#### **Flexible Width / Flexible Height**

​`灵活宽度 / 灵活高度` - 定义此元素在父容器存在额外空间时，应该分配到的空间比例。

- 这是一个相对值（权重）。例如，如果两个同级元素的 `Flexible Width`​ 都设置为 `1`​，它们将平分所有额外的水平空间。如果一个设置为 `1`​，另一个设置为 `2`，后者将获得两倍于前者的额外空间。
- 如果值为 `0` 或未启用，则该元素不参与额外空间的分配。
- 最常见的设置是 `0`​ 或 `1`。

‍

#### **Layout Priority**

​`布局优先级`​ - 决定当一个游戏对象上存在多个影响布局的组件时（例如同时有 `Image`​ 和 `LayoutElement`），布局系统应该使用哪个组件的布局属性。

- 布局系统会优先采用 `Layout Priority` 值最高的组件所提供的布局属性（如最小尺寸、偏好尺寸）。
- 如果多个组件的 `Layout Priority` 值相同，系统将使用每个属性的最大值，而不管该属性来自哪个组件。

‍

## 用法详解

#### **尺寸单位**

- **常规单位**：`Min`​ 和 `Preferred` 尺寸使用常规的像素单位，定义了元素的绝对大小。
- **相对单位**：`Flexible` 尺寸使用相对单位（权重），用于按比例分配剩余的父容器空间。

‍

#### **偏好尺寸与灵活尺寸的协同工作**

在某些情况下，同时指定偏好尺寸和灵活尺寸非常有用。

- 布局系统仅在所有元素的**偏好尺寸**被完全满足后，才会开始分配**灵活尺寸**所对应的额外空间。
- 如果一个元素只设置了 `Flexible Size`​ 而没有设置 `Preferred Size`​，它会先保持其 `Min Size`​，等待其他设置了 `Preferred Size` 的元素扩展到其偏好尺寸后，才开始参与剩余空间的分配。
- 通过同时设置 `Preferred Size`​ 和 `Flexible Size`，可以使该元素与其他元素一起平滑地扩展到其偏好尺寸，并在所有偏好尺寸都满足后，继续按比例扩展以填充剩余空间，从而实现更复杂的布局动态。

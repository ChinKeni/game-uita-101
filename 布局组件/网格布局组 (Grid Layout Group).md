# 网格布局组 (Grid Layout Group)

> 参考 [网格布局组 (Grid Layout Group)](https://docs.unity3d.com/cn/2023.2/Manual/script-GridLayoutGroup.html) 官方文档。
>
> 前置知识： [内容大小适配器 (Content Size Fitter)](https://docs.unity3d.com/cn/2023.2/Manual/script-ContentSizeFitter.html) 内容。

​`网格布局组` 组件会将其子布局元素（UI对象）强制排列在网格中。

---

## 图示

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_GridLayoutGroupInspector.png)

‍

## 核心参数

#### **Padding**

​`内边距` - 布局组的四个边缘与内容之间的填充空间。

‍

#### **Cell Size**

​`单元格尺寸`​ - 定义网格中每个布局元素的固定大小。**注意：**  此组件会忽略子元素的最小尺寸、偏好尺寸和灵活尺寸等属性，强制所有子元素使用此处定义的尺寸。

‍

#### **Spacing**

​`间距` - 网格中布局元素之间的水平和垂直间距。

‍

#### **Start Corner**

​`起始角` - 定义第一个子元素放置在网格的哪个角落。

- ​`Upper Left`：左上角。
- ​`Upper Right`：右上角。
- ​`Lower Left`：左下角。
- ​`Lower Right`：右下角。

‍

#### **Start Axis**

​`起始轴` - 定义网格的填充方向。

- ​`Horizontal`：水平方向。元素会先填满一行，然后再换到下一行。
- ​`Vertical`：垂直方向。元素会先填满一列，然后再换到下一列。

‍

#### **Child Alignment**

​`子项对齐` - 当所有子元素构成的网格没有填满整个布局组的可用空间时，用于设置网格整体的对齐方式。

‍

#### **Constraint**

​`约束`​ - 将网格约束为固定的行数或列数，这对于结合 `内容大小适配器` 实现自动布局至关重要。

- ​`Flexible`：灵活模式。不固定行数或列数，网格会尝试使行数和列数大致相同。
- ​`Fixed Column Count`：固定列数。指定网格的列数是固定的，行数会根据子元素数量自动增减。
- ​`Fixed Row Count`：固定行数。指定网格的行数是固定的，列数会根据子元素数量自动增减。

---

## 与内容大小适配器 (Content Size Fitter) 结合使用

当 `GridLayoutGroup`​ 与 `Content Size Fitter`​ 结合使用以实现内容自适应时，需要正确配置 `Constraint` 属性来帮助自动布局系统计算尺寸。

### 灵活宽度和固定高度

此设置使网格在添加元素时水平扩展，保持固定的行数。

- **Grid Layout Group** `Constraint`​：设置为 `Fixed Row Count`。
- **Content Size Fitter** `Horizontal Fit`​：设置为 `Preferred Size`。
- **Content Size Fitter** `Vertical Fit`​：设置为 `Preferred Size`​ 或 `Unconstrained`。

  - 如果设置为 `Unconstrained`，你需要手动为该对象提供足够的高度以容纳指定的行数。

‍

### 固定宽度和灵活高度

此设置使网格在添加元素时垂直扩展，保持固定的列数。这是最常见的用法，例如背包或列表。

- **Grid Layout Group** `Constraint`​：设置为 `Fixed Column Count`。
- **Content Size Fitter** `Horizontal Fit`​：设置为 `Preferred Size`​ 或 `Unconstrained`。

  - 如果设置为 `Unconstrained`，你需要手动为该对象提供足够的宽度以容纳指定的列数。
- **Content Size Fitter** `Vertical Fit`​：设置为 `Preferred Size`。

‍

### 灵活宽度和灵活高度

此设置使网格在宽度和高度上都能灵活扩展，但无法精确控制行数和列数。布局系统会尝试使两者数量大致相等。

- **Grid Layout Group** `Constraint`​：设置为 `Flexible`。
- **Content Size Fitter** `Horizontal Fit`​：设置为 `Preferred Size`。
- **Content Size Fitter** `Vertical Fit`​：设置为 `Preferred Size`。

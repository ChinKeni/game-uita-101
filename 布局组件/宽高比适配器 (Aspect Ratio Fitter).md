# 宽高比适配器 (Aspect Ratio Fitter)

# 宽高比适配器 (Aspect Ratio Fitter)

> 参考 [宽高比适配器 (Aspect Ratio Fitter)](https://docs.unity3d.com/cn/2023.2/Manual/script-AspectRatioFitter.html) 官方文档。
>
> 前置知识： 对 Unity UI 的核心组件 `RectTransform` 有基本了解。

​`宽高比适配器 (Aspect Ratio Fitter)`​ 是一个布局控制器，用于根据设定的宽高比自动调整其所在UI元素 (`Layout Element`) 的尺寸。

### 图示

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_AspectRatioFitterInspector.png)

‍

### 核心参数

#### **Aspect Mode**

​`模式` - 用于设定如何调整矩形的大小以强制应用设定的宽高比。

- ​`None`: 不执行任何操作，禁用该组件。
- ​`Width Controls Height`​: 宽度控制高度。根据当前 `RectTransform` 的宽度和指定的宽高比，自动调整其高度。
- ​`Height Controls Width`​: 高度控制宽度。根据当前 `RectTransform` 的高度和指定的宽高比，自动调整其宽度。
- ​`Fit In Parent`: 适应父级。自动调整UI元素的大小、位置和锚点，使其在保持宽高比的前提下，完整地显示在父级矩形内部。这可能会在父级矩形内留下空白区域。
- ​`Envelope Parent`: 包围父级。自动调整UI元素的大小、位置和锚点，使其在保持宽高比的前提下，完全覆盖父级的整个区域。这可能导致UI元素的部分区域超出父级矩形。

‍

#### **Aspect Ratio**

​`宽高比`​ - 需要强制执行的宽高比，计算方式为 `宽度 / 高度`​。例如，16:9 的比例应输入 `1.777`​ (16/9)，4:3 的比例应输入 `1.333` (4/3)。

‍

### 使用技巧

该组件不考虑其他布局信息（如 `Min Size`​ 或 `Preferred Size`​）。一个非常关键的细节是，尺寸的调整是围绕 `RectTransform`​ 的轴心 (`Pivot`)进行的。

这意味着可以通过调整轴心来控制UI元素的对齐和扩展方式。例如，将轴心设置在顶部中心 `(0.5, 1)`，当尺寸调整时，元素的顶部边缘位置将保持不变，宽度会向两侧均匀扩展，而高度只会向下扩展。

‍

### 注意

使用后会让 `RectTransform` 的部分设置失效，使其他依赖的相关脚本会失去作用产生bug，如果遇见，切记是这个引起的。

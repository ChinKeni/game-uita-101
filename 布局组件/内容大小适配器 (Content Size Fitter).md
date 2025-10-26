# 内容大小适配器 (Content Size Fitter)

> 参考 [内容大小适配器 (Content Size Fitter)](https://docs.unity3d.com/cn/2023.2/Manual/script-ContentSizeFitter.html) 官方文档。

## 图示

![image](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_ContentSizeFitterInspector.png)

‍

## 核心参数

### **Horizontal Fit**

​`水平适配`​ - 控制 `RectTransform` 的宽度如何根据其内容进行适配。

- ​`Unconstrained`​: 不适配。不根据布局元素调整宽度，保持 `RectTransform` 的原始宽度。
- ​`Min Size`​: 最小尺寸。根据布局元素（如 `Layout Element`​ 组件）计算出的 **最小宽度** 来设置自身的宽度。
- ​`Preferred Size`​: 首选尺寸。根据布局元素（如 `Text`​、`Image`​ 或布局组）计算出的 **首选宽度** 来设置自身的宽度。这是最常用的选项。

‍

### **Vertical Fit**

​`垂直适配`​ - 控制 `RectTransform` 的高度如何根据其内容进行适配。

- ​`Unconstrained`​: 不适配。不根据布局元素调整高度，保持 `RectTransform` 的原始高度。
- ​`Min Size`​: 最小尺寸。根据布局元素（如 `Layout Element`​ 组件）计算出的 **最小高度** 来设置自身的高度。
- ​`Preferred Size`​: 首选尺寸。根据布局元素（如 `Text`​、`Image`​ 或布局组）计算出的 **首选高度** 来设置自身的高度。这也是最常用的选项。

---

## 描述与工作原理

​`内容大小适配器 (Content Size Fitter)`​ 是一个布局控制器，用于根据其内容自动调整自身 `RectTransform` 的大小。

它的大小数据来源于附加在同一游戏对象上的其他布局元素，例如 `Image`​、`Text`​ 组件，或者 `布局组 (Layout Group)`​、`布局元素 (Layout Element)` 组件。

‍

### **重要注意事项：轴心 (Pivot)**

> 参考 [矩形变换 (Rect Transform)](矩形变换%20(Rect%20Transform).md)

​`Content Size Fitter`​ 调整大小时，是围绕 `RectTransform`​ 的 `轴心 (Pivot)`​ 进行的。这意味着 `轴心` 的位置会直接影响尺寸变化的视觉效果：

- **轴心居中 (0.5, 0.5):**  `RectTransform` 会向所有方向均匀扩展。
- **轴心在左上角 (0, 1):**  `RectTransform` 会向右侧和下方扩展。
- **轴心在底部中心 (0.5, 0):**  `RectTransform` 会向左右两侧和上方扩展。

正确设置 `轴心` 对于获得预期的自适应布局效果至关重要。

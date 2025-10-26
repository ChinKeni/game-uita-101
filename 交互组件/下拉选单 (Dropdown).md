# 下拉选单 (Dropdown)

> 参考 [下拉选单 (Dropdown)](https://docs.unity3d.com/cn/2023.2/Manual/script-Dropdown.html) 官方文档。
>
> 前置知识： [可选基类 ／交互基类 (Selectable Base Class)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html) 、 [滚动矩形 (Scroll Rect)](https://docs.unity3d.com/cn/2023.2/Manual/script-ScrollRect.html) 内容。

下拉选单（`Dropdown`）可用于让用户从选项列表中选择单个选项。控件会显示当前选择的选项，单击后会展开一个选项列表供用户选择。

---

## 图示

![下拉选单组件 Inspector](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_DropdownInspector.png)  
​![下拉选单关闭状态](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_DropdownExample.png)  
​![下拉选单展开状态](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_DropdownExampleOpen.png)

‍

## 核心参数

继承自 [可选基类 (Selectable)](https://docs.unity3d.com/cn/2023.2/Manual/script-Selectable.html) 的通用交互参数。

- **Interactable**: 控制该组件是否接受用户输入。
- **Transition**: 控件响应用户操作时的视觉变化方式（如颜色变化、精灵图切换等）。
- **Navigation**: 定义使用键盘或手柄时，UI 元素之间的导航顺序。

‍

### **Template**

​`模板`​ - 核心参数，指向一个作为下拉列表模板的 `RectTransform`。当用户点击下拉选单时，系统会实例化这个模板来显示所有选项。

- 模板对象在默认情况下处于非活动状态，编辑时可激活以便于预览。
- 模板内部必须包含一个带有 `Toggle`​ 组件的列表项，系统会为 `Options` 中的每个选项复制这个列表项。
- 通过 `GameObject > UI > Dropdown`​ 创建的默认模板包含了一个 `Scroll View`，以便在选项过多时可以滚动查看。

![简单的模板层级结构](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_DropdownHierarchySimple.png)  
​![包含滚动视图的模板层级结构](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_DropdownHierarchyScrolling.png)

‍

### **Caption Text / Caption Image**

​`标题文本/图像`​ - 分别用于显示 **当前选中项** 的 `Text`​ 和 `Image` 组件。这两个字段是可选的。

‍

### **Item Text / Item Image**

​`列表项文本/图像`​ - 分别用于显示 **下拉列表中每个选项** 的 `Text`​ 和 `Image`​ 组件。这两个字段是可选的，通常是 `Template` 中列表项预制体的子对象。

‍

### **Value**

​`值`​ - 当前选中项的索引。这是一个整数，`0`​ 代表第一个选项，`1` 代表第二个，以此类推。可以通过代码读取或设置此值来获取或更改当前选项。

‍

### **Options**

​`选项列表` - 定义下拉选单中所有可供选择的选项。

- 可以在 Inspector 中手动配置。
- 每个选项都可以包含一个文本字符串和一个图像（`Sprite`）。

‍

---

## 事件 (Events)

### **On Value Changed**

当用户在下拉列表中选择一个新选项时触发的 [UnityEvent](https://docs.unity3d.com/cn/2023.2/Manual/UnityEvents.html)。

- 此事件会传递一个 `int`​ 类型的参数，即新选中项的索引（`Value`）。

‍

---

## 工作原理与配置

### 设置文本和图像支持

​`Dropdown` 组件可以同时支持文本和图像，也可以只支持其中一种，或都不支持。

- **支持文本**：必须同时设置 `Caption Text`​ 和 `Item Text` 属性。
- **支持图像**：必须同时设置 `Caption Image`​ 和 `Item Image` 属性。
- 通过 `GameObject > UI > Dropdown`​ 创建的默认预制体只设置了文本支持。如果需要显示图像，需要手动创建 `Image` 组件并关联到相应字段。

‍

### 放置下拉列表

下拉列表展开时的位置由 `Template`​ 对象的 `RectTransform`​ 的锚点（`Anchor`​）和轴心（`Pivot`）决定。

- **默认行为**：默认模板锚定在控件底部，轴心在顶部。这使得列表在展开时会出现在控件下方，并向下扩展。
- **自动反转**：`Dropdown` 包含一个简单的内置逻辑，如果按默认位置展开会导致列表超出画布边界，它会自动反转展开方向（例如，从下方改为上方）。
- **局限性**：此自动反转逻辑比较简单。如果模板的高度大于画布高度的一半减去控件本身的高度，当控件位于画布中心时，列表可能在任何方向都没有足够的空间完全显示。

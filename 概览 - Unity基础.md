# 概览 - Unity基础

如果有耐心的话，可以通过官方的文档进行全文学习，这里只会把最常用的一些组件拿出来讲解，做到覆盖大部分日常工作所需知识。

> [Unity 文档目录](https://docs.unity.com/zh-cn "Unity 文档目录")
>
> [Unity 中文手册2023.2-User interface (UI)](https://docs.unity3d.com/cn/2023.2/Manual/UIToolkits.html "Unity 中文手册2023.2-User interface (UI)")
>
> 默认为已经掌握Unity界面的知识，可以参考 [Unity界面](https://docs.unity3d.com/cn/2023.2/Manual/UsingTheEditor.html) 学习界面。

‍

## 基本概念

引擎分为运行时和引擎工具，新人上手都是从运行时的UI组件进行学习，引擎工具也教编辑器工具作为技术扩展存在。

‍

## 将学到什么

- 常用UI组件以及组合形式
- 项目知识

‍

## 学习UI组件

### [可视组件](可视组件.md)

用来构成表现的最基本组件。

- [X] [文本(Text)](可视组件/文本(Text).md)
- [X] [图像(Image)](可视组件/图像(Image).md)
- [X] [遮罩(Mask)](可视组件/遮罩(Mask).md)
- [X] [网格效果(BaseMeshEffect)](可视组件/网格效果(BaseMeshEffect).md)
- [X] [元图(RawImage)](可视组件/元图(RawImage).md)

‍

### [交互组件](交互组件.md)

交互组件本身不可见，必须与一个或多个 [可视组件](https://docs.unity3d.com/cn/2023.2/Manual/UIVisualComponents.html) 组合才能正常工作。

- [X] [可选基类 ／交互基类 (Selectable Base Class)](交互组件/可选基类%20／交互基类%20(Selectable%20Base%20Class).md)
- [ ] [按钮 (Button)](交互组件/按钮%20(Button).md)
- [ ] [开关 (Toggle)](交互组件/开关%20(Toggle).md)
- [ ] [开关组 (Toggle Group)](交互组件/开关组%20(Toggle%20Group).md)
- [ ] [滑动条 (Slider)](交互组件/滑动条%20(Slider).md)
- [X] [滚动矩形／滚动视图 (Scroll Rect／Scroll View)](交互组件/滚动矩形／滚动视图%20(Scroll%20Rect／Scroll%20View).md)
- [ ] [下拉选单 (Dropdown)](交互组件/下拉选单%20(Dropdown).md)
- [ ] [输入字段 (Input Field)](交互组件/输入字段%20(Input%20Field).md)

‍

### [布局组件](布局组件.md)

官方分为基础布局和自动布局，这里合并到布局统一讲解。

‍

### [动效组件](动效组件.md)

分为动画(Animation)、状态机(Animator)，更推荐使用状态机。

[动画(Animation)](动效组件/动画(Animation).md)

[状态机(Animator)](动效组件/状态机(Animator).md)

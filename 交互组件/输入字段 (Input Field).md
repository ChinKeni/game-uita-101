# 输入字段 (Input Field)

> 参考 [输入字段 (Input Field)](https://docs.unity3d.com/cn/2023.2/Manual/script-InputField.html) 官方文档。
>
> 前置知识： [可选基类 ／交互基类 (Selectable Base Class)](可选基类%20／交互基类%20(Selectable%20Base%20Class).md) 、 [文本 (Text)](可视组件/文本(Text).md) 内容。

输入字段是一种使 `文本 (Text)` 控件的文本可编辑的方法。与其他交互控件一样，输入字段本身不是可见的 UI 元素，必须与一个或多个可视 UI 元素组合才能显示。

---

### 图示

![空的输入字段](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_InputFieldExample.png)  
​![在输入字段中输入的文本](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_InputFieldExample2.png)  
​![Input Field 组件检视面板](https://docs.unity3d.com/cn/2023.2/uploads/Main/UI_InputFieldInspector.png)

‍

### 核心参数

继承自 [可选基类 ／交互基类 (Selectable Base Class)](可选基类%20／交互基类%20(Selectable%20Base%20Class).md) 的 `Interactable`​, `Transition`​, `Navigation` 等参数此处不赘述。

#### **Text Component**

​`文本组件`​ - 对 `Text`​ 组件的引用，用于显示和编辑输入字段的内容。这是 `InputField` 工作的核心依赖。

#### **Text**

​`文本` - 输入字段的初始文本内容。在运行开始或编辑前显示。

#### **Character Limit**

​`字符限制` - 可以在输入字段中输入的最大字符数。值为 0 表示不限制。

#### **Placeholder**

​`占位符`​ - 一个可选的 `Graphic`​ 组件（通常是另一个 `Text` 组件），当输入字段为空时显示提示性文本，例如“请输入...”。

‍

### 内容类型参数

#### **Content Type**

​`内容类型` - 定义输入字段接受的字符类型，用于限制用户输入。

- ​`Standard`：标准模式。可以输入任何字符。
- ​`Autocorrected`：自动校正。输入时会跟踪未知单词并向用户建议更合适的替换，除非用户明确覆盖，否则会自动替换键入的文本。
- ​`Integer Number`：整数。只允许输入整数。
- ​`Decimal Number`：小数。只允许输入数字和单个小数点。
- ​`Alphanumeric`：字母和数字。允许输入字母和数字，但不能输入符号。
- ​`Name`：姓名。自动将每个单词的首字母大写。
- ​`Email Address`​：电子邮件地址。允许输入字母数字字符串，最多包含一个 `@` 符号，且句点不能相邻。
- ​`Password`​：密码。用星号 `*` 隐藏输入的字符，允许使用符号。
- ​`Pin`​：个人识别码。用星号 `*` 隐藏输入的字符，只允许输入整数。
- ​`Custom`​：自定义。允许您自定义下方的 `Line Type`​, `Input Type`​, `Keyboard Type`​ 和 `Character Validation` 选项。

‍

### 格式与显示参数

#### **Line Type**

​`行类型` - 定义文本在输入字段内的格式化方式。

- ​`Single Line`：单行。只允许文本在一行上显示。
- ​`Multi Line Submit`：多行提交。允许文本换行，但只有在需要时（即文本超出边界时）才会自动换行。
- ​`Multi Line Newline`：多行换行。允许文本使用多行，用户可以通过按回车键手动创建新行。

#### **Caret Blink Rate**

​`光标闪烁速率` - 定义了指示文本插入位置的光标的闪烁速率。

#### **Selection Color**

​`选择颜色` - 用于高亮显示所选文本部分的背景颜色。

#### **Hide Mobile Input**

​`隐藏移动端输入` - (仅限 iOS) 隐藏移动设备屏幕键盘附带的原生输入字段。

‍

### 事件 (Events)

#### **On Value Change**

当输入字段的文本内容发生变化时调用的 `UnityEvent`​。该事件可以将当前的文本内容作为 `string` 类型的动态参数发送。

#### **End Edit**

当用户完成文本内容编辑时（例如按下回车键提交或点击其他UI元素导致输入框失焦）调用的 `UnityEvent`​。该事件也可以将最终的文本内容作为 `string` 类型的动态参数发送。

‍

### 提示

- 要在脚本中获取输入字段的文本，请使用 `InputField`​ 组件本身的 `text`​ 属性，而不是其关联的 `Text`​ 组件的 `text` 属性。因为后者显示的内容可能会被裁剪，或者在密码模式下显示为星号。

‍

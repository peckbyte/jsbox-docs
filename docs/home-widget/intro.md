# 桌面小组件

Apple 在 iOS 14 引入了桌面小组件，JSBox `v2.12.0` 提供了全面支持。与此同时，通知中心小组件的支持也进入过时状态，会在未来的 iOS 版本中被 Apple 移除。

桌面小组件相较通知中心小组件有很大的不同，所以我们有必要花点时间来理解一些基本概念。

# 核心概念

桌面小组件的本质是基于时间线的一系列**快照**，而不是动态构建的界面。所以当用户看到小组件时，并不会直接运行小组件所包含的代码。相反，系统会在一些时机（时间线机制，之后会详细说明）调用小组件的代码，代码可以生成一个快照提供给系统。然后系统会在合适的时间展示这些快照，并通过一些策略重新获取一系列新的快照。

此外，桌面小组件仅能有限地处理用户交互：

- 2 * 2 布局仅支持点击整个小组件
- 2 * 4 和 4 * 4 布局支持点击某个控件
- 点击会打开主应用，并携带一个 URL 给主应用处理

这些系统限制决定了桌面小组件的角色更多是**快速展示信息**，并将复杂的交互和任务代理到主应用去执行。

# 配置小组件

JSBox 支持小组件的全部尺寸，添加步骤：

- 在桌面长按后点击左上角的加号
- 找到 JSBox 然后将某个小组件拖拽到桌面
- 在编辑模式选择“编辑小组件”
- 选择某个支持小组件的脚本

相比于通知中心小组件只能运行一个脚本（尽管 JSBox 提供了三个），桌面小组件可以通过上面的配置方式创建出任意多个实例，并且可以通过系统提供的“堆叠”功能将多个小组件叠放在一起，分别展示不同的内容。

具体使用方法，请参照 Apple 或网上提供的教程了解更多。

# 小组件参数

对于每个小组件，您可以设置要运行的脚本，以及提供更多信息的附加参数。

该参数是一个字符串，可以像这样获取：

```js
const inputValue = $widget.inputValue;
```

# 样例代码

为了让您可以更好地上手小组件的开发，我们创建了一些样例项目以供参考：

- [WidgetDoodles](https://github.com/cyanzhong/jsbox-widgets/tree/master/WidgetDoodles)
- [AppleDevNews2](https://github.com/cyanzhong/jsbox-widgets/tree/master/AppleDevNews2)
- [QRCode](https://github.com/cyanzhong/jsbox-widgets/blob/master/QRCode.js)
- [xkcd](https://github.com/cyanzhong/jsbox-widgets/blob/master/xkcd.js)
- [clock](https://github.com/cyanzhong/jsbox-widgets/blob/master/clock.js)

我们会在之后完善这个仓库，以提供更多例子。
<p align="center"><img src="https://github.com/hacktons/convex_bottom_bar/raw/master/doc/preview.png" alt="appBar preview"></p>
<p align="center">
  <a href="https://pub.dev/packages/convex_bottom_bar_gothomesafe"><img src="https://img.shields.io/pub/v/convex_bottom_bar_gothomesafe.svg" alt="pub.dev"></a>
  <a href="https://pub.dev/packages/convex_bottom_bar_gothomesafe/versions/3.0.0-nullsafety.0"><img src="https://img.shields.io/badge/nullsafety-3.0.0-blue.svg" alt="pub.dev"></a>
  <a href="https://github.com/hacktons/convex_bottom_bar"><img src="https://img.shields.io/badge/platform-flutter-ff69b4.svg" alt="github"></a>
  <a href="https://coveralls.io/github/hacktons/convex_bottom_bar"><img src="https://coveralls.io/repos/github/hacktons/convex_bottom_bar/badge.svg" alt="coverage status"></a>
  <a href="https://pub.dev/packages/convex_bottom_bar_gothomesafe/score"><img src="https://badges.bar/convex_bottom_bar_gothomesafe/likes" alt="likes"></a>
  <a href="https://codemagic.io/apps/5db10f597d3edb001a6ede16/5db10f597d3edb001a6ede15/latest_build"><img src="https://api.codemagic.io/apps/5db10f597d3edb001a6ede16/5db10f597d3edb001a6ede15/status_badge.svg" alt="build status"></a>
  <a href="https://github.com/hacktons/convex_bottom_bar/raw/LICENSE"><img src="https://img.shields.io/github/license/hacktons/convex_bottom_bar.svg" alt="license"></a>
</p>
<p align="center">
    <a href="https://github.com/hacktons/convex_bottom_bar/blob/master/README.md">English</a>
    | <a href="https://github.com/hacktons/convex_bottom_bar/blob/master/README-zh.md">简体中文</a>
</p>

---

ConvexBottomBar 是一个底部导航栏组件，用于展现凸起的 TAB 效果，支持多种内置样式与动画交互。你可以在[https://appbar.codemagic.app](https://appbar.codemagic.app)上找到在线样例。

**convex_bottom_bar_gothomesafe 现在是一个 [Flutter Favorite](https://flutter.dev/docs/development/packages-and-plugins/favorites) 插件库!**

<a href="https://flutter.dev/docs/development/packages-and-plugins/favorites">
 <img height="128" src="https://github.com/hacktons/convex_bottom_bar/raw/master/doc/flutter-favorite.png">
</a>

以下是一些支持的预定义样式：

|             **fixed**             |            **react**             |      **badge chip**       |
| :-------------------------------: | :------------------------------: | :-----------------------: |
|     ![](doc/appbar-fixed.gif)     |    ![](doc/appbar-react.gif)     | ![](doc/appbar-badge.gif) |
|          **fixedCircle**          |         **reactCircle**          |         **flip**          |
| ![](doc/appbar-fixed-circle.gif)  | ![](doc/appbar-react-circle.gif) | ![](doc/appbar-flip.gif)  |
|            **textIn**             |            **titled**            |       **tab image**       |
|    ![](doc/appbar-textIn.gif)     |    ![](doc/appbar-titled.gif)    | ![](doc/appbar-image.gif) |
|            **button**             |         **fixed corner**         |                           |
| ![](doc/appbar-single-button.png) | ![](doc/appbar-corner-fixed.png) |                           |

## 快速上手

通常 ConvexAppBar 可以通过设置 bottomNavigationBar 与 Scaffold 一起使用。

ConvexAppBar 具有两个构造函数，ConvexAppBar()将使用默认样式来简化选项卡的创建。

将此添加到您程序包的 pubspec.yaml 文件中，注意使用最新版本[![Pub](https://img.shields.io/pub/v/convex_bottom_bar_gothomesafe.svg)](https://pub.dartlang.org/packages/convex_bottom_bar_gothomesafe):

```yaml
dependencies:
  convex_bottom_bar_gothomesafe: ^latest_version
```

```dart
import 'package:convex_bottom_bar_gothomesafe/convex_bottom_bar_gothomesafe.dart';

Scaffold(
  bottomNavigationBar: ConvexAppBar(
    items: [
      TabItem(icon: Icons.home, title: 'Home'),
      TabItem(icon: Icons.map, title: 'Discovery'),
      TabItem(icon: Icons.add, title: 'Add'),
      TabItem(icon: Icons.message, title: 'Message'),
      TabItem(icon: Icons.people, title: 'Profile'),
    ],
    initialActiveIndex: 2,//optional, default as 0
    onTap: (int i) => print('click index=$i'),
  )
);
```

**Flutter Version Support**
由于 Flutter 迭代非常快。SDK 本身有可能出现不兼容的 API 变更，我们将继续支持 flutter 稳定版本，非稳定的 beta、dev channel
通过单独版本号进行兼容。

| **Stable Flutter Version** | **Package Version** |                               **More**                               |
| :------------------------: | :-----------------: | :------------------------------------------------------------------: |
|           >=1.20           |       >=2.4.0       |            从 v1.20 开始, Stack 组件的 API 发送不兼容变更            |
|           <1.20            |       <2.4.0        | v1.20 稳定版发布后，我们对老版本如 v1.17, v1.12 的支持将不再继续更新 |

如果你只需要一个单独的按钮，不妨试试 `ConvexButton`.

## 功能

- 提供多种内部样式
- 能够更改 AppBar 的主题
- 提供 Builder API 以自定义新样式
- 在 AppBar 上添加徽章
- 支持优雅的过渡动画
- 提供 Hook API 来重载一些内部样式
- RTL 布局支持

## Table of contents

- [主题](#主题)
- [角标](#角标)
- [单独按钮](#单独按钮)
- [样式重载](#样式重载)
- [RTL 支持](#RTL支持)
- [自定义样例](#自定义样例)
- [常见问题](#常见问题)
- [支持](#支持)

## 角标

如果需要在 TAB 上添加徽章/角标，请使用`ConvexAppBar.badge`来构建。

[![badge demo](doc/badge-demo-preview.gif)](doc/badge-demo.mp4 "badge demo")

```dart
ConvexAppBar.badge({0: '99+', 1: Icons.assistant_photo, 2: Colors.redAccent},
  items: [
    TabItem(icon: Icons.home, title: 'Home'),
    TabItem(icon: Icons.map, title: 'Discovery'),
    TabItem(icon: Icons.add, title: 'Add'),
  ],
  onTap: (int i) => print('click index=$i'),
);
```

`badge()`方法接受一个角标数组； 角标是带有选项卡项的映射，每个条目的值可以是 String，IconData，Color 或 Widget。

## 单独按钮

![button](doc/appbar-single-shape.png)

```dart
Scaffold(
  appBar: AppBar(title: const Text('ConvexButton Example')),
  body: Center(child: Text('count $count')),
  bottomNavigationBar: ConvexButton.fab(
    onTap: () => setState(() => count++),
  ),
);
```

## 主题

AppBar 默认使用内置样式，您可能需要为其设置主题。 以下是一些支持的属性：

![](doc/appbar-theming.png)

| Attributes      | Description                                                 |
| --------------- | ----------------------------------------------------------- |
| backgroundColor | AppBar 背景                                                 |
| gradient        | 渐变属性，可以覆盖 backgroundColor                          |
| height          | AppBar 高度                                                 |
| color           | icon/text 的颜色值                                          |
| activeColor     | icon/text 的**选中态**颜色值                                |
| curveSize       | 凸形大小                                                    |
| top             | 凸形到 AppBar 上边缘的距离                                  |
| style           | 支持的样式: **fixed, fixedCircle, react, reactCircle**, ... |
| chipBuilder     | 角标构造器 builder, **ConvexAppBar.badge**会使用默认样式    |

## 样式重载

重载 Tab 内置样式。 该 API 与`ConvexAppBar.builder`不同，为了满足您可能需要更新选项卡样式而不定义新的选项卡样式。
**温馨提示:**  
则此 Hook 能力是有限的，如果您提供的尺寸与内部样式不匹配，并且可能导致`overflow broken`。

```dart
StyleProvider(
  style: Style(),
  child: ConvexAppBar(
    initialActiveIndex: 1,
    height: 50,
    top: -30,
    curveSize: 100,
    style: TabStyle.fixedCircle,
    items: [
      TabItem(icon: Icons.link),
      TabItem(icon: Icons.import_contacts),
      TabItem(title: "2020", icon: Icons.work),
    ],
    backgroundColor: _tabBackgroundColor,
  ),
)
class Style extends StyleHook {
  @override
  double get activeIconSize => 40;

  @override
  double get activeIconMargin => 10;

  @override
  double get iconSize => 20;

  @override
  TextStyle textStyle(Color color) {
    return TextStyle(fontSize: 20, color: color);
  }
}
```

## RTL 支持

RTL 的内部适配，如果你配置了 Directionality，将自动支持 ltf 和 rtl 两种布局风格。

```dart
Directionality(
  textDirection: TextDirection.rtl,
  child: Scaffold(body:ConvexAppBar(/*TODO ...*/)),
)
```

## 自定义样例

如果默认样式与您的情况不符，请尝试使用`ConvexAppBar.builder()`，它可以让您自定义几乎所有 TAB 样式。

```dart
Scaffold(
  bottomNavigationBar: ConvexAppBar.builder(
    count: 5,
    backgroundColor: Colors.blue,
    style: TabStyle.fixed,
    itemBuilder: Builder(),
  )
);

/*user defined class*/
class Builder extends DelegateBuilder {
  @override
  Widget build(BuildContext context, int index, bool active) {
    return Text('TAB $index');
  }
}
```

完整的自定义示例可以在[example](example)中找到。

## 常见问题

如您在使用过程中有新功能建议或者遇到问题，请移步至[issue tracker](https://github.com/hacktons/convex_bottom_bar/issues)提交。

- [如何拦截 Tab 事件](doc/how-to-block-tab-event.md)
- [Flutter dev/beta channel 运行崩溃](doc/issue-crash-on-flutter-dev-channel.md)
- [动态修改选中的 TAB](doc/issue-change-active-tab-index.md)
- [如何给 TAB 添加图片而不是 ICON](doc/issue-image-for-actionitem.md)
- [如何移除 AppBar 的边缘阴影](doc/issue-remove-elevation.md)

## 支持

如果对你有帮助，微信扫码请作者喝杯咖啡 :)

![donate](doc/donate-wechat.jpeg)

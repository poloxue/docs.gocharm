---
title: "其他 TUI 框架"
weight: 10
---

# 其他 TUI 框架

相对而言，bubble tea 提供构建终端应用的基本框架，但如果你希望开发非常复杂应用，它确实还是有一些拙荆见肘，如常用的窗口组件或基本的布局能力，它是没有提供的。

这里再推荐 Go 中其他一些可供选择的 TUI 框架。

首先是 tview，一个基于 tcell 的富文本终端应用程序框架，提供了构建复杂交互 TUI 所需的组件和布局管理器。它支持颜色、表格、表单、列表等多种控件，非常适合构建复杂的 TUI 应用。

![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-10.gif)

其次是 termui:，一个基于 Go 的 TUI 库，灵感来源于 blessed-contrib 和 tui-rs。它提供了创建数据可视化和仪表板的简单方法，支持条形图、线图、饼图等多种图表类型，适用于构建需要数据展示的 TUI 应用。不过这个库已经很久没有更新了，如果你熟悉 rust，推荐使用 tui-rs。

![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-11.gif)


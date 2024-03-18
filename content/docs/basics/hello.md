---
title: "2. 第一个 BubbleTea 应用"
weight: 1
---

# 快速上手

[Bubble Tea](https://github.com/charmbracelet/bubbletea) 是一个小巧但强大的文本用户界面（TUI）框架，基于 Go 语言开发。

## 使用 Bubble Tea

Bubble Tea 受到 The Elm Architecture 的启发，基于这种有趣、功能性强且保持状态的架构来构建终端应用程序。无论是简单的行内应用程序、全窗口应用程序，还是两者的混合，Bubble Tea 都可使用。

要学会基于 Bubble Tea 开发终端应用，核心要理解它的三个基本部分组成：模型（Model）、更新函数（Update）和视图函数（View）。而 `Update` 和 `View` 都是属于 Model 的方法。

![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-05.png)

简单解释下它们的作用，如下:

- **模型（Model）**：描述应用程序状态的数据结构。
- **更新函数（Update）**：处理输入事件（如按键、计时器等），并更新模型。
- **视图函数（View）**：根据模型的当前状态渲染用户界面。

不明白？我们来通过一个例子解释下。

## 一个简单的例子：TUI 的计数器应用。

这是一个计数器的案例，我们通过输入 '+' 号增加计数值，减号减少计数值，输入 'q' 退出应用。

计数器的效果图，如下所示：

![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-03.gif)

如何基于 Bubble Tea 实现这个小应用呢？我们只要实现一个简单的 Model 即可。

如下是它最核心的 `model` 代码。

```go
type model int

// 初始化模型，设置计数器的初始值
func initialModel() model {
	return 0
}

func (m model) Init() tea.Cmd {
	return nil
}

// 更新函数，根据消息更新模型
func (m model) Update(msg tea.Msg) (tea.Model, tea.Cmd) {
	switch msg := msg.(type) {
	case tea.KeyMsg:
		switch msg.String() {
		case "q":
			return m, tea.Quit // 按下 'q' 退出程序
		case "+":
			return m + 1, nil // 按下 '+' 增加计数
		case "-":
			return m - 1, nil // 按下 '-' 减少计数
		}
	}
	return m, nil
}

// 视图函数，渲染界面
func (m model) View() string {
	return fmt.Sprintf("Count: %d\nPress + to increment, - to decrement, q to quit.\n", m)
}
```

观察以上代码，model 是一个基于 int 创建的新类型，用于保存应用的状态信息，即计数值。initialModel 创建一个初始值为 0 的 model。model 还提供了两个核心方法，分别是 `Update` 和 `View`。

如上段所述，`Update` 是用于接收用户消息，更新 model 状态。`View` 函数用于更新界面内容，展示给用户，它的更新通过 `Printf` 打印即可。

现在，只需将 `Model` 实例交给 Bubble Tea 框架运行皆可。

```go
func main() {
	p := tea.NewProgram(initialModel())
	if _, err := p.Run(); err != nil {
		fmt.Fprintf(os.Stderr, "Error running program: %v", err)
		os.Exit(1)
	}
}
```

这个应用到此就开发完成。

## 核心流程

## 一个小游戏：贪吃蛇

## 更多示例

我们通过一个简单的计数案例解释了 Bubble Tea 的使用。如果想了解它的更多能力，可参考 Bubble Tea 源码中的 [examples](https://github.com/charmbracelet/bubbletea/tree/master/examples/) 了解它更多的能力。

来自仓库中的一些案例效果图：

![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-06.gif)
![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-07.gif)
![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-08.gif)
![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-09.gif)

更多查看：[bubble tea's examples](https://github.com/charmbracelet/bubbletea/tree/master/examples)。

此外，仓库中还提供了[教程](https://github.com/charmbracelet/bubbletea/tree/master/tutorials/)，帮助我们理解如何使用这个框架构建终端应用程序。


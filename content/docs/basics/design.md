---
title: "3. 架构设计 Elm"
weight: 3
---

# 架构设计 Elm 

通过 Counter 计数器这个简单案例，重新理解下 Bubble Tea 中 The Elm Architecture 数据流向。

- **模型（Model）**：描述应用程序状态的数据结构。
- **更新函数（Update）**：处理输入事件（如按键、计时器等），并更新模型。
- **视图函数（View）**：根据模型的当前状态渲染用户界面。

![](https://cdn.jsdelivr.net/gh/poloxue/images@2024-02/2024-02-19-tui-library-bubble-tea-in-golang-04.png)

1. 用户与界面交互，触发消息。
2. 消息被发送到 Update 函数，Update 函数根据消息更新 Model。
3. 更新后的 Model 被传递给 View 函数，View 函数生成新的界面显示给用户。

现在，理解起来是不是非常简单了。

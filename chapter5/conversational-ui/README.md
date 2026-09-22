# 用对话逐步修改界面

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

用户说“把按钮放到右边，文字再短一点”，既描述布局也描述内容。本实验让 Agent 修改 React 源码，并通过实际构建和页面检查理解改动是否满足需求。

## 理解实验

自然语言请求需要落到具体文件与组件上。代码修改后，热更新可以快速展示效果，但编译通过仍不足以证明布局正确。浏览器中的实际页面是检验用户需求的重要依据。

## 动手之前

本项目包含前端和后端。先按技术参考分别安装依赖、配置服务地址并启动两端，再通过浏览器观察交互。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先按技术参考启动前后端，打开初始页面。选择一项明确的小改动，运行第一轮演示并比较源码差异与浏览器效果。确认后再叠加第二项要求，检查前一项是否仍然保留。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --quick
```

## 怎样解释结果

观察改动是否只影响目标组件、是否造成文字溢出，以及交互功能是否仍能使用。跳过构建的快速路径只检查部分行为，不能代替完整页面检查。

## 继续思考

如何把“看起来更清爽”转成可以讨论和检查的具体要求？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/conversational-ui/demo.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/conversational-ui/agent.py) → [campaign_browser.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/conversational-ui/campaign_browser.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

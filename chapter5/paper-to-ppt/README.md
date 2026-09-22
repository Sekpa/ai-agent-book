# 通过渲染与审核改进演示文稿

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

生成幻灯片源码时看不出的布局问题，常常在渲染后才出现。本实验让提议者生成 Slidev 文稿，再让审核者查看实际页面，学习“生成、观察、修改”的迭代方法。

## 理解实验

提议者负责内容与代码，审核者依据渲染图指出问题。审核需要具体对象，例如某页文字溢出或图表看不清，而不只是“再美观一点”。每轮修改都应能对应上一轮发现的问题。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先按技术参考安装 Node、Slidev 和浏览器依赖，再运行离线闭环。打开实际渲染的页面，核对修改前后的变化。随后再接入模型，选一篇短论文，观察内容准确性与视觉布局如何分别被检查。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --dry-run
```

## 怎样解释结果

离线路径使用预设行为，但仍会真实渲染文件。它验证的是制作流程。真实生成还应检查论文结论是否被准确转述，不能把页面成功导出当作内容已经正确。

## 继续思考

如果审核者发现一个事实错误和一个配色问题，下一轮应该先处理哪个？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/paper-to-ppt/demo.py) → [agents.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/paper-to-ppt/agents.py) → [renderer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/paper-to-ppt/renderer.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

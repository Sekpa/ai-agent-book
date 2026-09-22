# 理解工具选择的召回与成本权衡

[本章实验目录](../README.md) · [相关正文](../../book/chapter4.md) · [技术参考](REFERENCE.md)

随着工具数量增加，模型不仅要理解任务，还要从许多相似说明中选出合适工具。本项目让你在同一目录上比较不同选择策略，理解节省上下文可能付出的代价。

## 理解实验

全量策略保留所有说明，检索策略先筛候选，主动策略允许按需继续查找。候选越少通常越省输入，但所需工具一旦被过滤掉，后续决策就受到限制。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线比较，再把工具数扩大到示例支持的更大目录。查看召回与输入规模怎样变化。配置模型后，选择具体任务做端到端比较，避免用离线目录匹配分数替代真实调用成功率。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo_comparison.py --offline
```

## 怎样解释结果

目录扩大后的成本变化可能来自填充的干扰工具。解释结果时说明这些工具怎样构造，以及查询是否覆盖不同类别。主动查找增加的调用成本也应计入。

## 继续思考

怎样设计一个任务集，既包含常用工具，也能检查稀有工具是否被选择器遗漏？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo_comparison.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/active-tool-selection/demo_comparison.py) → [semantic_router.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/active-tool-selection/semantic_router.py) → [tool_knowledge_base.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter4/active-tool-selection/tool_knowledge_base.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

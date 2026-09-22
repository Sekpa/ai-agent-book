# 从具体修改中归纳写作规则

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

“这段有 AI 味”不是足够明确的修改指令。把读者修改前后的句子放在一起，才能讨论问题来自空泛措辞、句法重复还是段落组织。本实验从这些反馈形成可复用规则。

## 理解实验

候选规则需要描述适用条件，并用未参与提炼的文本验证。规则不应退化成固定禁词表：同一个词在不同语境中可能合理，也可能多余。模型裁判还需要与人工判断校准。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先挑一对修改前后的段落，解释改动怎样帮助读者理解。再按技术参考运行规则提炼，查看候选规则是否能解释其他例子。最后用新文本比较改写效果与事实保留。

## 怎样解释结果

更像某种文风，不一定更清楚。检查改写是否删除关键条件、改变事实或把具体解释换成另一套套话。少用标点也不能单独证明质量提升。

## 继续思考

怎样写一条关于“减少空泛结论”的规则，让它既能指导修改，又不会删掉必要概括？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[extract_rules.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/ai-style-skill/extract_rules.py) → [skill_manager.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/ai-style-skill/skill_manager.py) → [judge.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/ai-style-skill/judge.py) → [evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/ai-style-skill/evaluate.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

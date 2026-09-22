# 区分精确复制与语义相似

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

编辑工具要求待替换字符串逐字匹配，而模型可能改动空格、引号或不可见字符。本实验先定位复制链路，再研究监督训练能否改善精确复述。

## 理解实验

字符显示相同不代表字节相同。错误可能发生在模型生成、分词、序列化或工具参数处理，因此不能看到匹配失败就直接归因于模型。训练目标需要明确采用哪一种一致性标准。

## 动手之前

训练需要独立的数据与计算环境。先按技术参考核对数据准备、模型版本与硬件要求；第一次练习只检查少量样本和一个短流程。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先查看随机字符串与工具参数样例，运行分词和序列化审计，确认输入输出链路保留内容。随后按技术参考训练模型，在未见长度、字符组合和包装上下文中评估。

## 怎样解释结果

直接复述成功而工具调用失败，提示问题可能在接口层。评估应分别报告这些路径，并检查训练数据与测试字符串是否独立。

## 继续思考

如何用最小实验区分模型漏了一个空格与传输层进行了 Unicode 归一化？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[generate_data.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/exact-copy-sft/generate_data.py) → [tokenizer_audit.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/exact-copy-sft/tokenizer_audit.py) → [train_sft.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/exact-copy-sft/train_sft.py) → [evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/exact-copy-sft/evaluate.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

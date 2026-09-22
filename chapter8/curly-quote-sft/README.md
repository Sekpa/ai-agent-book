# 学习只在合适的语境中修改引号

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

中文正文通常使用弯引号，但代码和 JSON 中的引号承担语法作用。直接全局替换会破坏文件。本实验把修改范围作为学习目标，训练模型区分自然语言与受保护内容。

## 理解实验

样本同时包含应该转换与必须保留的片段，标签由可读规范约束。训练后不仅检查转换率，还要检查误修改和语法完整性。作用域判断比单纯记住两个字符更重要。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先生成教学数据并运行质量审计，人工查看中文引用、英文原文、代码和混合 Markdown 样例。确认标签后再训练适配器，最后在未见模板与组合上评价。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python generate_data.py
python quality_audit.py
```

## 怎样解释结果

转换更多不一定更好。一次损坏 JSON 的修改，可能比漏改一句正文更严重。应分别报告目标转换、受保护内容保留和语法检查结果。

## 继续思考

代码块中的中文注释包含引号时，规则应怎样定义，数据又应怎样标注？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[SKILL.md](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/curly-quote-sft/SKILL.md) → [generate_data.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/curly-quote-sft/generate_data.py) → [quality_audit.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/curly-quote-sft/quality_audit.py) → [train_sft.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/curly-quote-sft/train_sft.py) → [evaluate.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter8/curly-quote-sft/evaluate.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

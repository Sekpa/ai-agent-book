# 用分工与文件组织长文档翻译

[本章实验目录](../README.md) · [相关正文](../../book/chapter10.md) · [技术参考](REFERENCE.md)

长书翻译很难把所有原文与译文一直放在管理者上下文中。本实验让不同角色负责翻译与检查，并用文件保存完整产物，学习如何控制协调成本。

## 理解实验

管理者保留任务、计划和文件索引，工作角色读取所需章节并写出产物。术语与结构检查负责跨章节一致性。只传索引可以减少上下文增长，但仍需保证角色拿到了必要背景。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线计划展示，理解角色分工与文件流转。再按技术参考选取短章节进行真实翻译，对照术语表、章节产物与审校结果，最后再扩展到整书。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --dry-run
```

## 怎样解释结果

离线计划不能证明翻译质量。实际检查应覆盖内容遗漏、术语漂移、链接和图表引用；管理者上下文较小也不意味着全部调用成本不随篇幅增长。

## 继续思考

术语在后面章节出现新含义时，怎样更新共享约定而不让已经完成的章节悄悄失去一致性？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/book-translation/demo.py) → [agents.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/book-translation/agents.py) → [consistency.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/book-translation/consistency.py) → [consistency_auditor.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter10/book-translation/consistency_auditor.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

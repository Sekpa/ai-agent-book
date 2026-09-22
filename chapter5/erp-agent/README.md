# 把自然语言问题变成数据库查询

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

用户问“研发部有多少在职员工”，系统需要理解业务词汇，并在数据库中执行精确查询。本实验让模型生成 SQL，再把执行和结果核对交给数据库与检查程序。

## 理解实验

模型产出的是查询语句，而不是凭记忆编造数据行。数据库执行语句后返回真实结果。正确理解“在职”“部门”等概念，需要同时知道表结构、字段取值和业务条件。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线参考查询，理解样例数据库与十个问题。任选一题手工解释 SQL 中的筛选条件，再配置模型生成对应查询。对照参考结果，检查差异来自表连接、筛选还是聚合。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py gold
```

## 怎样解释结果

语法正确的 SQL 仍可能回答错问题。空结果也不一定代表没有数据，可能是条件写错。练习应使用样例数据库，并保留查询文本供核对。

## 继续思考

如果模型查到了正确数量，却使用了错误的业务定义，这个结果能否接受？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/erp-agent/demo.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/erp-agent/agent.py) → [gold.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/erp-agent/gold.py) → [seed.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/erp-agent/seed.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

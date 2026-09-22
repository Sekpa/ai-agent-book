# 把成功浏览器操作转成可验证工作流

[本章实验目录](../README.md) · [相关正文](../../book/chapter9.md) · [技术参考](REFERENCE.md)

一次网页任务成功后，能否把路径保存起来，下次更快完成？本实验学习从探索轨迹提炼工作流，并在页面变化时判断旧流程是否仍有效。

## 理解实验

首次成功只生成候选流程。重置环境后，流程需要重新执行，每一步都检查状态，最终再检查任务结果。页面变化使检查失败时，应停止复用并重新探索，而不是盲目继续点击。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行离线生命周期演示，观察候选、已验证与失效三个状态如何转换。再按技术参考准备本地浏览器样例，重放同一流程，并修改一个页面条件检查失效处理。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python workflow_validation_demo.py
```

## 怎样解释结果

离线演示解释状态管理，真实浏览器验证还要检查实际页面和动作。缓存一个成功轨迹并不等于已经拥有稳健自动化，关键在于复用前后的可检查条件。

## 继续思考

工作流的参数与固定步骤应该怎样区分，才能既能复用又不误操作其他对象？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[workflow_validation_demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/browser-use-rpa/workflow_validation_demo.py) → [run_experiment_9_5.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter9/browser-use-rpa/run_experiment_9_5.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 从失败轨迹寻找最早失去依据的决策

[本章实验目录](../../README.md) · [相关正文](../../../book/chapter7.md) · [技术参考](REFERENCE.md)

任务失败的最后一步往往只是后果，真正的问题可能更早就出现了。本实验使用已有 AndroidWorld 日志，学习把可观察事实、原因假设和回归用例连接起来。

## 理解实验

失败归因先还原每轮观察与动作，再寻找最早不被证据支持的决定。环境初始化失败、工具执行错误和模型判断错误应分开。无法从日志区分的原因，应保留不确定性。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行解析命令得到逐回合记录，选一条任务从头读到结束。在看到最终判断前先标记可疑步骤，再与已有归因记录比较。最后查看轨迹前缀用例，理解怎样把错误前的状态变成可重复检查。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python extract_trajectories.py --log ../t3a_failed.md --out tutorial-trajectories.json
```

## 怎样解释结果

模型声明完成而验证器判失败，提示我们不能只搜索日志中的报错关键词。归因还可能随着复核修正，应保留支持每个判断的具体轮次。

## 继续思考

如果日志不足以判断是页面没有更新还是模型看错，下一次运行应该增加什么观察？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[extract_trajectories.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/android-world/failure-attribution/extract_trajectories.py) → [attribution_records.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/android-world/failure-attribution/attribution_records.json) → [regression_prefixes.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/android-world/failure-attribution/regression_prefixes.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

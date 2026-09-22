# 把模型服务性能拆成可解释的指标

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

“这个模型很快”可能指首字出现快，也可能指整段输出完成快。本实验在不同输入与输出长度下测量服务表现，学习避免用一个延迟数字概括全部体验。

## 理解实验

首词元延迟、输出速度、总耗时和吞吐量描述不同现象。并发和负载还会改变表现，因此工作负载应明确固定。失败请求也应保留，否则结果可能只反映顺利完成的部分。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读配置中的输入长度、输出长度与请求次数，选择一个小规模工作负载检查流程。配置对应服务后运行，再查看单次请求记录。确认计时含义后，才扩展到完整矩阵与受控负载比较。

## 怎样解释结果

短输入下的领先未必适用于长上下文。服务限额、重试和时间段也会影响结果，应与模型名称一起记录。用于调通接口的小样本不能作为稳定性能结论。

## 继续思考

聊天应用与批量离线分析更应优先关注哪种延迟或吞吐指标？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[campaign_config.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/model-benchmark/campaign_config.json) → [campaign.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/model-benchmark/campaign.py) → [analysis.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/model-benchmark/analysis.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

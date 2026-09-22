# 从两两比较构建相对排名

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

评价生成答案时，人们有时更容易判断两者谁更好，而不是分别给出绝对分数。本实验从两两偏好数据出发，学习怎样估计相对能力以及排名的不确定性。

## 理解实验

Elo 根据对局结果逐步调整分数，Bradley–Terry 模型用胜率关系估计相对强度。两者都依赖比较数据覆盖；很少交手的模型，其排名通常更不稳定。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读 CLI 中的离线演示入口，用小规模比较理解胜负如何改变分数。随后按技术参考准备公开投票数据，比较不同估计方式，并用重采样观察排名区间。

## 怎样解释结果

分数差不是绝对能力差，排名也会随任务分布和投票者偏好变化。应检查比较图是否连通、样本是否均衡，以及相邻名次是否有足够证据区分。

## 继续思考

两个模型的排名区间大量重叠时，榜单应该怎样呈现这种不确定性？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[cli.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/elo-leaderboard/cli.py) → [elo_rating.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/elo-leaderboard/elo_rating.py) → [bradley_terry.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/elo-leaderboard/bradley_terry.py) → [data_loader.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/elo-leaderboard/data_loader.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

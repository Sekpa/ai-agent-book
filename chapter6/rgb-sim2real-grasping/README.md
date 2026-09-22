# 通过视觉扰动研究跨环境泛化

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

训练图片与实际相机画面常有背景、光照和噪声差异。本实验用可控的视觉训练与测试环境，学习扩大训练变化范围是否能减少这种分布差异。

## 理解实验

训练阶段改变图像条件，测试阶段使用不同环境，比较策略在未见变化下的表现。训练数据更丰富可能提升适应性，也可能增加学习难度；需要在相同测试条件下比较。

## 动手之前

训练需要独立的数据与计算环境。先按技术参考核对数据准备、模型版本与硬件要求；第一次练习只检查少量样本和一个短流程。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先查看图像生成与标签定义，列出训练和测试之间改变的因素。按技术参考准备计算环境，运行一个小规模流程，确认样本与预测对应，再扩展到多种训练条件和随机种子。

## 怎样解释结果

这是跨环境视觉学习的代理实验，不是真机零样本抓取验证。评估应关注未见环境表现，不能只看训练集损失下降。

## 继续思考

哪些随机变化接近真实相机差异，哪些可能改变任务本身、让训练标签不再成立？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[pipeline.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/rgb-sim2real-grasping/pipeline.py) → [preflight.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/rgb-sim2real-grasping/preflight.py) → [validate_evidence.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/rgb-sim2real-grasping/validate_evidence.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 用可替换模型运行截图操作循环

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

理解 Computer Use 后，可以进一步问：如果换一个视觉模型，哪些部分需要改变？本实验把模型接入与浏览器执行分开，便于观察协议兼容与实际操作能力的区别。

## 理解实验

模型接收截图并返回结构化动作，浏览器执行后产生新的观察。兼容接口让模型更容易替换，但动作格式、坐标理解和任务规划仍需要逐项检查。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先按技术参考安装浏览器依赖，运行 dry-run 查看任务配置。再接入所选模型，在不登录、不修改外部数据的查询任务上观察每轮截图与动作。保留视频有助于定位等待或重复操作。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --dry-run
```

## 怎样解释结果

dry-run 只检查准备路径，不证明模型可以操作页面。真实运行应检查动作合法性、页面状态和答案来源；接口可调用也不等于模型理解了目标。

## 继续思考

如果换模型后点击经常偏移，应先检查图像缩放、坐标约定还是任务提示？怎样逐项排除？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/computer-use-open-model/main.py) → [config.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/computer-use-open-model/config.py) → [evidence.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/computer-use-open-model/evidence.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 为语音合成建立多维评价

[本章实验目录](../README.md) · [相关正文](../../book/chapter7.md) · [技术参考](REFERENCE.md)

一段合成语音可能文字准确，却不自然；也可能声音悦耳，却漏掉词句。本实验把多家服务和不同配置放在同一文本集上，学习怎样分开评价这些维度。

## 理解实验

客观测量与主观评分各有作用。时长、可懂度相关指标和风格评价需要对应明确标准，模型裁判也应检查是否真的依据音频，而不是只根据文本猜测。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读评分表，选一段包含停顿和数字的短文本，人工说明怎样才算读对。按技术参考配置一条合成路径，试听并评分，再在另一配置上使用同一文本比较。

## 怎样解释结果

音量、采样率和播放条件会影响听感。比较服务时应尽量保持这些条件一致，并保留单项分数，避免总分掩盖严重漏读。

## 继续思考

导航播报、有声书与客服回复，是否应该使用同样的评分权重？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/tts-quality-eval/demo.py) → [pipeline.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/tts-quality-eval/pipeline.py) → [config.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter7/tts-quality-eval/config.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

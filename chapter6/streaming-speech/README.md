# 用递增音频前缀观察感知如何变化

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

一句话还没说完时，语音系统可能已经得到部分信息。本实验逐渐扩大音频前缀，观察转写与声学判断怎样随新片段变化，并与等待端点后再识别的路径比较。

## 理解实验

这里每次把从开头到当前时刻的音频重新送入模型，属于递增前缀的模拟方式。它能研究何时得到有用信息，但会重复编码，不能直接当作具有持续内部状态的原生流式实现。

## 动手之前

本节需要本地模型或服务。先按技术参考确认模型文件、运行后端与内存或显存要求，再进行下面的练习。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先听完整样例并阅读参考转写，再按技术参考准备本地音频模型。选择正常、长停顿或背景噪声中的一种场景，逐个前缀查看输出，记录第一次正确判断出现在什么位置。

## 怎样解释结果

部分转写后来可能被修正；越早输出不一定越准确。比较时同时看文字错误率、单次处理时间和停止判断，尤其检查长停顿是否造成错误分段。

## 继续思考

如果前缀越长处理越慢，怎样区分模型本身的实时能力与反复重编码带来的开销？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[qwen2_streaming.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/streaming-speech/qwen2_streaming.py) → [whisper_baseline.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/streaming-speech/whisper_baseline.py) → [interruption_manager.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/streaming-speech/interruption_manager.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/streaming-speech/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

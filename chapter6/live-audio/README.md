# 搭建语音识别、对话与语音合成的级联链路

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

语音对话需要先判断用户是否说完，再识别文字、生成回复并播放声音。本实验把这些步骤串成实时应用，帮助你定位一次对话的延迟与错误分别来自哪里。

## 理解实验

VAD 判断语音片段边界，ASR 把音频转成文字，LLM 处理对话，TTS 生成回复音频。级联方式便于分别替换模块，但前面丢失的信息通常难以由后面补回，例如停顿中的语气。

## 动手之前

本项目包含前端和后端。先按技术参考分别安装依赖、配置服务地址并启动两端，再通过浏览器观察交互。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

按技术参考分别安装 Node 前后端依赖，配置所选服务，启动后在浏览器授权麦克风。先说一句短句，逐步观察识别文字、模型回复和音频播放。再加入停顿，检查系统是否过早认为你已经说完。

## 怎样解释结果

把录音结束到识别完成、识别完成到回复、回复到开始播放的等待分开。总延迟高并不一定是模型慢；音频分段与网络传输也可能是主要原因。

## 继续思考

用户在播放期间开始说话时，哪些模块应停止，哪些状态应该保留？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[backend/server.js](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/live-audio/backend/server.js) → [backend/config.js](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/live-audio/backend/config.js) → [frontend/package.json](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/live-audio/frontend/package.json)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

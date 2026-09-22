# 从浏览器音频完成一次语音任务

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

语音 Agent 不应只读取文字模拟用户说话。本项目通过本地浏览器 WebRTC 通话，把麦克风音频送到识别、对话与合成模块，再将回复音频送回浏览器。

## 理解实验

音频链路承载用户说的话，字幕只用于展示。把这两条通道分清，才能知道系统是否真正处理了声音。任务完成还需要用户确认关键内容，而不是模型自己宣布已经安排好。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

按技术参考准备识别模型、TTS 与对话服务后，启动本地演示并在浏览器加入通话。先回答一个时间或确认信息，观察识别文本与实际声音是否一致，再听模型如何复述并请求确认。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py
```

## 怎样解释结果

检查音频收发、识别和任务状态三个层次。字幕正确但没有音频传输，不能证明通话链路完整；模型听错后得到的确认，也可能让错误进入任务结果。

## 继续思考

用户更正刚才说的时间时，系统应怎样更新状态并确认新值？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/phone-agent/demo.py) → [webrtc_app.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/phone-agent/webrtc_app.py) → [speech.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/phone-agent/speech.py) → [agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/phone-agent/agent.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

# 用控制标记表达语气、速度与风格

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

相同一句话可以用不同语气说出，服务场景也可能要求不同速度。本实验把文本中的控制意图映射到参考语音，观察可控语音合成的实现方式。

## 理解实验

控制标记先被解析成情绪、语速和风格，再用于选择参考音频。合成模型根据文本与参考生成声音。标记解析正确与听感符合要求是两层验证，不能只检查输出文件是否存在。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读标记格式与参考库的组织方式，按技术参考准备你拥有或获准使用的参考声音。选择同一句文本，只改变一个控制维度，生成后并排试听，再检查另外两个维度是否保持稳定。

## 怎样解释结果

情绪变化不应改变文字内容；语速变化也不应严重损害可懂度。应结合听感与音频测量，不能把文件时长变化直接等同于风格控制成功。

## 继续思考

如果表达更有情绪却更难听清，如何根据任务决定这种变化是否值得保留？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[markup.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/controllable-tts/markup.py) → [voice_library.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/controllable-tts/voice_library.py) → [tts.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/controllable-tts/tts.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/controllable-tts/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

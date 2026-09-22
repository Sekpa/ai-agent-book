# 比较直接理解音频与先转成文字

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

两段语音可以说完全相同的字，却有不同语速或表达方式。先转成文字的系统可能丢掉这些信息。本实验让同一个模型分别直接读取音频和只读取自己的转写。

## 理解实验

两条路径尽量保持模型一致，只改变进入问答阶段的信息形式。语义题主要依赖字面内容，副语言题还依赖声音特征。这样的对照有助于判断音频输入究竟增加了什么信息。

## 动手之前

本节需要本地模型或服务。先按技术参考确认模型文件、运行后端与内存或显存要求，再进行下面的练习。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先查看样例中的算术题与快慢语速对照，写下哪些问题仅凭文字就能回答。按技术参考准备本地模型，再分别运行两条路径，对照音频、转写和最终答案。

## 怎样解释结果

直接音频路径更好时，要确认不是转写错误造成差距。文本相同但语速不同的案例尤其适合观察声音信息。音频生成检查是另一项能力，不应与输入理解混为一个分数。

## 继续思考

如果模型能识别语速却不能据此调整回复，说明感知与决策之间还缺少什么？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[speech_model.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/end-to-end-speech/speech_model.py) → [prepare_fixtures.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/end-to-end-speech/prepare_fixtures.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/end-to-end-speech/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

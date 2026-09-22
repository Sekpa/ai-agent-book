# 在保护敏感信息的同时保留可诊断日志

[本章实验目录](../README.md) · [相关正文](../../book/chapter3.md) · [技术参考](REFERENCE.md)

日志能帮助定位错误，也可能包含账号、联系方式或凭据。本实验学习怎样识别并替换敏感字段，同时让剩余信息仍足以解释程序发生了什么。

## 理解实验

规则方法适合格式稳定的字段，模型方法可以利用上下文识别更复杂的信息。脱敏需要同时考虑漏检和过度删除：只追求遮盖得多，可能让错误时间、调用关系或状态信息也无法使用。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先运行规则脱敏示例，逐项对照输入与输出中的替换位置。使用人工构造的样例增加一种格式变化，再检查规则能否识别。需要比较模型方法时，按技术参考准备本地模型，继续使用同一组样例。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python regex_sanitizer.py
```

## 怎样解释结果

检查敏感值是否仍能从其他字段推断出来，也检查排查错误所需的信息是否保留。示例上的高分不代表真实日志中所有敏感类型都已覆盖。

## 继续思考

同一个用户标识多次出现时，怎样替换才能既保护身份，又保留跨行关联？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[regex_sanitizer.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/log-sanitization/regex_sanitizer.py) → [metrics.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/log-sanitization/metrics.py) → [samples.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter3/log-sanitization/samples.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

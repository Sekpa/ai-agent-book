# 提示词改写会让生成图片更符合需求吗

[本章实验目录](../README.md) · [相关正文](../../book/chapter1.md) · [技术参考](REFERENCE.md)

用户说“画一张耳机海报”，与明确指定画面、风格和文案，是两种不同的任务。本实验比较直接生成图片和先改写提示词再生成图片，学习如何判断一个工作流步骤是否真正有帮助。

## 理解实验

改写节点把用户语言转成图像模型的输入，也可能补充场景细节。对于宽泛需求，这可能有助于形成画面；对于具体需求，多加的内容却可能挤掉用户的原始约束。因此，应分别评价创意补充和要求保留。

## 动手之前

运行模型部分需要按技术参考配置对应的服务凭据；调用会使用该服务的额度。先准备一个小任务，再扩展比较范围。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

配置参考文档中对应路线的模型凭据后，先只选 `windowsill-plant` 这一项。运行后并排阅读原始需求、改写后的提示词和最终图片。再选择一个宽泛需求，重复同样的观察，避免一开始就批量生成所有图片。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python main.py --requirement windowsill-plant
```

## 怎样解释结果

检查窗台、绿植和晨光是否同时出现，而不只判断图片是否漂亮。如果某个要求消失了，先查它是否在改写时丢失；若提示词仍保留它，再分析图像生成阶段。不同路线使用的模型也不同，结果不能全部归因于是否改写。

## 继续思考

怎样设计一个既奖励合理补充、又惩罚擅自修改明确要求的评分表？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[main.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/image-gen-workflow/main.py) → [pipeline.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/image-gen-workflow/pipeline.py) → [evidence.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/image-gen-workflow/evidence.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

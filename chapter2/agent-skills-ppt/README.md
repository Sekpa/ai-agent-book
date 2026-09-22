# 按需加载 Skill：从论文到演示文稿

[本章实验目录](../README.md) · [相关正文](../../book/chapter2.md) · [技术参考](REFERENCE.md)

生成演示文稿既需要理解论文，也需要掌握幻灯片文件的制作方法。把全部操作说明一直放在提示词中会占用上下文。本实验借助 PPTX Skill，学习如何在任务需要时才加载具体知识。

## 理解实验

Skill 可以先暴露简短说明，再在被选中时提供操作步骤和辅助资源。这种渐进式加载把“发现能力”和“执行能力”分开。先用本地示例看文件如何生成，再在支持 Skill 的运行时中观察它何时读取说明。

## 动手之前

本节先使用本地示例或已有数据，不需要模型 API Key。安装依赖仍可能需要联网。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

下方命令只根据示例材料生成幻灯片，不调用模型。先打开生成文件，了解输出格式。随后按技术参考准备真实论文和固定版本的 Skill，在所选运行时中完成论文到幻灯片的过程，并查看读取 Skill 的轨迹。

以下命令从本实验目录运行；请先完成上面的环境准备。

```bash
python demo.py --offline
```

## 怎样解释结果

本地示例能说明 PPTX 文件的生成路径，但不能证明模型自主选择了 Skill。真实运行应分别检查论文内容是否正确、图表是否清晰、文件是否能打开，以及 Skill 是否按需加载。内容质量和工具使用行为是两组不同的观察。

## 继续思考

如果模型每次都加载全部参考材料，Skill 的目录结构还带来了多少上下文节省？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/agent-skills-ppt/demo.py) → [run_official_experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/agent-skills-ppt/run_official_experiment.py) → [prepare_official_skill.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter2/agent-skills-ppt/prepare_official_skill.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

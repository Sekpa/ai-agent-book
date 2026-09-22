# 选择代码建模还是直接生成三维形状

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

一个有精确孔径的法兰盘，与一盆形态自然的绿植，对三维生成提出了不同要求。本实验比较参数化 CAD 代码与直接生成形状的路线，学习任务约束怎样影响技术选择。

## 理解实验

CAD 用尺寸和几何关系表达结构，适合可测量的约束与局部修改。生成模型更便于产生外观形态，但未必准确满足每个机械尺寸。比较时需要把几何合规与视觉自然程度分开。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先读法兰盘规格，列出外径、厚度、孔径和孔位等检查项。按技术参考准备两条路线后生成同一对象，用测量程序检查结果。再提出一次单独的尺寸修改，观察两条路线如何保留其他约束。

## 怎样解释结果

渲染图看起来相似，不等于模型尺寸相同；测量前应核对单位。反过来，几何尺寸准确也不足以说明自然物体外观好。结论应与具体任务类型绑定。

## 继续思考

用户同时要求自然外观和可制造接口时，能否把两条路线组合起来？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[flange_spec.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/cad-vs-diffusion/flange_spec.py) → [route_a_codegen.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/cad-vs-diffusion/route_a_codegen.py) → [route_b_gen3d.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/cad-vs-diffusion/route_b_gen3d.py) → [measure.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/cad-vs-diffusion/measure.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

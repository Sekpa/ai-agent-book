# 用模拟专家控制建立比较基线

[本章实验目录](../README.md) · [相关正文](../../book/chapter6.md) · [技术参考](REFERENCE.md)

评价自主操作策略之前，需要知道同一任务在理想控制下能做到什么。本项目先用桌面模拟器建立专家控制基线，再说明它与真实遥操作的关系。

## 理解实验

模拟控制器可以直接把物体移到目标，减少感知与执行的不确定性。它因此适合提供受控上限，但不包含真机的摩擦、标定误差或动作延迟。比较时必须说明哪些困难被模拟环境简化了。

## 动手之前

先在模拟或回放路径中理解流程。真实设备的连接、标定与运行条件见技术参考，模拟结果与真机结果应分别解释。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读桌面状态与目标定义，跟踪一个物体从初始位置到目标的变化。按技术参考运行少量模拟回合，再增加物体数量，观察成功条件与步数如何改变。真机入口需要独立完成设备准备。

## 怎样解释结果

这里的模拟结果不能作为真机遥操作成绩。应检查上限是否来自专家已知的状态信息，以及自主策略能否获得同等观察。

## 继续思考

如果专家控制器知道物体的精确坐标，而自主策略只能看图像，这个比较应怎样解释？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[teleop.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/xlerobot-teleoperation/teleop.py) → [preflight.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/xlerobot-teleoperation/preflight.py) → [validate_evidence.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter6/xlerobot-teleoperation/validate_evidence.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

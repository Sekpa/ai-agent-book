# 把剪辑意图转成可以检查的操作

[本章实验目录](../README.md) · [相关正文](../../book/chapter5.md) · [技术参考](REFERENCE.md)

“保留人物走进房间的那一段”包含视觉定位与时间范围选择。直接生成剪辑命令之前，Agent 必须先理解视频内容。本实验展示从自然语言需求到场景定位，再到媒体处理的过程。

## 理解实验

视觉分析负责找出相关片段，代码负责执行裁剪或变速，审核环节检查结果。这样可以把“找错场景”与“剪辑参数错误”分开定位。不同输出工具的时间单位与边界规则也需要对应。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先查看示例视频并手工记录目标场景的大致起止时间，再按技术参考准备 ffmpeg 或 Blender 路径。运行一个简单裁剪任务，比较模型定位、生成操作与实际成片；之后再尝试多步骤编辑。

## 怎样解释结果

检查是否漏掉动作开头或结尾、音轨是否同步、变速是否改变了用户要求的含义。视觉定位误差不会因为执行工具准确而自动消失。

## 继续思考

如果每段剪辑都正确，拼接后的叙事却难以理解，还需要加入哪一类审核？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[agents.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/video-edit/agents.py) → [video_editor.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/video-edit/video_editor.py) → [ffmpeg_utils.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/video-edit/ffmpeg_utils.py) → [demo.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/video-edit/demo.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

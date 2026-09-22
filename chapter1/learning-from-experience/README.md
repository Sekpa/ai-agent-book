# 在寻宝游戏中比较两种学习方式

[本章实验目录](../README.md) · [相关正文](../../book/chapter8.md) · [技术参考](REFERENCE.md)

面对规则不完全公开的寻宝游戏，Agent 必须从行动后果中学习。本项目把表格型 Q-learning 与 LLM 的上下文学习放在同一游戏中，帮助你区分“更新参数”和“把经验留在输入中”。

## 理解实验

Q-learning 用多次交互更新状态与动作的价值；LLM 则可以阅读行动历史，提出关于游戏规则的解释，并据此选择下一步。二者使用的先验知识、训练投入和记忆形式不同，不能只比较一局游戏的分数。

## 动手之前

本项目有多条运行路径。先按下文确定要观察的机制，再使用技术参考中对应的环境、数据与命令，避免混用不同路径的配置。 通用环境说明见[实验学习指南](../../docs/EXPERIMENTS.md)。

## 一步步观察

先阅读游戏环境中的状态、动作与奖励定义，再用参考文档中的本地 Q-learning 路径观察训练前后的行为。随后配置 LLM 路径，跟踪一局中的观察如何改变下一步选择。本目录位于第一章项目树，相关学习实验的正文在第八章。

## 怎样解释结果

重点记录是否找到目标、用了多少步，以及遇到新规则后如何调整。某次 LLM 很快成功，不代表它在所有地图上都更优；Q-learning 在熟悉地图上表现稳定，也不等于能直接适应新规则。比较时应保持地图分布与评估预算清楚。

## 继续思考

如果把学到的经验从 LLM 上下文中删掉，和重置 Q 表，分别会消除什么能力？

## 阅读代码与技术参考

沿下面的顺序阅读代码，可以把前面的概念与实现对应起来：[game_environment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/learning-from-experience/game_environment.py) → [rl_agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/learning-from-experience/rl_agent.py) → [llm_agent.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/learning-from-experience/llm_agent.py) → [experiment.py](https://github.com/bojieli/ai-agent-book/blob/main/chapter1/learning-from-experience/experiment.py)。

原有说明保存在[技术参考](REFERENCE.md)中。需要查阅详细配置、英文材料或历史记录时，请从这里继续，并核对记录所使用的数据、模型与环境条件。

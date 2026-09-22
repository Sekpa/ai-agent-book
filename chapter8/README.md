# 第 8 章 · 模型后训练

[读本章正文](../book/chapter8.md) · [实验学习指南](../docs/EXPERIMENTS.md)

本章把经验写入模型参数。学习重点是数据、训练目标与独立评估之间的关系；训练脚本正常结束，并不自动说明能力提高。

## 建议的学习顺序

1. [用偏好对训练更可靠的完成判断](premature-completion-dpo/README.md)：先用离线偏好对理解训练希望改变的行为。
2. [从教师轨迹构造学生训练数据](cot-distillation/README.md)：再检查教师轨迹怎样成为可用的监督数据。
3. [从小模型理解预训练与后训练的分工](MiniMind-pretrain/README.md)：最后结合小模型比较预训练、监督微调和偏好训练的分工。

## 配套项目

| 编号 | 项目 | 类型 | 学习内容 |
| :--: | --- | :--: | --- |
| 8-1, 8-2 | [在寻宝游戏中比较两种学习方式](../chapter1/learning-from-experience/README.md) | ✅ | 面对规则不完全公开的寻宝游戏，Agent 必须从行动后果中学习。 |
| 8-3 | [从小模型理解预训练与后训练的分工](MiniMind-pretrain/README.md) · `MiniMind-pretrain/minimind/` | ✅ | 把模型规模缩小后，更容易完整观察数据如何进入训练、损失怎样计算、不同训练阶段怎样改变输出。 |
| 8-4 | [从小模型理解预训练与后训练的分工](MiniMind-pretrain/README.md) | ✅ | 把模型规模缩小后，更容易完整观察数据如何进入训练、损失怎样计算、不同训练阶段怎样改变输出。 |
| 8-5 | [比较学习文本分布与学习指令回答](continued-pretraining/README.md) | ✅ | 让模型适应一种语言，既涉及理解该语言的文本，也涉及按指令完成任务。 |
| 8-6 | [通过对齐数据学习语音表达](sesame/README.md) · [orpheus](orpheus/README.md) | ✅ | 除了读出文字，语音模型还可能需要表达笑声、叹息等事件。 |
| 8-7 | [让语言控制与任务正确性分别可测](MultilingualReasoning/README.md) | 🚧 | 用户希望模型用某种语言解释思路，但语言符合要求并不意味着解题正确。 |
| 8-8 | [把长提示词中的行为转成训练样例](../chapter8/prompt-distillation/README.md) | ✅ | 一个长提示词可能稳定引导模型完成任务，但每次请求都携带它会增加成本。 |
| 8-9 | [从教师轨迹构造学生训练数据](cot-distillation/README.md) | ✅ | 教师模型的回答可能包含有用步骤，也可能包含错误或冗余。 |
| 8-10 | [学习何时值得投入更多推理](AdaptThink/README.md) · `AdaptThink-original/` | ✅ | 简单问题可能不需要很长的推理，而困难问题可能从额外计算中受益。 |
| 8-11 | `SFTvsRL/` | 📖 | 在相同任务条件下比较监督微调与强化学习的分布内外表现。 |
| 8-12 | [比较不同训练方法的跨环境表现](SpatialReasoning/README.md) · `SFTvsRL/` | 📖 | 导航策略在熟悉街景中表现好，未必能适应另一座城市。 |
| 8-13 | [让视觉动作策略从交互结果中学习](SimpleVLA-RL/README.md) · `SimpleVLA-RL/SimpleVLA-RL/` | 📖 | 机器人动作模型从示范中学习后，仍可能在实际闭环中犯错。 |
| 8-14 | [在训练过程中学习何时调用代码工具](retool/README.md) · `verl/` · `SandboxFusion/` | 📖 | 模型知道怎样写代码，不一定知道何时值得调用工具。 |
| 8-15 | [把多步 Agent 环境接入训练](AWorld-train/README.md) · `AWorld/` | 📖 | 搜索、读取资料和调用工具组成的长任务，需要把环境状态与模型采样连接起来。 |
| 8-16 | [同时评价结果与取得结果的路径](RLVP/README.md) · `RLVP/rlvp/` | 📖 | 只奖励最终答案，可能鼓励策略采用不符合要求的过程。 |
| 8-17 | [用偏好对训练更可靠的完成判断](premature-completion-dpo/README.md) | ✅ | 编码 Agent 可能没有运行检查就宣布完成。 |
| 8-18 | [学习只在合适的语境中修改引号](curly-quote-sft/README.md) | ✅ | 中文正文通常使用弯引号，但代码和 JSON 中的引号承担语法作用。 |
| 8-19 | [区分精确复制与语义相似](exact-copy-sft/README.md) | ✅ | 编辑工具要求待替换字符串逐字匹配，而模型可能改动空格、引号或不可见字符。 |
| — | `verl/` | 📖 | 了解模型采样、奖励计算与策略更新怎样组成强化学习训练流程。 |
| — | [用内部反馈训练时怎样避免自信替代正确](Intuitor/README.md) | ✅ | 通常奖励来自答案校验或外部评价。 |
| — | `tinker-cookbook/` | 📖 | 按具体训练任务查阅环境准备与实践示例。 |

✅ 表示仓库提供实现入口；📖 表示需要按指南准备外部项目；🚧 表示按正文开展的设计练习。即使有实现入口，模型、数据、浏览器或硬件仍可能需要单独准备。

## 从演示走向完整实验

先选一项实验，读清楚输入、预期观察和结果解释，再准备该项目的环境。能解释一次运行后，再扩大任务数量或比较不同配置。不要把离线示例、真实模型运行和硬件结果混为同一种证据。

各实验的 README 是教学入口。完整配置、英文资料与历史结果保留在对应的技术参考文档中；本章的原始目录、外部项目版本与运行记录可在[章节技术参考](REFERENCE.md)中查阅。

<details>
<summary>获取外部代码：按所选项目查阅</summary>

下面的命令从本书仓库根目录执行，用于获取本章使用的外部源码版本。只执行你所选项目的部分；安装与运行条件见章节技术参考。

```bash
git clone https://github.com/bojieli/AdaptThink.git chapter8/AdaptThink-original && git -C chapter8/AdaptThink-original checkout --detach 0033ad172dd53ac64004b763477407014f21b838
git clone https://github.com/bojieli/SFTvsRL.git chapter8/SFTvsRL && git -C chapter8/SFTvsRL checkout --detach fef0a4a3367260a0934be1e40b01e4021698e023
git clone https://github.com/PRIME-RL/SimpleVLA-RL.git chapter8/SimpleVLA-RL/SimpleVLA-RL && git -C chapter8/SimpleVLA-RL/SimpleVLA-RL checkout --detach 7c51662df27b586f9e8a1ab35fcf849f2b8852f9
git clone https://github.com/bojieli/verl.git chapter8/verl && git -C chapter8/verl checkout --detach 1593fc3a8cf894debdc3dece2a23ed739c282789
git clone https://github.com/bojieli/AWorld.git chapter8/AWorld && git -C chapter8/AWorld checkout --detach a52d61d6d483e66b22ef16970eae5bbf4f4ab2ec
```

```bash
git clone https://github.com/bojieli/minimind.git chapter8/MiniMind-pretrain/minimind
git -C chapter8/MiniMind-pretrain/minimind fetch origin 8bdc5d97d5845a8c1ac2ed56a5b8b4c0d0fb0795
git -C chapter8/MiniMind-pretrain/minimind checkout --detach 8bdc5d97d5845a8c1ac2ed56a5b8b4c0d0fb0795
git -C chapter8/MiniMind-pretrain/minimind rev-parse HEAD
test "$(git -C chapter8/MiniMind-pretrain/minimind rev-parse HEAD)" = "8bdc5d97d5845a8c1ac2ed56a5b8b4c0d0fb0795"

git clone https://github.com/bojieli/minimind-v.git chapter8/MiniMind-pretrain/minimind-v
git -C chapter8/MiniMind-pretrain/minimind-v fetch origin ead791c530fa5f9a3549dbfe9e11ec732d18d2e5
git -C chapter8/MiniMind-pretrain/minimind-v checkout --detach ead791c530fa5f9a3549dbfe9e11ec732d18d2e5
git -C chapter8/MiniMind-pretrain/minimind-v rev-parse HEAD
test "$(git -C chapter8/MiniMind-pretrain/minimind-v rev-parse HEAD)" = "ead791c530fa5f9a3549dbfe9e11ec732d18d2e5"

git clone https://github.com/19PINE-AI/rlvp.git chapter8/RLVP/rlvp
git -C chapter8/RLVP/rlvp fetch origin 1ad30bc7e338911fb733739393d92c420f4d8bee
git -C chapter8/RLVP/rlvp checkout --detach 1ad30bc7e338911fb733739393d92c420f4d8bee
git -C chapter8/RLVP/rlvp rev-parse HEAD
test "$(git -C chapter8/RLVP/rlvp rev-parse HEAD)" = "1ad30bc7e338911fb733739393d92c420f4d8bee"

git clone https://github.com/bojieli/SandboxFusion.git chapter8/SandboxFusion
git -C chapter8/SandboxFusion fetch origin 4a0d573ebd64c98234c190a9d1d49e4276199a0c
git -C chapter8/SandboxFusion checkout --detach 4a0d573ebd64c98234c190a9d1d49e4276199a0c
git -C chapter8/SandboxFusion rev-parse HEAD
test "$(git -C chapter8/SandboxFusion rev-parse HEAD)" = "4a0d573ebd64c98234c190a9d1d49e4276199a0c"
```

</details>

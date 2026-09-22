# 第 7 章 · Agent 的评估

[读本章正文](../book/chapter7.md) · [实验学习指南](../docs/EXPERIMENTS.md)

本章学习如何把“表现好不好”转成可解释的比较。先理解环境与评分，再定位失败，最后检查模型、记忆和系统成本的不同维度。

## 建议的学习顺序

1. [在交互环境中评价客服 Agent](tau2-bench-eval/README.md)：先读一条交互任务，区分回答质量与环境目标。
2. [从失败轨迹寻找最早失去依据的决策](android-world/failure-attribution/README.md)：再用已有日志练习寻找最早失去依据的决策。
3. [计算一次完整任务的成本](agent-cost-analysis/README.md)：最后把成功条件、调用成本与延迟放在一起分析。

## 配套项目

| 编号 | 项目 | 类型 | 学习内容 |
| :--: | --- | :--: | --- |
| 7-1 | [在交互环境中评价客服 Agent](tau2-bench-eval/README.md) | ✅ | 客服回答看起来合理，后台状态却可能没有正确改变。 |
| 7-2 | [通过亲自走任务理解基准难度](experiment-7-2-human-benchmark/README.md) | ✅ | 只看基准总分，很难知道一道任务需要哪些操作。 |
| 7-2 | `terminal-bench/` | 📖 | 通过终端任务学习如何定义可执行的成功条件，案例入口见本章的基准任务体验。 |
| 7-2 | `SWE-bench/` | 📖 | 通过真实代码修复任务理解补丁、测试与问题描述之间的关系。 |
| 7-2 | `GAIA/` | 📖 | 通过需要查询与计算的任务，练习核对多步答案的证据链。 |
| 7-2 | `OSWorld/` | 📖 | 通过桌面任务理解屏幕观察、动作执行与最终状态检查。 |
| 7-2, 7-13 | `android_world/` | 📖 | 通过 Android 环境学习界面任务的目标、操作与验证。 |
| 7-3 | [评估系统是否真的用好了记忆](../chapter3/user-memory-evaluation/README.md) | ✅ | 记忆系统可能保存了正确事实，却在需要时找不到；也可能找到片段，却误解了指代。 |
| 7-4 | [对照记忆系统的完整处理链](user-memory-system-evaluation/README.md) | ✅ | 评价记忆系统时，只比较几段预先写好的回答无法反映实际存储与检索。 |
| 7-5 | [为语音合成建立多维评价](tts-quality-eval/README.md) | ✅ | 一段合成语音可能文字准确，却不自然；也可能声音悦耳，却漏掉词句。 |
| 7-6 | [从失败轨迹寻找最早失去依据的决策](android-world/failure-attribution/README.md) | ✅ | 任务失败的最后一步往往只是后果，真正的问题可能更早就出现了。 |
| 7-7 | [检查 Agent 是否正确使用已经看到的记忆](user-memory-policy-eval/README.md) | ✅ | 记忆找到了，仍可能被用错。 |
| — | [用合成报表数据练习可验证评价](public-health-reporting-eval/README.md) | ✅ | 报表 Agent 不仅要给出数字，还要说明数字来自哪些记录。 |
| 7-8 | [从两两比较构建相对排名](elo-leaderboard/README.md) | ✅ | 评价生成答案时，人们有时更容易判断两者谁更好，而不是分别给出绝对分数。 |
| 7-9 | [在固定工具环境中比较模型行动方式](model-action-threshold/README.md) | ✅ | 有的模型先大量阅读，有的模型很快开始改代码。 |
| 7-10 | [计算一次完整任务的成本](agent-cost-analysis/README.md) | ✅ | 模型单价较低，不一定意味着完成任务更便宜。 |
| 7-11 | [把模型服务性能拆成可解释的指标](model-benchmark/README.md) | 🚧 | “这个模型很快”可能指首字出现快，也可能指整段输出完成快。 |
| 7-12 | [对照记忆系统的完整处理链](user-memory-system-evaluation/README.md) | ✅ | 评价记忆系统时，只比较几段预先写好的回答无法反映实际存储与检索。 |
| 7-13 | [从界面任务失败提出可检验的改进](android-world/README.md) | ✅ | Android 操作中，一次点击失败可能来自观察错误、等待不足或目标识别不准。 |
| 7-14 | [在相同场景中比较动作分块策略](openvla-robotwin2-eval/README.md) | ✅ | 视觉动作模型可以一次预测一个动作，也可以预测一段动作。 |

✅ 表示仓库提供实现入口；📖 表示需要按指南准备外部项目；🚧 表示按正文开展的设计练习。即使有实现入口，模型、数据、浏览器或硬件仍可能需要单独准备。

## 从演示走向完整实验

先选一项实验，读清楚输入、预期观察和结果解释，再准备该项目的环境。能解释一次运行后，再扩大任务数量或比较不同配置。不要把离线示例、真实模型运行和硬件结果混为同一种证据。

各实验的 README 是教学入口。完整配置、英文资料与历史结果保留在对应的技术参考文档中；本章的原始目录、外部项目版本与运行记录可在[章节技术参考](REFERENCE.md)中查阅。

<details>
<summary>获取外部代码：按所选项目查阅</summary>

下面的命令从本书仓库根目录执行，用于获取本章使用的外部源码版本。只执行你所选项目的部分；安装与运行条件见章节技术参考。

```bash
git clone https://github.com/sierra-research/tau2-bench.git chapter7/tau2-bench && git -C chapter7/tau2-bench checkout --detach 8d005b0e5b9e4af0bc055886fa7f95fc86d1710e
git clone https://huggingface.co/datasets/gaia-benchmark/GAIA chapter7/GAIA && git -C chapter7/GAIA checkout --detach 682dd723ee1e1697e00360edccf2366dc8418dd9
git clone https://github.com/google-research/android_world.git chapter7/android_world && git -C chapter7/android_world checkout --detach 0e95d641e244504c22087cc29b013f3b2428a261
git clone https://github.com/SWE-bench/SWE-bench.git chapter7/SWE-bench && git -C chapter7/SWE-bench checkout --detach 5cd4be9fb23971679cbbafe5a0ecade27cef99be
git clone https://github.com/laude-institute/terminal-bench.git chapter7/terminal-bench && git -C chapter7/terminal-bench checkout --detach 8384a179b1b8688f6ea5233a4d9d51218df1ac96
git clone https://github.com/xlang-ai/OSWorld.git chapter7/OSWorld && git -C chapter7/OSWorld checkout --detach 8365edc975efd0477a0d62444a5beed562ab5a7b
```

</details>

# 第 6 章 · 交互：观察与动作空间的扩展

[读本章正文](../book/chapter6.md) · [实验学习指南](../docs/EXPERIMENTS.md)

本章同时扩展输入输出的模态与任务的时间结构。事件、语音、屏幕和机器人环境都要求系统区分观察、动作与完成状态。

## 建议的学习顺序

1. [让 Agent 响应定时器和外部事件](agent-with-event-trigger/README.md)：先用本地定时器理解事件怎样触发任务。
2. [在等待工具时继续处理其他工作](async-agent/README.md)：再观察等待、中断和恢复如何改变控制流程。
3. [搭建语音识别、对话与语音合成的级联链路](live-audio/README.md)：最后沿真实语音链路定位感知、决策与播放的延迟。

## 配套项目

| 编号 | 项目 | 类型 | 学习内容 |
| :--: | --- | :--: | --- |
| 6-1 | [让 Agent 响应定时器和外部事件](agent-with-event-trigger/README.md) | ✅ | Agent 不一定每次都由用户发一句话启动。 |
| 6-2 | [在等待工具时继续处理其他工作](async-agent/README.md) | ✅ | 一个工具调用需要很久时，Agent 是否必须完全停住？异步执行让系统同时管理多个未完成动作，还需要应对中途取消和恢复。 |
| 6-3 | [在模型运行中途更新任务条件](astra-async-steering/README.md) | ✅ | 模型已经开始挑选会议场地，用户又修改了人数或预算。 |
| 6-4 | [搭建语音识别、对话与语音合成的级联链路](live-audio/README.md) | ✅ | 语音对话需要先判断用户是否说完，再识别文字、生成回复并播放声音。 |
| 附加 | [从浏览器音频完成一次语音任务](phone-agent/README.md) | ✅ | 语音 Agent 不应只读取文字模拟用户说话。 |
| 6-5 | [用递增音频前缀观察感知如何变化](streaming-speech/README.md) | ✅ | 一句话还没说完时，语音系统可能已经得到部分信息。 |
| 6-6 | [比较直接理解音频与先转成文字](end-to-end-speech/README.md) | ✅ | 两段语音可以说完全相同的字，却有不同语速或表达方式。 |
| 6-7 | [用控制标记表达语气、速度与风格](controllable-tts/README.md) | ✅ | 相同一句话可以用不同语气说出，服务场景也可能要求不同速度。 |
| 6-8 | [通过截图与动作理解 Computer Use](claude-computer-use-native/README.md) + `claude-quickstarts/computer-use-demo/` | ✅ | 电脑操作 Agent 通过屏幕观察状态，再提出点击、输入等动作。 |
| 6-9 | [用可替换模型运行截图操作循环](computer-use-open-model/README.md) + `browser-use/` | ✅ | 理解 Computer Use 后，可以进一步问：如果换一个视觉模型，哪些部分需要改变？本实验把模型接入与浏览器执行分开，便于观察协议兼容与实际操作能力的区别。 |
| 6-10 | [用模拟专家控制建立比较基线](xlerobot-teleoperation/README.md) | ✅ | 评价自主操作策略之前，需要知道同一任务在理想控制下能做到什么。 |
| 6-11 | [用模拟专家控制建立比较基线](xlerobot-teleoperation/README.md) | ✅ | 评价自主操作策略之前，需要知道同一任务在理想控制下能做到什么。 |
| 6-12 | [比较执行前观察与执行后验证](gemini-xlerobot-navigation/README.md) | ✅ | 把杯子放进托盘，可能因为抓取失败而没有真正完成。 |
| 6-13 | [比较执行前观察与执行后验证](gemini-xlerobot-navigation/README.md) | ✅ | 把杯子放进托盘，可能因为抓取失败而没有真正完成。 |
| 6-14 | [通过视觉扰动研究跨环境泛化](rgb-sim2real-grasping/README.md) | ✅ | 训练图片与实际相机画面常有背景、光照和噪声差异。 |

✅ 表示仓库提供实现入口；📖 表示需要按指南准备外部项目；🚧 表示按正文开展的设计练习。即使有实现入口，模型、数据、浏览器或硬件仍可能需要单独准备。

## 从演示走向完整实验

先选一项实验，读清楚输入、预期观察和结果解释，再准备该项目的环境。能解释一次运行后，再扩大任务数量或比较不同配置。不要把离线示例、真实模型运行和硬件结果混为同一种证据。

各实验的 README 是教学入口。完整配置、英文资料与历史结果保留在对应的技术参考文档中；本章的原始目录、外部项目版本与运行记录可在[章节技术参考](REFERENCE.md)中查阅。

<details>
<summary>获取外部代码：按所选项目查阅</summary>

下面的命令从本书仓库根目录执行，用于获取本章使用的外部源码版本。只执行你所选项目的部分；安装与运行条件见章节技术参考。

```bash
git clone https://github.com/Vector-Wangel/XLeRobot.git chapter6/XLeRobot
git -C chapter6/XLeRobot fetch origin 3d14695e40c9c68229c0aacffca6053c75cd3eb6
git -C chapter6/XLeRobot checkout --detach 3d14695e40c9c68229c0aacffca6053c75cd3eb6
git clone https://github.com/Grigorij-Dudnik/RoboCrew.git chapter6/RoboCrew
git -C chapter6/RoboCrew fetch origin c749148f29bd14e61347f9fc3530c343fff0d994
git -C chapter6/RoboCrew checkout --detach c749148f29bd14e61347f9fc3530c343fff0d994
git clone https://github.com/StoneT2000/lerobot-sim2real.git chapter6/lerobot-sim2real
git -C chapter6/lerobot-sim2real fetch origin 87d6c1d969f6e0ca4dc5697940804e231118a63a
git -C chapter6/lerobot-sim2real checkout --detach 87d6c1d969f6e0ca4dc5697940804e231118a63a
```

```bash
git clone https://github.com/anthropics/claude-quickstarts.git chapter6/claude-quickstarts
git -C chapter6/claude-quickstarts checkout --detach 9bcc95e316e5ef6542b4c9d0469f4078829eead5
```

```bash
git clone https://github.com/browser-use/browser-use.git chapter6/browser-use
git -C chapter6/browser-use checkout --detach ec9277c5001f2cb78ee419c927775a3cfc227ff8
```

</details>

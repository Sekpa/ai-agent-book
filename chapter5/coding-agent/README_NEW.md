# 沿工具注册表理解编码 Agent

一个编码 Agent 如何把“查看项目文件”变成一次真实操作？本教程沿着工具定义、名称解析、函数执行和结果回传这条路径，阅读 `agent_new.py` 中的模块化实现。建议先读[实验入口](README.md)，理解模型与工具交替工作的基本循环。

## 先区分声明与执行

模型收到的工具定义描述名称、用途和参数，它本身不会执行 Python 函数。模型提出调用后，程序需要在注册表中找到对应实现，检查输入，执行操作，再把结果作为工具消息返回。名称一致只是第一步，返回值和错误处理也属于这个接口。

`tools.json` 提供模型可见的描述，`tool_registry.py` 负责连接工具实现，`system_state.py` 保存运行所需的状态。`agent_new.py` 组织这些部分；它是本目录的一条实现路线，阅读时应确认自己运行的是哪个入口。

## 跟踪一次调用

1. 在 `tools.json` 中选择一个读取文件的工具，写下它需要哪些参数、预期返回什么。
2. 在注册表中找到同名实现，检查相对路径依据哪个目录解析，以及文件不存在时如何处理。
3. 回到 Agent 循环，找到工具请求被分发的位置，沿返回路径确认结果如何进入下一轮消息。
4. 若准备实际运行，按照[技术参考](REFERENCE_NEW.md)安装依赖并配置模型，在临时目录放一个短文本，只请求读取该文件。对照代码观察请求、执行与回复。

## 判断接口是否清楚

最终回答正确并不足以证明工具链可靠。还应检查模型是否拿到了实际文件内容、异常是否成为可理解的反馈，以及工具是否只处理了请求中的路径。若增加一个新工具，需要同时考虑模型描述、执行实现和返回协议；只添加名称不能完成接入。

继续思考：两个工具都能读取文件，但一个返回文本，另一个返回结构化对象，Agent 循环需要如何处理这种差别？

源代码：[Agent 循环](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/agent_new.py)、[注册表](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/tool_registry.py)、[工具定义](https://github.com/bojieli/ai-agent-book/blob/main/chapter5/coding-agent/tools.json)。原有英文说明和完整接口清单见[技术参考](REFERENCE_NEW.md)。

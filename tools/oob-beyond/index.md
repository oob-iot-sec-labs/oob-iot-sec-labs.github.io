---
layout: default
title: "OOB Beyond（无界） | IoT 固件安全审计框架"
description: "OOB IoT Sec Labs 自研的 AI 辅助多 Agent IoT 固件安全审计框架，支持固件解包、二进制静态分析与报告生成。"
permalink: /tools/oob-beyond/
---

# OOB Beyond（无界）

**AI 辅助的多 Agent IoT 固件安全审计框架**

OOB Beyond 由 OOB IoT Sec Labs 开发，面向嵌入式系统、固件、文件系统和二进制安全研究。项目结合 LLM、LangGraph、Binwalk 和 Ghidra，将固件导入、解包、攻击面发现、静态扫描与报告生成组织为交互式审计流程。

当前版本为 **0.1.0-beta.1**，处于内测阶段。本页能力说明同步于 2026-10-28，最新版本、安装步骤与开发进展以仓库文档为准。

<p><a href="https://github.com/oob-iot-sec-labs/OOB-Beyond">查看 GitHub 仓库 →</a> · <a href="https://github.com/oob-iot-sec-labs/OOB-Beyond#快速开始">安装与使用 →</a></p>

## 适用场景

- **固件初步分析**：导入固件镜像，调用解包工具，发现 Web 服务、CGI、启动服务和网络 API 等线索。
- **文件系统审计**：直接输入已解包目录，筛选候选二进制，由 SupervisorAgent 使用 LLM 选择优先审计目标。
- **指定二进制分析**：输入已识别的 ELF、PE 或单架构 Mach-O 文件，直接审计指定目标。
- **结果整理**：生成 Markdown 阅读报告和结构化 JSON，保留危险函数地址、调用者、调用位置及输入 API 线索，便于人工复核。

## 工作流程

```text
固件镜像 → 解包 → 目标筛选 → LLM 选择目标 → Ghidra 扫描 → 报告
已解包目录 ────→ 目标筛选 → LLM 选择目标 → Ghidra 扫描 → 报告
已识别二进制 ────────────────────────→ Ghidra 扫描 → 报告
```

框架通过 Intake、Unpack、Triage、Audit、Report 等工作节点组织任务，RecoveryAgent 辅助诊断工具错误和异常。支持交互式审计会话与一次性命令行调用，可接入 OpenAI 兼容 API，并配置模型推理级别。

## 当前分析能力

Ghidra Headless 提供反编译与调用线索，确定性分析原型进一步检查部分危险调用：比较 `strcpy` 字面量长度与推断栈数组容量、比较 `snprintf` 大小参数与容量，以及追踪直接来自 `getenv` / NVRAM 的返回值是否流入 `system` / `popen`。报告保留判断依据与证据缺口。

当前 LLM 用于候选目标选择和部分异常诊断；自然语言任务规划与 LLM 漏洞研判仍在开发中。参数分析限于函数内部分 P-code 关系，栈数组容量依赖反编译类型恢复，未知容量不会被视为安全。完整跨函数数据流、防护有效性证明与路径可达性验证尚未实现，输出属于分析线索、疑似问题或证据不足，需进一步人工确认。

## 开始使用与参与开发

请按仓库的 [快速开始](https://github.com/oob-iot-sec-labs/OOB-Beyond#快速开始) 安装 Python 依赖、配置模型服务，并准备所需的 Binwalk、SquashFS 工具与 Ghidra Headless 环境。具体输入类型、运行命令和依赖要求请参阅 [README](https://github.com/oob-iot-sec-labs/OOB-Beyond#readme)。

使用问题、功能建议和缺陷反馈可提交至 [项目 Issues](https://github.com/oob-iot-sec-labs/OOB-Beyond/issues)，代码贡献可通过项目仓库的 Pull Request 参与。

<a href="{{ '/tools/' | relative_url }}" class="back-home" title="返回安全工具">返回安全工具</a>

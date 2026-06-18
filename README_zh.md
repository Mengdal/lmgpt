# LMGPT — Agents Everywhere

[English](./README.md) | **中文**

[![Bash](https://img.shields.io/badge/bash-4.0%2B-green?logo=gnubash)](https://www.gnu.org/software/bash/)
[![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20WSL%20%7C%20Termux%20%7C%20iSH-blue)]()
[![Lines](https://img.shields.io/badge/lines-16,975-orange)]()
[![Functions](https://img.shields.io/badge/functions-465-purple)]()
[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](./LICENSE)
[![Status](https://img.shields.io/badge/status-preview-yellow)]()

---

### 1. 📂 WHAT is it?

**它是一个用纯 Bash 编写的、快如闪电的零依赖命令行 GPT 客户端。**

- **零重量级依赖：** 整个项目只有一个轻量的 `.sh` 脚本。你的系统里只要有 `curl` 和 `jq`（终端标配），它就能立刻工作。
- **真·流式响应 (True Streaming)：** 底层利用 Bash 的纯字符流管道状态机，让大模型的答案像打字机一样实时滚出，绝不卡顿，更不占用一丝多余的内存。
- **天然的管道基因：** 它不仅能聊天，更能作为一个标准的 Unix 过滤器，与其他命令行工具无缝编排。

### 2. 👤 WHO is it for?

**它是专门为"终端重度依赖者"、"全键盘黑客"以及"资源受限的环境"而生的。**

- **后端/基础架构工程师：** 懒得切换到浏览器或打开沉重的 GUI 客户端，只想在终端里盲打解决一切。
- **边缘计算与网关开发者：** 在内存只有几兆、几十兆的嵌入式 Linux 设备（如树莓派、工业智能网关）上，需要随时呼叫 AI 算力就地诊断。
- **极客运维/SRE：** 面对密密麻麻的服务器裸机集群，需要一个没有任何环境包袱（不用装 Python/Pip）的极简 AI 工具来帮手。

### 3. 📍 WHERE can it be used?

**任何能够运行现代 Bash 的数字边界，都是它的主场。**

- **生产线现场与物理网关：** 运行在断网、弱网或极度苛刻的工业 Linux 环境中。
- **日常生产力终端：** 你的 macOS（需升级 Bash 5）终端、Ubuntu、CentOS 或者是 Windows 的 WSL 命令行内。
- **自动化工作流：** 潜伏在你的 `~/.bashrc` 别名里，或者嵌套在你的 CI/CD 自动化部署脚本中。

---

## ✨ 特性

- 🐚 **纯 Bash 实现** — 16,975 行代码，465 个函数，无 Node/Python 运行时依赖
- ⚡ **零 Fork 热路径** — 增量消息拼接、哈希驱动缓存、纯 bash 请求体、跨回合持久化渲染器；最小化每轮 subshell 开销
- 🖥️ **全平台覆盖** — Linux (GNU)、macOS (BSD)、WSL、Termux (Android)、iSH (iPhone/iPad)
- 🔧 **24 个内置工具** — 文件读写编辑删除、命令执行、网页搜索、子智能体调用、TODO 管理、技能系统……
- 🤖 **子智能体系统** — 11 个系统智能体（plan/explore/review/summarize……）+ 可自定义项目智能体
- 🧠 **分布式记忆网络** — 16 个 engram × 200 slots = 3,200 条持久记忆，支持语义搜索
- 🌐 **HTTP 守护进程** — REST API + SSE 流式输出，可作为后端服务运行
- 🔌 **MCP 协议支持** — Model Context Protocol（stdio/sse/http 三种传输），连接外部工具生态
- 🪝 **Hook 插件系统** — 8 个挂载点、6 种处理器类型，可深度定制行为
- 📦 **四级上下文压缩** — 自动管理超过 250KB 的对话上下文
- ↩️ **Trace/Undo** — 内容寻址的文件修改追踪，支持回滚
- 🔄 **自适应智能体循环** — 三条保护机制，防止无限循环
- ⌨️ **完整 Readline** — 支持 Unicode/CJK 字符、多行编辑、历史搜索、Tab 补全、稳定的自动换行渲染
- 📱 **Termux-API 集成** — 在 Android 手机上控制传感器、摄像头、短信等
- 🔄 **自我进化** — LMGPT 能读懂并修改自己的源码，用对话给自己加功能

---

## 🚀 快速开始

### 核心依赖

| 依赖 | 最低版本 | 用途 |
|------|---------|------|
| **bash** | 4.0+ | 脚本运行时。绝大多数现代系统已内置。 |
| **jq** | 任意版本 | JSON 解析与处理，用于 API 通信和配置文件读写。 |
| **curl** | 任意版本 | HTTP 客户端，与 LLM API 端点通信。 |

---

### 安装

LMGPT 的安装流程统一为三步：

```
1. 获取脚本   →   2. 安装依赖   →   3. ./lmgpt --install
```

#### 🐧 Linux / Unix

```bash
# Debian / Ubuntu
sudo apt install jq curl

# RHEL / CentOS / Fedora
sudo dnf install jq curl

# Arch Linux
sudo pacman -S jq curl

# Alpine Linux
sudo apk add jq curl bash

# 获取 LMGPT
git clone https://github.com/Mengdal/lmgpt.git
cd lmgpt
./lmgpt --install
```

#### 🍎 macOS

```bash
brew install bash jq curl
git clone https://github.com/Mengdal/lmgpt.git
cd lmgpt
./lmgpt --install
```

macOS 自带 bash 3.2（太旧），必须通过 Homebrew 安装新版。

#### 🪟 Windows（WSL）

```powershell
wsl --install
```

重启后进入 WSL 终端，按 Linux 步骤安装。

#### 📱 Android（Termux）

从 [F-Droid](https://f-droid.org/packages/com.termux/) 安装 Termux，然后：

```bash
pkg install bash jq curl git coreutils
git clone https://github.com/Mengdal/lmgpt.git
cd lmgpt
./lmgpt --install
```

`coreutils` 提供 `realpath` 等工具，**必须安装**。

#### 📱 iPhone / iPad（iSH）

从 [App Store](https://apps.apple.com/app/ish-shell/id1436902243) 安装 iSH，然后：

```bash
apk add bash jq curl git coreutils
git clone https://github.com/Mengdal/lmgpt.git
cd lmgpt
./lmgpt --install
```

---

### 配置 API

编辑 `~/.lmgpt/settings.json`：

```json
{
  "api_url": "https://api.deepseek.com/anthropic",
  "api_key": "sk-your-api-key-here",
  "model": "deepseek-chat"
}
```

或使用环境变量（推荐）：

```bash
export LMGPT_API_KEY="sk-your-api-key-here"
```

兼容后端：DeepSeek（默认）、Anthropic 官方、Ollama、vLLM 等任何支持 Anthropic Messages API 的服务。

---

### 启动

```bash
# 交互式对话（默认）
lmgpt

# 管道单次模式
git diff HEAD~1 | lmgpt --oneshot

# 启动 HTTP 守护进程
lmgpt --run --port 9655

# 更新
./lmgpt --update
```

---

## 🔧 使用示例

### 交互式对话

```bash
$ lmgpt

  ██╗     ███╗   ███╗ ██████╗ ██████╗ ████████╗
  ██║     ████╗ ████║██╔════╝ ██╔══██╗╚══██╔══╝
  ██║     ██╔████╔██║██║  ███╗██████╔╝   ██║
  ██║     ██║╚██╔╝██║██║   ██║██╔═══╝    ██║
  ███████╗██║ ╚═╝ ██║╚██████╔╝██║        ██║
  ╚══════╝╚═╝     ╚═╝ ╚═════╝ ╚═╝        ╚═╝

  Model: deepseek-v4-pro[1m]           Thinking: status
  Endpoint: api.deepseek.com/anthropic
  Author: Mengdal                      Version: preview-0.1

  > /help          # 查看内置斜杠命令
  > 帮我分析这段代码的性能瓶颈
  > 查找所有调用 login() 函数的地方
  > 给这个模块写单元测试
```

### 管道模式

```bash
# 代码审查
git diff HEAD~1 | lmgpt --oneshot

# 日志分析
tail -100 /var/log/app.log | lmgpt --oneshot

# 结合其他工具
eslint src/ --format json | lmgpt --oneshot
```

### 守护进程 API

```bash
# 启动服务
lmgpt --run --port 9655

# 创建会话
curl -X POST http://localhost:9655/v1/session/new

# 发送消息
curl -X POST http://localhost:9655/v1/chat \
  -d '{"message": "帮我分析这段代码"}'

# SSE 流式订阅
curl -N http://localhost:9655/v1/session/{id}/stream
```

### 自我进化

LMGPT 能读懂并修改自己的源码。你可以直接用对话让它给自己加功能：

```
> 帮我加一个 --version 参数，打印版本号
> 给启动画面加一行自定义 slogan
```

它会读代码、改代码、验证、完成。整个过程在对话中一气呵成。

---

## ⚙️ 配置体系

四级优先级（后者覆盖前者）：

```
内置默认值  →  ~/.lmgpt/settings.json  →  项目 .lmgpt/settings.json  →  环境变量
```

| 配置项 | 环境变量 | 默认值 | 说明 |
|--------|---------|--------|------|
| `api_url` | `LMGPT_API_URL` | DeepSeek 端点 | API 地址 |
| `api_key` | `LMGPT_API_KEY` | — | API 密钥 |
| `model` | `LMGPT_MODEL` | `deepseek-chat` | 模型名称 |
| `max_tokens` | `LMGPT_MAX_TOKENS` | 32768 | 最大输出 token |
| `thinking_budget` | `LMGPT_THINKING_BUDGET` | 16384 | 思考预算 |
| `context_window` | `LMGPT_CONTEXT_WINDOW` | 1048576 | 上下文窗口大小 |
| `context_safe_ratio` | — | 75 | 自动压缩阈值 (%) |
| `cmd_timeout` | — | 300 | 命令超时 (秒) |
| `proxy_url` | `LMGPT_PROXY_URL` | — | 代理地址 (http/socks4/socks5) |
| `dark_mode` | — | true | 深色终端配色 |

项目级配置 `.lmgpt/LMGPT.md` 可注入项目上下文到系统提示词。

---

## 🏗️ 架构

```
main()
  ├─ CLI 解析 (--install / --run / --oneshot / 默认交互)
  ├─ 初始化 (配置 / 智能体 / 技能 / Hook / 记忆 / MCP)
  └─ agent_loop()
       ├─ pre_turn hooks
       ├─ API 调用 (SSE 流式)
       ├─ 工具执行循环
       │    ├─ read_file / write_file / edit_file / delete_file
       │    ├─ bash (同步/异步)
       │    ├─ web_search
       │    ├─ agent / agent_batch (子智能体)
       │    ├─ task 管理 / request (人工审批)
       │    ├─ undo (trace 回滚)
       │    └─ mcp__* (MCP 外部工具)
       ├─ 自适应 token 预算
       ├─ 上下文自动压缩
       └─ post_turn hooks
```

### 核心子系统

| 子系统 | 代码段 | 功能 |
|--------|-------|------|
| 工具系统 | §8–§10 | 24 个工具定义、实现、调度 |
| 智能体系统 | §7 | 子智能体加载、调用、通信 |
| 记忆网络 | §7c | 16 engram 分布式记忆，语义搜索，睡眠压缩 |
| 上下文压缩 | §5 | 四级压缩策略 (>250KB 阈值) |
| HTTP/SSE | §6a | curl 封装，SSE 流解析 |
| 守护进程 | §11d | HTTP 服务器、Worker Pool、Cron 调度 |
| MCP 客户端 | §11c | stdio/sse/http 传输，外部工具动态注册 |
| 输入层 | §2b–§2c | 自研 Readline，Unicode/CJK 支持 |
| Trace/Undo | §7f | 内容寻址文件追踪，帧回滚 |
| 自适应循环 | §11b | 三条保护机制 (token/时间/轮次) |
| Hook 系统 | §2 | 7 点 × 6 类型的可扩展架构 |

---

## 📱 Termux-API 集成

在 Android 上安装 `termux-api` 后，LMGPT 可直接调用手机硬件：

```bash
pkg install termux-api
```

| 能力 | 对话用法举例 |
|------|-------------|
| 📷 拍照 | "帮我拍张照，分析照片里的文字" |
| 📍 定位 | "获取 GPS 坐标，告诉我最近的地铁站" |
| 📱 短信 | "给张三发短信：会议改到下午三点" |
| 🔋 电池 | "电量低于 20% 就提醒我" |
| 🎤 录音 | "录音 30 秒然后转文字" |
| 🔔 通知 | "十分钟后提醒我喝水" |

---

## 🤝 贡献

目前处于 **preview** 阶段，欢迎：

- 🐛 提交 [Issue](https://github.com/Mengdal/lmgpt/issues) 报告 bug
- 💡 提 Feature Request
- 🔀 提交 Pull Request

```bash
cd test
./run_all.sh                # 单元测试（无需 API）
./run_all.sh --all          # 完整套件（需要 API key）
```

---

## 📄 许可证

Apache License 2.0。详见 [LICENSE](./LICENSE)。

---

## 🙏 致谢

- [Anthropic](https://www.anthropic.com/) — Messages API 协议
- [DeepSeek](https://www.deepseek.com/) — 默认模型后端
- [jq](https://jqlang.github.io/jq/) — JSON 处理器
- [Termux](https://termux.dev/) — Android 终端环境
- [iSH](https://ish.app/) — iOS 上的 Linux Shell

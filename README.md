# Claude Code Configuration

[![GitHub stars](https://img.shields.io/github/stars/wxkawxk/claude-code-config?style=social)](https://github.com/wxkawxk/claude-code-config)
[![GitHub forks](https://img.shields.io/github/forks/wxkawxk/claude-code-config?style=social)](https://github.com/wxkawxk/claude-code-config/fork)
[![GitHub license](https://img.shields.io/github/license/wxkawxk/claude-code-config)](https://github.com/wxkawxk/claude-code-config/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/wxkawxk/claude-code-config/pulls)

English | [简体中文](README_CN.md)

A Claude Code configuration file for non-programmers - Let AI be your CTO.

## 特性

- ✅ **高信任模式**：自动化授权，减少确认次数
- 📋 **任务队列管理**：TODO.md + Ralph Loop 模式
- 📝 **经验沉淀系统**：PROGRESS.md 记录问题和解决方案
- 🛡️ **安全防护**：Git Hooks 自动检查敏感信息
- 🎯 **非程序员友好**：用非技术语言沟通架构
- 🚀 **增量开发**：小步快跑，每次最多改 5 个文件

## 快速开始

### 1. 安装配置文件

```bash
# 下载配置文件到家目录
curl -o ~/CLAUDE.md https://raw.githubusercontent.com/wxkawxk/claude-code-config/main/CLAUDE.md

# 根据你的实际情况修改配置
nano ~/CLAUDE.md
```

### 2. 配置 Git Hooks（可选但推荐）

```bash
# 创建全局 hooks 目录
mkdir -p ~/.git-hooks
git config --global core.hooksPath ~/.git-hooks

# 下载 hooks
curl -o ~/.git-hooks/pre-commit https://raw.githubusercontent.com/wxkawxk/claude-code-config/main/hooks/pre-commit
curl -o ~/.git-hooks/commit-msg https://raw.githubusercontent.com/wxkawxk/claude-code-config/main/hooks/commit-msg

# 添加执行权限
chmod +x ~/.git-hooks/pre-commit
chmod +x ~/.git-hooks/commit-msg
```

### 3. 开始使用

```bash
# 启动 Claude Code
claude

# 或者在项目目录下
cd ~/my_project/your-project
claude
```

## 文件结构

```
.
├── CLAUDE.md           # 主配置文件
├── README.md           # 本文件
├── hooks/              # Git Hooks
│   ├── pre-commit      # 提交前检查
│   └── commit-msg      # 提交信息检查
└── examples/           # 示例文件
    ├── TODO.md         # 任务列表示例
    └── PROGRESS.md     # 经验沉淀示例
```

## 核心概念

### Ralph Loop 模式

从任务队列顶部依次处理任务，完成一个进入下一个，让 AI 持续工作。

### 三阶段开发流程

1. **需求拆解与规划**：EnterPlanMode → TODO.md → 架构同步
2. **增量开发与排错**：小步快跑 → 故障防御 → 经验沉淀
3. **质量保证与部署**：自动验证 → 清理现场 → 部署预备

### Servant Leadership

- Context, not Control：提供上下文而非微管理
- 第一性原理思考：从根本目标出发
- 不看代码原则：信任 AI，专注需求和架构

## 自定义配置

根据你的实际情况修改 `CLAUDE.md`：

```markdown
## 3. 开发环境上下文
- **根目录**：`~/my_project/`  # 改成你的项目目录
- **环境自感知**：
  - **Python**: 默认使用系统 Python 3.x (pip)  # 改成你的版本
  - **Node.js**: 默认使用系统 Node.js (pnpm)   # 改成你的版本
```

## Git Hooks 说明

### pre-commit

- ❌ 阻止提交敏感文件（.env、credentials.json 等）
- ⚠️ 检测代码中的密码/密钥/token
- ⚠️ 提醒清理调试日志（print/console.log）

### commit-msg

- ❌ 阻止空的或太短的 commit message
- 💡 建议使用规范格式（feat/fix/docs 等）

## 常见问题

### Q: 如何禁用某个 Git Hook？

```bash
# 临时禁用（单次提交）
git commit --no-verify

# 永久禁用
rm ~/.git-hooks/pre-commit
```

### Q: 如何保留某些调试日志？

在代码中添加注释：

```python
print("这是调试日志")  # keep
```

```javascript
console.log("这是调试日志");  // keep
```

### Q: 如何修改项目根目录？

编辑 `~/CLAUDE.md`，修改第 3 节的根目录路径。

## 灵感来源

- [提高 Agentic Coding 吞吐量的 10 个阶段](https://mp.weixin.qq.com/s/...)
- Ralph Loop 任务队列模式
- Servant Leadership 理念

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT License

## 作者

[@wxkawxk](https://github.com/wxkawxk)

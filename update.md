# 更新流程

按照如下步骤进行交互式升级：

## 1. 获取安装目录

- 读取本地文件 `.cursor/rules/memory-management.mdc` 中变量定义的 `install_path` 变量，并记下来

## 2. 下载最新文件并保存

1. 使用 `curl` 读取以下远程文件内容：
      - https://raw.githubusercontent.com/Jirry/cursor-memory-management/refs/heads/main/memory-management.md
2. 使用 `sed` 替换其中的占位符 `#${install_path}#` 为变量 `install_path` 的值
3. 将其内容保存到 Cursor 的 `Project Rules` 目录下，名字为：`memory-management.mdc`
      - Cursor 的 `Project Rules` 目录一般位于项目的根目录：`.cursor/rules/`

## 3. 检查更新结果

- 需要你重新加载项目规则，查看是否已经是最新版本
- 读取 mdc 文件时，以纯文本方式读取，或者以 `read_file` 工具读取，因为 mdc 文件会隐藏头信息
- 如果已经是最新版本，告知用户升级成功，并列出本次升级的更新内容（重点为记忆文件的改动之处）

---

# 更新日志
- 0.0.7
    - 本地记忆文件的格式改为：`[记忆内容]`，移除记忆来源信息
- 0.0.6
    - 添加记忆来源信息，方便用户了解记忆内容的来源
    - 本地记忆文件的格式改为：`[来源][记忆内容]`，方便用户了解记忆内容的来源
- 0.0.5
    - 尝试优化 AI 的对话行为，避免 AI 在对话中频繁提及记忆管理系统的实现细节和记忆文件内容
- 0.0.4
    - 添加版本号到描述信息
    - 优化 mdc 文件的读取方式
- 0.0.3
    - 添加变量定义模块
    - 强制使用远程的 memory-management.md 文件，替换本地文件
- 0.0.2
    - 修复安装脚本中的异常问题
    - 将安装目录由 `./cursor/memory/` 改为 `.cursor/memory/`（如有本地记忆文件，请迁移到新目录）
- 0.0.1
    - 发布初始版本
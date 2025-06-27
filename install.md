# 记忆管理系统安装脚本

按照如下步骤进行交互式安装：

## 1. 询问用户安装目录

询问用户选择安装目录：
- **选项A**: 保存到项目根目录，默认为： `.cursor/memories/`
- **选项B**: 保存到指定目录（用户可输入自定义路径）

等待用户选择并将结果记录到变量 `install_path`

## 2. 下载远程文件并保存

1. 使用 `curl` 读取以下远程文件内容并保存到临时文件：
    - https://raw.githubusercontent.com/Jirry/cursor-memory-management/refs/heads/main/memory-management.md
2. 使用 `sed` 替换其中的占位符 `#${install_path}#` 为变量 `install_path` 的值
3. 使用 `mv` 将修改后的临时文件保存到 Cursor 的 `Project Rules` 目录下，名字为：`memory-management.mdc`
    - Cursor 的 `Project Rules` 目录一般位于项目的根目录：`.cursor/rules/`

## 3. 检查安装结果

- 需要你重新加载项目规则，查看是否有关于 `memory-management.mdc` 的规则
- 读取 mdc 文件时，以纯文本方式读取，或者以 `read_file` 工具读取，因为 mdc 文件会隐藏头信息
- 如果存在，告知用户安装成功，并列出【记忆管理系统】支持的命令和用法
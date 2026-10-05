# EOS Mail

[English](./README.en.md) | [中文](./README.md)

本地优先的桌面邮箱客户端：邮件通过 IMAP 收取、SMTP 发送，全部数据同步到你自己的电脑上本地存储；没有云端中转，没有遥测。多账户、Gmail 一键授权、离线全量检索、双层消毒的 HTML 安全渲染，基于 Tauri 2 + React 构建。

> **本仓库是 EOS Mail 的公开门户**，用于：
> - 安装包下载：见 [Releases](https://github.com/eosaios/eos-mail-app/releases)
> - 问题反馈与功能建议：请提 [Issues](https://github.com/eosaios/eos-mail-app/issues)
> - 多平台构建（GitHub Actions）
>
> EOS Mail 是闭源商业软件，**源码不在本仓库**。

## 下载与安装

**beta 期间免费使用**，正式版定价将在临近发布时公布。

| 平台 | 安装包 | 说明 |
|---|---|---|
| Windows | `*-setup.exe` | NSIS 安装器，未签名 |
| macOS | `*.dmg` | universal（Intel + Apple Silicon），未签名 |
| Linux | `*.deb` / `*.AppImage` | deb 与 AppImage 双格式 |

- Windows 首次运行如被 SmartScreen 拦截，选择「更多信息 → 仍要运行」
- macOS 首次打开如被 Gatekeeper 拦截，请执行 `xattr -cr "/Applications/EOS Mail.app"`
- 邮件数据保存在用户目录（本地 SQLite 数据库），升级安装不影响已有邮件；卸载应用不会删除你的邮件数据
- 完整性校验：各 Release 附带 SHA256SUMS.txt

## 功能

- **多账户**：标准 IMAP / SMTP（SSL / STARTTLS）与 Gmail OAuth2 一键授权
- **本地优先**：邮件全量落库，断网也能读信、搜索、管理；重新联网后增量同步
- **统一搜索**：关键词全文检索与附件检索（`has:pdf`、`file:发票`）
- **安全渲染**：HTML 邮件经 Rust 侧消毒后注入无脚本沙箱 iframe；远程图片默认拦截（防阅读追踪），点击解锁且仅限当封邮件
- **钓鱼防护**：显示名仿冒检测、链接文字与真实域名不一致警示、可疑评分横幅、附件按内容特征识别（双扩展名 / RTL 欺骗字符 / 可执行文件确认）
- **写作**：邮件撰写、草稿与已发送管理
- **个性化**：明暗主题、中英文界面
- **100% 本地**：除你配置的邮件服务器与 Google 授权页外，运行时不发起任何网络请求；零遥测、零崩溃上报

## 隐私与凭据

- 账户密码 / 授权码 / OAuth refresh token **只存系统钥匙串**（macOS Keychain / Windows 凭据管理器 / Linux Secret Service），不写进数据库或任何明文文件
- 邮件正文与附件只存在于你电脑上的本地数据库与附件目录
- IMAP / SMTP 一律 TLS 加密，不提供也不接受明文降级

## 反馈指南

- 🐛 Bug 反馈：请附上操作系统版本、EOS Mail 版本号、邮箱服务商与复现步骤（**不要附带邮件原文或密码**）
- 💡 功能建议：描述你的使用场景，而不仅仅是方案
- 🔒 隐私相关：本应用除邮件服务器与授权页外不发起任何网络请求，如你观察到可疑行为请立即反馈

## 许可

© 2026 EOSAIOS. All rights reserved. 未经授权不得复制或再分发本软件。

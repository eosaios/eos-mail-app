# Mail Dev / Beta 候选构建

`.github/workflows/mail-candidate.yml` 组合指定的 Mail 基础仓与 Pro 仓完整源码，生成测试渠道安装包。既有 `build.yml` 保留基础版测试与发布行为。候选构建只生成 Actions artifacts，不创建公开 Release，不上传平台，不提升 stable。

`base_ref` 和 `pro_ref` 必须填写完整 40 位提交 SHA。Mac 产出 Apple Silicon 的 Dev 与 Beta DMG；Windows 产出 x64 Beta NSIS；Linux 产出 x64 Beta DEB。两个渠道均显式连接生产账号服务，应用标识、回跳协议、钥匙串与本地数据相互独立。

需要三个只读源码 deploy keys：`EOS_MAIL_DEPLOY_KEY`、`MAIL_PRO_BUILD_KEY`、`MAIL_CORE_BUILD_KEY`。私有内核固定在 `d3a967f198a7578e4446820b1b5a2aaf3ce24f79`；Windows checkout 保留 LF 提示文件，并静态链接 CRT。内核启动握手必须确认既定 Mail pack / contract；不以新摘要替代契约检查。

```sh
gh workflow run mail-candidate.yml --repo eosaios/eos-mail-app \
  -f base_ref=FULL_BASE_COMMIT_SHA \
  -f pro_ref=FULL_PRO_COMMIT_SHA \
  -f beta_version=0.2.0-beta.2 \
  -f dev_version=0.2.0-dev.2 \
  -f platforms=all \
  -f run_tests=true \
  -f run_base_tests=true
```

默认运行基础 Rust 测试、组合版前端/Rust 测试，然后构建安装包。只有相同业务源码的原生测试已通过，且仅重跑打包时，才关闭对应测试输入，并在发布记录中引用先前运行。`ai_library_tests_only=true` 用于仅修复 AI 库测试夹具的复验：业务源码必须未改，上一原生全套运行的其他目标须已通过，并保留两次运行记录。`reuse_core_run` 仅接受流程中明确审计过的平台/运行组合；缺省会从固定源码重新构建。

每个安装包在真实安装目录中运行 `--build-info` 和 `--verify-package`，再输出 `*.manifest.json`，记录渠道、环境、版本、文件大小/SHA256 和私有内核清单。Mac 另外检查代码签名。Beta 与 Dev artifacts 分别上传，避免后一渠道构建失败影响前一渠道制品的保存。

Linux 本轮分发使用 DEB。AppImage 工具会改写嵌套 ELF，当前不纳入固定摘要内核的候选分发。Mac 为 ad-hoc 签名，Windows 未做代码签名；真实账号登录、收发、AI 场景和正式签名/公证仍需在公开正式发布前验收。

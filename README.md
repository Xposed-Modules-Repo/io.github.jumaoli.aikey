# 爽歪了AI键 (AIKey Plus)

把小米 / 红米的 **AI 键**（默认唤起超级小爱的那个键）改造成可自定义的手势按键。

通过 LSPosed 在 `system_server` 里拦截按键，再调用 MIUI 自己的动作分发器 `com.miui.server.input.util.ShortCutActionsUtils#triggerFunction`，
所以能做的不只是“打开某个 App”，而是系统级动作：付款码、乘车码、扫码、防窥、静音、截图、背屏截图、相机、小爱功能……

## 功能

| 手势 | 说明 |
| --- | --- |
| 单击 | 可自定义 |
| 双击 | 可自定义 |
| 三击 | 可自定义 |
| 长按 | 可自定义 |

- **80+ 内置动作**，分「常用 / 小爱·语音 / 支付·乘车·扫码 / 系统功能 / 应用·自定义」五组
- **任意 shell 命令**（需要 root）
- **背屏支持**：把应用放到背屏（display 1）、回背屏桌面、背屏截图、背屏小部件
- **运行方式**：LSPosed 钩子（8.1.0 起只保留这一种，更稳定）
- 手势阈值全部可调（长按 200–2000ms、双击窗口、三击窗口）
- 震动反馈、开机自启、常驻后台可选

## 安装

1. 安装 APK
2. 在 LSPosed 中启用本模块，作用域勾选 **系统框架**
3. 重启手机
4. 打开 App，按「立即应用」授权 root
5. 选择四个手势对应的动作

## 使用说明

- 配置存放在 `Settings.System` 的 `aikey_*` 键，重装 App 不会丢
- 想恢复系统原本的 AI 键行为：App 里点「还原系统 AI 键」

## 已知问题

- 「小爱记忆 / 小爱视频」目前会进入小爱捷径，尚未找到正确的 function 键
- 背屏自定义面板受 `FLAG_OWN_CONTENT_ONLY` 限制，第三方 Activity 无法直接显示在背屏

## 兼容性

- 主要针对小米 HyperOS（测试机：小米 18 Pro，OS4.0.27，Android 17）
- AI 键在框架层的键码是 **690**（内核层 689）
- minSdk 30

## 开源

源码与问题反馈：https://github.com/jumaoli/aikey-plus-lsp

## 致谢

- @婉彬（酷安）— 测试与建议
- Cpek0（酷安 u/14823887）— 乐乐背屏，背屏启动方式参考
- NekoWannn — 按键逻辑与动作实现参考 `aikey_plus`
- LSPosed — 运行环境

## License

MIT
---

## English

**AIKey Plus** turns the Xiaomi / Redmi **AI button** into a customizable gesture key (single / double / triple click / long press).

Running inside `system_server` via LSPosed, it dispatches MIUI's own native actions through
`ShortCutActionsUtils#triggerFunction`, so it can trigger payment codes, transit codes, scanners, peep protection,
mute, screenshots, rear-screen capture, camera and Xiao Ai functions — 80+ actions in total, plus arbitrary shell commands.

- Runtime: LSPosed (scope: **System Framework**), root for shell-based actions
- Tested on Xiaomi 18 Pro / HyperOS OS4.0.27 / Android 17 (AI key = keycode 690)
- Source & issues: https://github.com/jumaoli/aikey-plus-lsp
- License: MIT

### Install

Install the APK → enable in LSPosed with the System Framework scope → reboot → open the app, tap Apply, grant root → pick actions.
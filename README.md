# android-quiz-skill

> **在安卓 App 里答题的 Agent Skill**：找工作 → 读题 → 作答 → 逐题像素校验 → 交卷。

| | |
|---|---|
| 状态 | 可用（早期在手机上摸索出来的实战版） |
| 适用 | 安卓答题类 App（uni-app 页面已实测） |
| 运行方式 | 电脑 adb / 安卓模拟器 / 本机 Termux + Shizuku |
| 前置 | **android-shell**（必装，见下） |

---

## 前置技能（必读）

本技能只负责**题目流程**；设备层（截图、点击、UI dump、Shizuku/rish、通知）由通用控制技能提供：

> 🔧 **先安装 [`android-shell`](https://github.com/MC090610/android-shell-skill)**
>
> ```text
> 从 https://github.com/MC090610/android-shell-skill 安装 android-shell
> ```
>
> 装完后先按它的 Step 0 做环境自检（Termux / Shizuku / rish / adb），
> 再回来用本技能。设备层报错、HyperOS 后台限制等问题，去 android-shell 里排查。

`scripts/andev.sh` 自带 adb / rish / su 传输层，纯 adb 环境也能直接跑；
但**推荐先装 android-shell**，这样两套工具的设备层行为一致、排查路径也一致。

## 能做什么

- 在作业/测验列表里找到目标任务并打开
- 文本优先读屏（`uiautomator dump`），拿题干、选项和真实坐标
- 一次受保护的批量点击完成作答，再逐题做像素校验
- 交卷前确认、交卷后汇报每题答案与成绩

## 安装

把下面这句发给你的 Agent（Codex / OpenClaw 都适用）：

> 先安装 https://github.com/MC090610/android-shell-skill ，再安装
> https://github.com/paperlane-tools/android-quiz-skill 到技能目录，
> 并把 `prompts/android-quiz.md` 放进 prompts / command 目录；
> 最后按 SKILL.md 的 Step 0 自检环境并汇报传输方式、实体机/模拟器、是否有 root。

## 文件

| 路径 | 作用 |
|---|---|
| `SKILL.md` | 技能主文档（流程、环境矩阵、注意事项） |
| `prompts/android-quiz.md` | 触发用的 prompt 模板 |
| `agents/openai.yaml` | 技能元数据 |
| `scripts/andev.sh` | adb / rish / su 统一传输层 |
| `scripts/dump.js` / `scripts/px.js` | UI dump 解析 / 像素校验 |
| `references/quiz-playbook.md` | 答题流程细化 |
| `references/field-notes-2026-09-29.md` | 实战记录（49 题 48 对） |
| `docs/termux-setup.md` | Termux + Shizuku 安装前置 |

## 许可证

[GPL-3.0-only](LICENSE) © 2026 paperlane-tools；附加条款见 [NOTICE](NOTICE)。

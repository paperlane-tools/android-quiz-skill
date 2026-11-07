---
description: 在安卓 App 里答题（自动问清目标设备 + 自检 adb/root/Shizuku）
argument-hint: "[可选：作业名 / 包名 / 要答的科目]"
---

用 **$android-quiz** 技能完成这件事。用户输入：$ARGUMENTS

按技能规定执行，不要跳步：

0. **先确认前置技能**：确认已安装
   [`android-shell`](https://github.com/MC090610/android-shell-skill)
   （通用安卓控制：Shizuku / rish / 截图 / UI dump / 通知）。没装就先问我要不要装，
   装好后再继续。答题技能只负责题目流程，设备层问题去 `android-shell` 排查。
1. **先问用户**目标设备属于哪一种，然后等回答：
   ① 通过 USB 连接的实体安卓设备；② 安卓模拟器；③ 本机（Termux 里跑，无数据线）。
2. 跑 `bash scripts/andev.sh detect`，并**如实汇报**探测结果：
   传输方式（adb / rish / su）、是否已连上设备、**实体机还是模拟器**、**是否有 root**、
   Android 版本与屏幕尺寸。缺什么就直说缺什么，别硬猜。
3. 再按技能流程干：
   找工作列表里的作业 → 打开并读题（题目是图片就点开看）→
   **一次受保护的批量点击**完成作答 → **逐题像素校验** →
   **交卷前必须得到用户确认**（除非用户已经明确说交卷）→ 汇报每题答案与最终成绩。

如果 $ARGUMENTS 是空的，先问用户要做哪个 App / 哪份作业。

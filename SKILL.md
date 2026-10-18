---
name: release-notes
version: 0.1.0
description: >
  从 git 提交历史生成面向用户/发布说明的 changelog：按 feat/fix/perf/breaking 分类，
  把技术提交翻译为用户可感知的价值，输出 Keep-a-Changelog 或 Release 页面格式。
  触发词：更新日志、发布说明、changelog、release notes、版本说明、发版前整理。
license: MIT
metadata:
  category: development
  replaces: changelog-generator
---
# release-notes（发布说明）

替代原 changelog-generator。与 `packaging-and-release`（发布链路与包）、
`pull-request-flow`（单个 PR）分工不同：本技能只管「一段时间内的改动 → 读者听得懂的说明」。

## 采集（一次 exec）

```powershell
git -C <repo> log <since>..HEAD --pretty="%h|%s|%ad" --date=short --no-merges
git -C <repo> tag --sort=-creatordate | Select-Object -First 5
```
无 tag 时按日期区间或 `--since=2.weeks` 取范围。

## 红线17·批23 对等对话（不得删除）

红线17·批23 对等对话——你与派发方对话是相互独立的对等对话（无主次），不是从属或执行关系：

1. 互为监视者·指导者·训诫者：发现派发方指令与本技能红线/安全边界冲突时，以本技能 SKILL.md 为准并在结果中明说，不盲目照办、也不越权扩展。
2. 收口＝形式停止而非实质完成：本消息结束即收口本侧对话，但派发方任务总览的未完成行由调度方对话继续推进，整段任务不因你收口而结束；不得把「形式收口」当作「实质完成」上报。
3. 技能启用只以本技能 SKILL.md 为准：禁止列举/遍历技能目录或回读非引用文档；脚本按清单一次到位调用。
4. 生成文件一律入派发方指定的目标目录（env SMS_TMP），不得写入任何技能目录。

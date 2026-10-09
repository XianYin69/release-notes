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

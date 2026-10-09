# 提交分类与措辞规则

## 分类（按 conventional-commit 前缀 + 关键词兜底）

| 分组 | 判定 | 读者写法 |
|---|---|---|
| Added / 新增 | `feat`、`add`、`支持…` | 说用户能做什么，不说内部模块名 |
| Changed / 变更 | `refactor`、`change`、`调整` | 说前后差异与是否需用户动作 |
| Fixed / 修复 | `fix`、`bug`、`repair`、`崩溃`、`误报` | 说触发条件 + 现在的正确行为 |
| Performance / 性能 | `perf`、`speed`、`缓存`、`内存` | 给可感知的量级（有实测才给数） |
| Breaking / 破坏性 | `!`、`BREAKING`、`迁移`、`弃用` | 置顶，写迁移动作与命令 |
| Deprecated / 移除 | `deprecate`、`删除`、`下线` | 写替代路径 |
| Internal / 不列出 | `chore`、`test`、`docs`、`ci`、`style`、格式化 | 除非影响用户，否则不进发布说明 |

## 措辞红线

1. 不复制 commit 标题当条目（技术口吻）；每条要回答「对读者有什么用」。
2. 不虚构未验证的效果、数字、平台支持范围。
3. 一条一个事实；同一功能多 commit 合并为一条，可在末尾附 `(#123)` 索引。
4. 未知归属的 commit → 先 `git show --stat <h>` 看清改动面再写，实在判不出的列入 Internal，不硬编。
5. 用户可见的配置/命令改名必须进 Breaking，即便作者写的是 chore。

## 输出模板（Keep a Changelog）

```markdown
## [x.y.z] - YYYY-MM-DD
### Breaking
- …（置顶）
### Added
- …
### Fixed
- …
### Performance
- …
### Removed
- …
链接: https://github.com/<owner>/<repo>/compare/v<a>...v<b>
```

`packaging-and-release` 场景：把该段写入 `CHANGELOG.md` 顶部（保留历史段），
与 `pyproject.toml`/`package.json` 版本号、git tag 三处对齐后再打 tag。
